## Eample

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
