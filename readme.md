# Grafana with docker

## Create a network
```
docker network create grafana-network
```

## Run containers
Starting a container with grafana.
> Grafana - Metrics Viewer
```
docker container run -d -v grafana:/var/lib/grafana -p 3000:3000 --name grafana --network grafana-network grafana/grafana
```

Starting a container with influxdb.
> Influxdb - Time series database
```
docker container run -d -v influxdb:/var/lib/influxdb -p 8083:8083 -p 8086:8086 -p 25826:25826/udp --name influxdb --network grafana-network influxdb:1.0
```

## Telegraf - Metrics Collector
After up containers, 
[install telegraf](https://docs.influxdata.com/telegraf/v1.13/introduction/installation/).

### Commands
After installation, view status.
```
sudo service telegraf status
```
In case of failure on database connect, restart service.
```
sudo service telegraf restart
```
