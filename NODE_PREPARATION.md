# Node Preparation

  0. The join command *must* be `docker swarm join --advertise-addr=<dedicated-public-ip> <manager-ip>`, where `manager-ip` will be provided.
  0. Note that you *need* to specify a *Dedicated Public IPv4 Address* for the node to join. Otherwise, the Routing Mesh feature will not be working on your node.
  0. Please read No. 2 again ;-)
  0. Docker version: 1.12.2
  0. Ubuntu version: 16.04
  0. Public IPv4 for *each node*
  0. TCP port 2377 for cluster management
  0. TCP and UDP port 7946 for communication among nodes
  0. TCP and UDP port 4789 for overlay network
  0. Append following settings in `/etc/sysctl.conf` and issue command `sysctl -p` afterwards.
```
net.ipv4.neigh.default.gc_thresh1 = 30000
net.ipv4.neigh.default.gc_thresh2 = 32000
net.ipv4.neigh.default.gc_thresh3 = 32768
```
  
# Workloads

  0. The first workload will be a Wordpress cluster ~ 2,900 nodes connecting to Percona Galera XtraDB.
  0. The second wordload will be `alpine top` to stress the Docker swarm managers by maximizing task numbers. We are expecting to reach 150,000 tasks for this run.
