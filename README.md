# willfarrell/filebeat

**Filebeat: Analyze Log Files in Real Time**
Get ready for the next-generation Logstash Forwarder: Filebeat. Filebeat collects, pre-processes, and forwards log files from remote sources so they can be further enriched and combined with other data sources using Logstash. https://www.elastic.co/products/beats/filebeat

- [documentation](https://www.elastic.co/guide/en/beats/filebeat/index.html)
- [sample filebeat.yml](https://github.com/elastic/filebeat/blob/master/etc/filebeat.yml)

## Supported tags and Dockerfile links

-	[`1.0.1`, `1.0` (*Dockerfile*)](https://github.com/willfarrell/docker-filebeat/blob/master/1.1.1/Dockerfile)
-	[`1.1.1` (*Dockerfile*)](https://github.com/willfarrell/docker-filebeat/blob/master/1.1.1/Dockerfile)
-	[`1.1.2`, `1.1` (*Dockerfile*)](https://github.com/willfarrell/docker-filebeat/blob/master/1.1.1/Dockerfile)
-	[`1.2.1`, `1.2`, `1`, `latest` (*Dockerfile*)](https://github.com/willfarrell/docker-filebeat/blob/master/1.2.1/Dockerfile)
-	[`5.0.0-alpha1`, `5.0`, `5` (*Dockerfile*)](https://github.com/willfarrell/docker-filebeat/blob/master/5.0.0-alpha/Dockerfile)

## Run Examples

### docker-cli
```
docker run \
	-v /path/to/filebeat.yml:/etc/filebeat/filebeat.yml \
	willfarrell/filebeat:5.0.0-alpha1 \
	-c /etc/filebeat/filebeat.yml
```

### Dockerfile

```Dockerfile
FROM willfarrell/filebeat:1
COPY filebeat.yml /filebeat.yml
```

### docker-compose

```yml
version "2"

services:
  filebeat:
    image: willfarrell/filebeat:1
    command: "filebeat -e -c /etc/filebeat/filebeat.yml"
    environment:
      LOGSTASH_HOST: "192.168.99.100"
      LOGSTASH_PORT: "5044"
    volumes:
     - "./filebeat.yml:/etc/filebeat/filebeat.yml:rw"

```