# Docker Swarm Monitoring with Sematext Docker Agent

We use a special build of the Sematext Docker Agent for swarm3k.
Differences to the regular Sematext Docker Agent Setup:
- Metrics, Logs and Events are stored only in Logsene. 
  This means the SPM backend will not be involved inthe Swarm3k project. 
- Kibana (integrated in Logsene) should be used for metrics visulisation.  
- Collection interval is set to 1 minute resolution (expecting 150k containers) to reduce the amount of data and speed up Kibana queries (less data points).
- Metrics and Logs are tagged with swarm specific tags from "docker info", like NodeID, ServiceID, Swarm labels, ...
- Collection of "docker info" 
- TODO: Node metrics like cpu/mem/IO are curently not stored in Logsene, we will fix this in the next days. 

# Installation 

1. Get a free account at [sematext.com/spm](https://apps.sematext.com/users-web/register.do)  
2. [create a Logsene App](https://apps.sematext.com/logsene-reports/registerApplication.do) to obtain an App Token for [Logsene](http://www.sematext.com/logsene/)  
3. Deploy Sematext Docker Agent to all cluster nodes. Please replace YOUR_LOGSNE_TOKEN with your Logsene token in the following command.

   ```
docker service create --mode global --name sematext-agent-docker \
type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock \ 
-e LOGENE_STATS_TOKEN=YOUR_LOGSENE_TOKEN \ # for metrics and docker events
-e LOGSENE_TOKEN=YOUR_LOGSNE_TOKEN \ # optional for container logs
sematext/sematext-agent-docker:swarm3k
   ```

    You’ll see your Docker metrics in Logsene after about a minute. 
    Create a Kibana dashboard for your metrics, events and logs. 


# Example Data:

## 1. Container Stats (_type: dockerstats): 

```
{
  "_index": "80e5977e-c7d2-4570-8f66-xxxxxxxxx_2016-09-24_1",
  "_type": "dockerstats",
  "_id": "AVdiqiHO417-Q-IWBmAo",
  "_score": null,
  "_source": {
    "@timestamp": "2016-09-25T18:44:53.344Z",
    "message": "stats for container helloworld.92.232aj5zegih6wr3l6g06hbjd5 fdfcbd8c5976",
    "severity": "info",
    "host": "b012c0a9e548",
    "ip": "172.17.0.71",
    "container_id": "fdfcbd8c5976",
    "image_name": "alpine:latest",
    "container_name": "helloworld.92.232aj5zegih6wr3l6g06hbjd5",
    "cpu_stats_cpu_usage_cpu_percent": 0.005344840145022679,
    "cpu_stats_throttling_data_throttled_time": 0,
    "network_rx_packets": 0,
    "network_rx_dropped": 0,
    "network_tx_packets": 11,
    "network_tx_dropped": 0,
    "memory_stats_usage": 69632,
    "memory_stats_failcnt": 0,
    "memory_stats_stats_pgfault": 0,
    "memory_stats_stats_pgpgout": 0,
    "blkio_stats_io_service_bytes_recursive_0_value": 0,
    "blkio_stats_io_service_time_recursive_0_value": 0,
    "blkio_stats_io_service_bytes_recursive_1_value": 0,
    "blkio_stats_io_service_time_recursive_1_value": 0,
    "container_hostname": "fdfcbd8c5976",
    "node_id": "e7herumhadti45itzlvsli6yu",
    "service_id": "7tjqymouhqsxjto7gdw6t2usb",
    "service_name": "helloworld",
    "task_name": "helloworld.92",
    "network_rx_bytes": 0,
    "network_rx_errors": 0,
    "network_tx_bytes": 1078,
    "network_tx_errors": 0,
    "memory_stats_limit": 513794048,
    "memory_stats_stats_pgpgin": 0,
    "blkio_stats_io_wait_time_recursive_0_value": 0,
    "blkio_stats_io_wait_time_recursive_1_value": 0
  }
 ```

## 2. Docker Events (_type: dockerEvent)

 
 ```
{
  "_index": "80e5977e-c7d2-4570-8f66-xxxxxxxxx_2016-09-24_1",
  "_type": "dockerEvent",
  "_id": "AVdiZrZF417-Q-IWpyaz",
  "_score": null,
  "_source": {
    "@timestamp": "2016-09-25T17:31:01.741Z",
    "message": "Docker Event: attach alpine:latest 1597a0b63999c144fc3d434483079959f920cb1019a5d2184b2c5e329ab41458 com.docker.swarm.node.id:3ud17y3bwt40lebmv3pk0cpz6, com.docker.swarm.service.id:7tjqymouhqsxjto7gdw6t2usb, com.docker.swarm.service.name:helloworld, com.docker.swarm.task:, com.docker.swarm.task.id:akdljc7dg1qfn894vfwis134n, com.docker.swarm.task.name:helloworld.91, image:alpine:latest, name:helloworld.91.akdljc7dg1qfn894vfwis134n",
    "severity": "info",
    "host": "e9ce7415ce1e",
    "ip": "172.17.0.3",
    "dockerEventStatus": "attach",
    "dockerEventType": "container",
    "dockerEventAction": "attach",
    "dockerEventFrom": "alpine:latest",
    "image_name": "alpine:latest",
    "container_id": "1597a0b63999",
    "container_name": "helloworld.91.akdljc7dg1qfn894vfwis134n",
    "dockerEventHost": "docker-512mb-fra1-01",
    "tags": [
      "docker",
      "docker-512mb-fra1-01",
      "attach",
      "1597a0b63999c144fc3d434483079959f920cb1019a5d2184b2c5e329ab41458"
    ]
  }
 ```
 
## 3. Docker Node Info (_type: docker_node_info)
 
```
{
  "_index": "80e5977e-c7d2-4570-8f66-xxxxxxxxx_2016-09-24_1",
  "_type": "docker_node_info",
  "_id": "AVdiZ6HwAHryUog82hLp",
  "_score": null,
  "_source": {
    "@timestamp": "2016-09-25T17:31:59.908Z",
    "message": "docker info: 20 containers running on node docker-512mb-fra1-01",
    "severity": "info",
    "host": "e9ce7415ce1e",
    "ip": "172.17.0.3",
    "docker_daemon_id": "QO7I:6CR7:TFJC:T6SX:WKZC:CMOI:2QB4:PLHZ:QVEK:MLNE:HY2P:EO6G",
    "containers": 339,
    "containers_running": 20,
    "containers_paused": 0,
    "node_mem_total": 489.9921875,
    "images": 13,
    "node_name": "docker-512mb-fra1-01",
    "swarm_node_id": "3ud17y3bwt40lebmv3pk0cpz6",
    "swarm_nodes": 4,
    "swarm_managers": 1
  }
  ```
  
## 4. Container Logs
 
**From a Docker Compose Project**
 
 ```
 {
  "_index": "80e5977e-c7d2-4570-8f66-xxxxxxxxx_2016-09-24_1",
  "_type": "wordpress_latest",
  "_id": "AVdiZ7BUAHryUog82ieI",
  "_score": null,
  "_source": {
    "@timestamp": "2016-09-25T17:32:22.421Z",
    "message": "Warning: mysqli::mysqli(): (HY000/2002): php_network_getaddresses: getaddrinfo failed: Name or service not known in - on line 19",
    "severity": "info",
    "host": "docker-512mb-fra1-01",
    "ip": "172.17.0.3",
    "logSource": "wordpress:latest_wordpress_wordpress_1_53f6353a46a3",
    "container_id": "53f6353a46a3",
    "image_name": "wordpress:latest",
    "container_name": "wordpress_wordpress_1",
    "container_hostname": "53f6353a46a3",
    "compose_project": "wordpress",
    "compose_container_number": "1",
    "compose_service": "wordpress"
  }
  ```
  
**From a Swarm Service (_type: imageName)**
 
 ```
  {
  "_index": "80e5977e-c7d2-4570-8f66-xxxxxxxxx_2016-09-24_1",
  "_type": "access_log_combined",
  "_id": "AVdi_FvkAHryUog8oyEn",
  "_score": null,
  "_source": {
    "@timestamp": "2016-09-25T20:14:30.000Z",
    "message": "GET / HTTP/1.1",
    "severity": "info",
    "host": "docker-512mb-fra1-01",
    "ip": "172.17.0.2",
    "logSource": "nginx:latest_nginx.3.7yggv9wpg3yvfgujqe07hoo2x_159b591f960d",
    "client_ip": "10.255.0.3",
    "remote_id": "-",
    "user": "-",
    "ts": "25/Sep/2016:20:14:30 +0000",
    "method": "GET",
    "path": "/ HTTP/1.1",
    "status_code": 200,
    "size": 612,
    "referer": "-",
    "user_agent": "curl/7.35.0",
    "container_id": "159b591f960d",
    "image_name": "nginx:latest",
    "container_name": "nginx.3.7yggv9wpg3yvfgujqe07hoo2x",
    "container_hostname": "159b591f960d",
    "node_id": "3ud17y3bwt40lebmv3pk0cpz6",
    "service_id": "7onbow9pk4e5xsgsfkjrz7t3r",
    "service_name": "nginx",
    "task_name": "nginx.3"
  }
  ```
 
