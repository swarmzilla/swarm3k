# Swarm3k - We'll do it on Friday, 28 October 2016 3.00PM UTC
SwarmZilla 3000 Collaborative Project

## We now have **3,060 nodes** and counting !!

## Special Thanks

![DigitalOcean](https://www.digitalocean.com/assets/media/logos-badges/DO_Logo_horizontal_blue-1fdb454a.png)

[DigitalOcean](http://digitalocean.com) gave us $250 credits to provision nodes for this project.

![Sematext](https://sematext.com/wp-content/uploads/2016/02/sematext-logo-250-45.png)

[Sematext](https://sematext.com) joins us as our official monitoring and logging system.

![Demonware](https://dl.dropboxusercontent.com/u/381580/demonware.png)

[Demonware](https://www.demonware.net) joins us with their 1,000 nodes.

## Contribution Proposal
  0. Please create a pull request, saying you'd like to contribute nodes.
  Please also include your full name, Twitter's handle *and* your company name.
  0. Date for the experiments will be announced after we get more than 3,000 nodes.
  0. Please note that the node's specification for this run is **1GB of RAM with 1 vCore**.
  We're sorry that 512MB will be not enough for our testing this time.
  
## What's mininum requirements of a node?
  0. For the security reason, we do not provision or operate your nodes directly. *A cool engineer* on your side will be responsible for provision and join the cluster using the provided token
  0. Token will be provided in this room: gitter.im/swarmzilla/swarm3k during the run.
  0. Last time, we ran the Swarm2K cluster around 8 hours. Basically, you can expect this run of Swarm3K will be around 8 hours too.
  0. Each node must have a public IPv4 on its network interface. Floating IPs cannot be used to join this public cluster.
  0. Docker 1.12.2 (will be released very soon)
  0. TCP port 2377 for cluster management
  0. TCP and UDP port 7946 for communication among nodes
  0. TCP and UDP port 4789 for overlay network

| Name          | Company       | Number of Nodes<br>Expected to Contribute |
| ------------- |:-------------:|:-----------------------------------------:|
| [@chanwit](https://twitter.com/chanwit) | Suranaree University | 100 |
| [@FlorianHeigl](https://twitter.com/FlorianHeigl1) | my own boss | 10 | 
| [@jmaitrehenry](https://twitter.com/jmaitrehenry) | PetalMD | 50 |
| [@everett_toews](https://twitter.com/everett_toews) | Rackspace | 100 |
| [@InetCloudArch](https://twitter.com/InetCloudArch) | Internet Thailand | 500 |
| [@squeaky_pl](https://twitter.com/squeaky_pl) | n/a | 10 |
| [@neverlock](https://twitter.com/neverlock) | Neverlock | 10 |
| [@demonware](https://twitter.com/demonware) | Demonware | 1000 |
| [@sujaypillai](https://twitter.com/sujaypillai) | Jabil | 50 |
| [@pilgrimstack](https://twitter.com/pilgrimstack) | OVH | 500 |
| [@ajeetsraina](https://twitter.com/ajeetsraina) | Collabnix | 10 |
| [@AorJoa](https://twitter.com/aorjoa) | Aiyara Cluster | 10
| [@f_soppelsa](https://twitter.com/f_soppelsa) | Personal | 20
| [@GroupSprint3r](https://twitter.com/GroupSprint3r) | SPRINT3r | 630
| [@toughIQ](https://twitter.com/toughiq) | Personal | 30
| [@mrnonaki](https://twitter.com/mrnonaki) | N/A | 10
| [@zinuzoid](https://twitter.com/zinuzoid) | HotelQuickly | 20
| [@first087](https://twitter.com/first087) | N/A | 25

## Beginner's Guide
If you're an individual and it's your first time joining SwarmZilla, we encourage you to *not* contribute more than 50 nodes.
The provision steps for number of nodes more than 50 will make things complex.

If you're joining us for the second time (welcome back Heroes!!), feel free to contribute any number of nodes.

## Goals
This is the 2nd collaborative project to distributedly form a huge Docker cluster, targeting 3,000 nodes.

We understand Docker and we also understand that the community needs long-term versions of Docker. This test will be done on the stable 1.12.2 version of Docker to get feedbacks and of course to make the next stable versions being more stable!!

  * Networking; We will be creating a large subnet /20 and trying to assign, as many as possible, IP addresses to each container on each node distributedly. We expect to have around ~3,000 IP addresses assigned and the workload application should be working fine.
  * Routing Mesh; We will be testing the Routing Mesh feature on Docker 1.12.2.
  * For the routing mesh tests, the workload will be Wordpress applications. We're designing this.

## Public results
All experimental results will be provided publicly for all of you to analyze, write blogs,
or even used as information for further development of your own commercial projects. Please feel free to use it.
If you'd like to refer to the set of published data, just link back to this project page.
