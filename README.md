# Swarm3k
SwarmZilla 3000 Collaborative Project

## We now have **760 nodes** and counting !!

## Special Thanks

![DigitalOcean](https://www.digitalocean.com/assets/media/logos-badges/DO_Logo_horizontal_blue-1fdb454a.png)

[DigitalOcean](http://digitalocean.com) gave us $250 credits to provision nodes for this project.

![Sematext](https://sematext.com/wp-content/uploads/2016/02/sematext-logo-250-45.png)

[Sematext](https://sematext.com) joins us as our official monitoring and logging system.

## Contribution Proposal
  0. Please create a pull request, saying you'd like to contribute nodes.
  Please also include your full name, Twitter's handle *and* your company name.
  0. Date for the experiments will be announced after we get more than 3,000 nodes.
  0. Please note that the node's specification for this run is **1GB of RAM with 1 vCore**.
  We're sorry that 512MB will be not enough for our testing this time.

| Name          | Company       | Number of Nodes<br>Expected to Contribute |
| ------------- |:-------------:|:-----------------------------------------:|
| [@chanwit](https://twitter.com/chanwit) | Suranaree University | 100 |
| [@FlorianHeigl](https://twitter.com/FlorianHeigl1) | my own boss | 10 | 
| [@jmaitrehenry](https://twitter.com/jmaitrehenry) | PetalMD | 50 |
| [@everett_toews](https://twitter.com/everett_toews) | Rackspace | 100 |
| [@InetCloudArch](https://twitter.com/InetCloudArch) | Internet Thailand | 500 |

## Beginner's Guide
If you're an individual and it's your first time joining SwarmZilla, we encourage you to *not* contribute more than 50 nodes.
The provision steps for number of nodes more than 50 will make things complex.

If you're joining us for the second time (welcome back Heroes!!), feel free to contribute any number of nodes.

## Goals
This is the 2nd collaborative project to distributedly form a huge Docker cluster.
SwarmZilla 3000 will be targeting 3,000 nodes. This test will be done on the stable 1.12.2 version of Docker to make it more stable of course.

  * Networking; We will be creating a large subnet /20 and trying to assign, as many as possible, IP addresses to each container on each node distributedly. We expect to have around ~3,000 IP addresses assigned and the workload application should be working fine.
  * Routing Mesh; We will be testing the Routing Mesh feature on Docker 1.12.2.
  * For the routing mesh tests, the workload will be Wordpress applications. We're designing this.

## Public results
All experimental results will be provided publicly for all of you to analyze, write blogs,
or even used as information for further development of your own commercial projects. Please feel free to use it.
If you'd like to refer to the set of published data, just link back to this project page.
