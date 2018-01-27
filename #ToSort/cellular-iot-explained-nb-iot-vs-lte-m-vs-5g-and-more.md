# Cellular IoT Explained – NB-IoT vs. LTE-M vs. 5G and More

_Captured: 2017-11-04 at 17:43 from [www.iotforall.com](https://www.iotforall.com/cellular-iot-explained-nb-iot-vs-lte-m/amp/)_

![Cellular-IoT-Explained-–-NB-IoT-vs.-LTE-M-vs.-5G-and-More](https://www.iotforall.com/wp-content/uploads/2016/12/Cellular-IoT-Explained-–-NB-IoT-vs.-LTE-M-vs.-5G-and-More.jpg)

> _Yitaek Hwang >Categories: Connectivity December 30, 2016_

With the Consumer Electronics Show (CES) kicking off next week, the buzz around 5G -- especially its relation to cellular IoT -- has been growing. A quick Google search on 5G IoT brings up related articles on NB-IoT and how [Verizon and AT&T are set to commercialize LTE-Cat M1](http://www.fiercewireless.com/tech/verizon-at-t-both-claim-lte-cat-m-firsts-for-internet-things) next year as well. But attempts to decode the acronyms fall short, searching "NB-IoT vs. LTE-M" just brings up confusing summaries like this:

![Cellular IoT - unhelpful explanation of nb-iot, cat-0, and others](https://cdn-images-1.medium.com/max/800/1*NElcQqs2kIB_OLC56es04w.jpeg)

I don't know about you, but this didn't help me at all. It was as if 3GPP (the group behind 3G) decided to keep out new players by overwhelming them with cryptic acronyms and esoteric technical definitions. We all know 4G is faster than 3G and 2G, so 5G is probably going to follow that trend…but Cat-1 and EC-GSM? What are those?

Fear not! After some digging, I've translated the technical details of each option into laymen's terms, so you can be prepared for CES 2017 and the oncoming wave of cellular IoT.

## Where did cellular IoT come from?

Popularity and ubiquity of IoT devices has led to the rise of low-power, wide-area network (LPWAN) options such as SigFox, LoRa, and Weightless (here's [why LPWAN is important in IoT](https://iotforall.com/what-is-lpwan/) and [a breakdown of the different options](https://iotforall.com/comparison-of-lpwan-technologies/)).

Traditional cellular options such as 4G and LTE networks consume too much power and don't fit well with applications where only a small amount of data is transmitted infrequently (e.g. meters for reading water levels, gas consumption, or electricity use).

Cellular IoT is meant to meet the requirements of low-power, long-range applications.

### Cat-1

Cat-1 is the **_only fully-available_** cellular IoT option at the moment and represents an early push towards connecting IoT devices using existing LTE networks. While the performance is inferior to 3G networks, it's an excellent option for IoT applications that require a browser interface or voice. The major attraction is that it's already standardized, and more importantly, it's simple to transition into the Cat-1 network. Experts predict that as 3G technology sunsets, Cat-1 networks will take its place.

### Cat-0

For LTE-based IoT networks to succeed, they need to have the following characteristics: 1) long battery life, 2) low cost, 3) support for high volume of devices, 4) enhanced coverage (better signal penetration through walls for example), and 5) long rage/wide spectrum.

Cat-0 **optimizes for cost** as it eliminated features that supported high data rate requirements for Cat-1 (dual receiver chain, duplex filter). If Cat-1 is poised to replace 3G, Cat-0 sets the groundwork for Cat-M to replace 2G as the cheaper option.

### Cat-M1/Cat-M/LTE-M

Cat-M (officially known at LTE Cat-M1) is often viewed as the second generation of LTE chips built for IoT applications. It completes the cost and power consumption reduction that Cat-0 set the stage for. By capping the maximum system bandwidth to 1.4 MHz (as opposed to 20 MHz for Cat-0), Cat-M is really targeting LPWAN applications like smart metering where only small amount of data transfer is required.

This page contains a form, you can see it [here](https://www.iotforall.com/cellular-iot-explained-nb-iot-vs-lte-m/?view-original-redirect=1).

But the true advantage of Cat-M over other options out there, is that **Cat-M is compatible with the existing LTE network**. For carriers such as Verizon and AT&T, this is great news as they don't have to spend money to build new antennas. They simply need to upload new software as long as the devices operate within its LTE network. The existing customer bases of these two companies will most likely hear that Cat-M is by far the superior option.

### NB-IoT/Cat-M2

NB-IoT (also called Cat-M2) has a similar goal to Cat-M, but it uses a different technology (DSSS modulation vs. LTE radios). Therefore, NB-IoT doesn't operate in the LTE band, meaning that providers have a higher upfront cost to deploy NB-IoT.

Still, NB-IoT is touted as the **potentially less expensive option** as it eliminates the need for a gateway. Other infrastructures typically have gateways aggregating sensor data, which then communicates with the main server (here's a [deeper explanation of gateways](https://iotforall.com/what-is-a-gateway/)). With NB-IoT, sensor data is sent directly to the main server. For this reason, Huawei, Ericsson, Qualcomm, and Vodafone are actively researching and making an effort to commercialize NB-IoT.

### EC-GSM (formerly EC-EGPRS)

EC stands for Extended Coverage. EC-GSM is the IoT-optimized GSM network, the wireless protocol used by 80% of smart phones globally. As the name suggests, this can be deployed in existing GSM networks. Ericsson, Intel, and Orange are said to have completed live trials of EC-GSM earlier this year. EC-GSM, however, isn't generating as much buzz as Cat-M or NB-IoT.

### 5G

Unlike the cellular IoT options above, 5G has **yet to be officially defined**. Next Generation Mobile Networks Alliance (NGMN) is pushing for specs for it to be 40 times faster than 4G, while supporting up to 1 million connections per square kilometer. 5G will most likely enable high-bandwidth, high-speed applications for Ultra-HD (4k) streaming, self-driving car connectivity, or VR/AR applications.

Still, talks are being made to also support IoT devices with 5G-IoT networks. However, all **these are just speculations** as 3GPP will finalize the specifications in 2019. The commercial rollout target year is 2020 according to NGMN's timeline.

## Why You Should Care

If you are a cellular carrier provider, you will be forced to choose a technology to deploy to meet the narrowband IoT applications.

For the rest of us, it's important to understand that these different options **do not **necessarily have to be **mutually exclusive**. This extends to other LPWAN players like SigFox, LoRa, Weightless, and Ingenu (read more at [Calum McClelland](https://medium.com/@calummcclelland)'s "[Which LPWAN Technology is Right for You](https://iotforall.com/comparison-of-lpwan-technologies/)").

IoT covers a broad spectrum of applications. Sometimes you need high bandwidth, like with real-time surveillance. For asset tracking, data throughput is small, but there are inevitably many handovers as objects move. Smart meters and many smart city use-cases require small data transfer once or twice a day. This means that no one technology (even 5G) may fit the specific needs of an IoT solution/device.

Fragmentation within IoT sucks, but it exists because IoT is so broad. Don't be fooled by the marketing noise claiming superiority of one technology over another.

The answer is always, "it depends."
