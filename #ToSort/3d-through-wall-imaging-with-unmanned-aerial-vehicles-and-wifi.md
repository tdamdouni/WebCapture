# 3D Through-Wall Imaging With Unmanned Aerial Vehicles and WiFi

_Captured: 2017-11-26 at 10:48 from [www.ece.ucsb.edu](http://www.ece.ucsb.edu/~ymostofi/3DThroughWallImaging.html)_

[ 3D Through-Wall Imaging with WiFi and Drones](https://www.youtube.com/watch?v=THu3ZvAHI9A)

WiFi signals are everywhere these days. Unmanned aerial vehicles are expected to become a part of our near-future society. In this paper, we are interested in the possibilities created at this intersection of robotics and communication. More specifically, we propose a new methodology that enables the first demonstration of high-resolution 3D through-wall imaging of completely unknown areas, **using only WiFi signals and unmanned aerial vehicles**. Some of the key features of our approach are as follows: 1) only WiFi RSSI measurements are used, 2) no prior measurements need to be made in the area of interest, and 3) the objects do not have to move to be imaged. Here, we briefly summarize our proposed approach and show sample experiments results. See the [paper](http://www.ece.ucsb.edu/~ymostofi/papers/IPSN17_KaranamMostofi.pdf) and [video](https://www.youtube.com/watch?v=THu3ZvAHI9A) for more details.

  * C.R. Karanam and Y. Mostofi, "3D Through-Wall Imaging with Unmanned Aerial Vehicles Using WiFi," in the proceedings of the 16th ACM/IEEE International Conference on Information Processing in Sensor Networks (IPSN), April 2017.[[pdf](http://www.ece.ucsb.edu/~ymostofi/papers/IPSN17_KaranamMostofi.pdf)] 

In this paper, we have proposed a new approach that has enabled 3D through-wall imaging of completely unknown areas with only WiFi signals and Unmanned Aerial Vehicles (UAVs). Two UAVs move autonomously outside of the area of interest, while one transmits a WiFi signal and the other one measures the received signal strength (RSSI) of the corresponding transmission, in order to image the unknown area in 3D using our proposed approach. The figures below show two examples of the UAVs in action.

![](http://www.ece.ucsb.edu/~ymostofi/3DImagingPics/two_copters_scenario.png)

Figure 1. Two examples of our considered scenario where two UAVs fly outside an unknown area to collect WiFi RSSI measurements for the purpose of 3D through-wall imaging based on our proposed approach. 

There are four tightly-integrated key components to our proposed approach to enable 3D through-wall imaging, as shown in the figure below. First, we have proposed robotic paths that can capture the spatial variations in all the three dimensions as much as possible while maintaining the efficiency of the operation. Second, we have modeled the 3D unknown area of interest as a Markov Random Field and utilized Loopy Belief Propagation to update the imaging decision of each voxel. In order to approximate the interaction of the transmitted wave with the area of interest, we have used the WKB linear wave model. Finally, we have also taken advantage of the compressibility of the information content to image the area with a very small number of WiFi measurements (less than 4%), using sparse signal processing.

![](http://www.ece.ucsb.edu/~ymostofi/3DImagingPics/key_components.png)

> _Figure 2. Key components of our proposed approach for 3D through-wall imaging._

In [our past work](http://www.ece.ucsb.edu/~ymostofi/SeeThroughImaging.html), we have extensively worked on through-wall imaging with WiFi signals and have shown several experimental results in 2D. However, enabling 3D through-wall imaging beyond simulations is considerably challenging, due to the considerable increase in the number of unknowns. This is then the main motivation for the proposed methodology of this paper.

Here, we show two sample experimental results on our campus. The UAVs have no prior measurements in the area of interest, and the area is completely unknown to them. The results were obtained with less than 4% WiFi measurements, indicating the efficiency of the operation.

![](http://www.ece.ucsb.edu/~ymostofi/3DImagingPics/result_two_cube.png)

Figure 3. (left) Top view of the 3D area of interest, (middle) the 3D binary ground-truth image of the unknown area to be imaged, which has the dimensions of 2.96 m x 2.96 m x 0.4 m, and (right) the reconstructed 3D binary image using our proposed framework. 

![](http://www.ece.ucsb.edu/~ymostofi/3DImagingPics/result_L_shape.png)

Figure 4. (left) Top view of the 3D area of interest, (middle) the 3D binary ground-truth image of the unknown area to be imaged, which has the dimensions of 2.96 m x 2.96 m x 0.5 m, and (right) the reconstructed 3D binary image using our proposed framework. 

The figure below summarizes our experimental testbed, which consists of only off-the-shelf units. More specifically, the transmitting UAV (TX UAV) is equipped with a WiFi router for WiFi transmission and a Google Tango tablet for localizing itself. Similarly, the receiver UAV (RX UAV) has a Raspberry Pi unit, a WiFi card for measuring the WiFi RSSI, and a Tango tablet for localizing itself. The autonomous UAVs have way-points to achieve along their routes and will constantly coordinate with each other so that they are at the right transmit/receive position pairs.

![](http://www.ece.ucsb.edu/~ymostofi/3DImagingPics/exp_setup.png)

> _Figure 5. An overview of the experimental testbed._

There are several potential applications that can benefit from obtaining a high-resolution 3D image of an unknown area through walls with safe everyday WiFi signals. Emergency response, archeological discovery, and structural monitoring, for instance, are a few examples.

  * Lucas Buckland, Harald Schafer, Saandeep Depatla, Arjun Muralidharan, Herbert Cai, Belal Korany and Paige Sullivan for helping with the experiments. 
  * Dept. of ECE and College of Engineering at UCSB for facilitating the experiments. 

Copyright (C) 2007
