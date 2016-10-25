# Node Preparation

  * Docker 1.12.2
  * Ubuntu 16.04
  * TCP port 2377 for cluster management
  * TCP and UDP port 7946 for communication among nodes
  * TCP and UDP port 4789 for overlay network
  * Setting in `/etc/sysctl.conf`
```
net.ipv4.neigh.default.gc_thresh1 = 30000
net.ipv4.neigh.default.gc_thresh2 = 32000
net.ipv4.neigh.default.gc_thresh3 = 32768
```

# Workloads

  0 The first workload will be a Wordpress cluster ~ 2,900 nodes connecting to Percona Galera XtraDB.
  0 The second wordload will be `alpine top` to stress the Docker swarm managers by maximizing task numbers. We are expecting to reach 150,000 tasks for this run.
