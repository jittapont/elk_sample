## Set up

### Start elasticsearch
```bash
  docker run -d --name elasticsearch -h elasticsearch  -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.9.2
```
> Test elasticsearch
```bash
  curl http://localhost:9200
```

### Start kibana
```bash
  docker run -d --name kibana -h kibana --link elasticsearch:elasticsearch -p 5601:5601 kibana:7.9.2
```
> Visit kibana by go to [link](http://localhost:5601/app/home#/)

### Start logstash
```bash
  docker run -it --name logstash -h logstash --link elasticsearch:elasticsearch -v ~/logstash.conf:/usr/share/logstash/pipeline/logstash.conf logstash:7.9.2 
```
Then start typing log message in terminal

## Start visualize log data

1. Go to [spaces](http://localhost:5601/app/management/kibana/spaces)
2. Go to [index pattern](http://localhost:5601/app/management/kibana/indexPatterns)
3. Create an index pattern (default will be logstash-*)
4. Add time field using @timestamp and click create index
5. Go to [dashbaord](http://localhost:5601/app/discover#/?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:now-15m,to:now))&_a=(columns:!(_source),filters:!(),index:b39344e0-0f9c-11eb-8a03-a955ac853ab1,interval:auto,query:(language:kuery,query:''),sort:!()))
