# ClusterHAT review

_Captured: 2017-05-20 at 10:33 from [www.raspberrypi.org](https://www.raspberrypi.org/magpi/clusterhat-review/)_

![](https://www.raspberrypi.org/magpi/wp-content/uploads/2017/03/ClusterHAT_Boards-1.jpg)

> _Building a computer cluster is one of the most impressive Raspberry Pi projects. And being able to program cluster computers is one of the most highly valued skills in the world of big data._

A cluster is a set of computers networked together and used as a single system. Each computer (or 'node') is scheduled to work on the same task, controlled by a master computer.

_The full article can be found in [The MagPi 55](https://www.raspberrypi.org/magpi/issues/magpi/55) and was written by Lucy Hattersley._

Knowing how to manage, and use, clustered computers and supercomputers is a pretty valuable skill. It's also one of the areas at the absolute forefront of computing technology.

But it has always been difficult to get started. Traditionally, cluster computing has been an expensive hobby. You need lots of computers (preferably identical) and a network controller and the skill to network them all together. This difficulty is before you even start learning how to manage several computers working in tandem.

On top of all that, it can be expensive to run multiple full-sized computers. Energy costs quickly ramp up when you're running a cluster.

### Hat on it

The [Cluster HAT](https://shop.pimoroni.com/products/cluster-hat) removes the expense and effort required to create a cluster. This lower barrier to entry makes it a lot easier to get on with the more important act of learning cluster computing technologies.

The HAT sits on top of a Raspberry Pi 2/3 and you slot four Pi Zero computers on to the HAT (via the USB connection).

A USB cable is run from the Raspberry Pi to the HAT to provide power to the four Pi Zero boards. The latter are controlled directly via the GPIO pins.

You need a microSD card for each Pi Zero, and one for the controlling Raspberry Pi. So that's five SD cards in total.

We costed up a Raspberry Pi, Cluster HAT, four Pi Zero boards, and four official microSD cards - it comes to £102\. That's by far the cheapest cluster computer you will find on the market. For those looking to get into cluster computing, this is a game-changer.

### Getting started

Setting up the Cluster HAT hardware was an absolute breeze. Screw the four pins on to a Raspberry Pi 3 board and insert the supplied USB cable, then attach the HAT (wiring the cable between the board and HAT). Attach the USB power to the HAT and then slot on the four Pi Zero boards. The whole setup took less than five minutes.

Software is well handled too. A dedicated site (magpi.cc/2jHMeQq) provides image files for the controller (the Pi 2/3) and one image file for each Pi Zero board.

The Cluster HAT version of Raspbian boots into the command line, but offers a script for controlling the cluster. For example:

This command-line code switches on all four Pi Zero boards. You can also control them separately, using p1-4. Such as:

It takes a few moments for each Pi Zero to power up and load its software, at which point it'll appear in ifconfig.

Access each node using SSH (enabled by default):

Here you can use ifconfig to find the IP address Cluster HAT has assigned to the Pi Zero (under USB Ethernet).

### Pi computing

One thing this isn't, though, is a supercomputer. There's a good set of benchmarks by Nick Smith on [Climbers.net](http://climbers.net/sbc/clusterhat-review-raspberry-pi-zero/).

Nick used iperf to test the network-over-USB connection and found it comparable to Ethernet.

The slower speed of the Pi Zero boards compared to Raspberry Pi 2/3 boards is much more pronounced.

Nick benchmarked the system using [HPC Challenge Benchmark](http://icl.cs.utk.edu/hpcc/). He found the cluster of four Pi Zero boards ran at roughly half the speed of a single Raspberry Pi 3 board.

The slower speed makes sense when you think about it. Nick explains: "This is partly down to the faster individual cores in the Pi 3, but also the node-node communication is obviously a great deal faster within the Pi 3 SoC compared to communicating between separate Zeros with Ethernet-over-USB."

So you're not building a faster Raspberry Pi. However, we don't think this matters. The aim for most people will be to build a low-cost and relatively easy‑to‑assemble cluster for educational purposes.

Once created, you can start to experiment with the concepts behind cluster computing. The Cluster HAT is ideal for teaching, learning or developing cluster computing ideas.

We suspect it will also appeal to developers who have access to larger cluster computing systems, but not all the time. You can test and run code on the Cluster HAT, then migrate it across to a larger system.

### Distributed computing

Cluster computing is not a game for beginners. Realistically speaking, prospective learners will need a working knowledge of Python, Java, SQL (and relational database techniques). You'll also need a good understanding of the Linux command line.

Fortunately, starters are not alone. There's a vibrant [Cluster HAT Google Groups board](https://groups.google.com/forum/#!forum/clusterhat). There are lots of resources and projects being shared by the community.

One book that is recommended reading is [Raspberry Pi Super Cluster (£16.78) by Andrew K Dennis](https://www.packtpub.com/hardware-and-creative/raspberry-pi-super-cluster).

Whatever resources you choose, we think the Cluster HAT is a great resource for starting distributed computing. It's small, cheap, and easy to set up.

You have to leap a lot of hurdles to learn cluster computing. But Cluster HAT removes the expensive and difficult hardware build. It's then up to you to learn the sophisticated coding techniques.

### Final word

5/5

A compact, neat and cost-effective solution to building a cluster computer. The end-product might lack raw power, but it's perfect for teaching and learning distributed computing concepts.
