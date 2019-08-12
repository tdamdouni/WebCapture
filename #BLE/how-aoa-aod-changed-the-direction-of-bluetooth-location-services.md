# How AoA & AoD Changed the Direction of Bluetooth Location Services

_Captured: 2019-04-28 at 23:03 from [www.bluetooth.com](https://www.bluetooth.com/blog/new-aoa-aod-bluetooth-capabilities/?utm_source=tw&utm_medium=ad&utm_term=social&utm_content=tw-newaoaaodboost-paid&utm_campaign=location-services)_

While _Bluetooth®_ location services have seen tremendous success based on current capabilities, there is a market demand for solutions that can provide even greater performance. Some real-time location services (RTLS) deployments require location accuracy down to centimeter level. Fortunately, a new feature has recently been added to Bluetooth technology that will enable the development of [location services solutions](https://blog.bluetooth.com/new-direction-finding-feature?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding) capable of meeting centimeter-level performance requirements.

![](https://3pl46c46ctx02p7rzdsvsg21-wpengine.netdna-ssl.com/wp-content/uploads/page-content/Point-of-Interest_2_Gray_Square_MK.jpg)

## Adding Direction Finding

The term _radio direction finding_ refers to the practice of determining the direction from which a received signal was transmitted. Radio direction finding has been in practice since the early twentieth century and is used in systems to support everything from aviation and nautical navigation to wildlife tracking.

In [version 5.1 of the Bluetooth Core Specification](https://www.bluetooth.com/specifications/bluetooth-core-specification?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding), Bluetooth added an optional direction finding capability. Using this new feature, a Bluetooth device can determine the direction of a signal being transmitted from another Bluetooth device. This seemingly basic capability has the potential to significantly enhance Bluetooth location services solutions.

Bluetooth location services currently use RSSI to estimate the distance between two devices and, in the case of RTLS and indoor positioning system (IPS) solutions, use those distance estimates and trilateration to determine the position of a device. Now, with direction finding, those same devices can also use information about the direction of another device and, for RTLS and IPS solutions, use triangulation to improve location accuracy.

The new Bluetooth direction finding feature supports two methods for determining the direction of a Bluetooth signal, both of which are based on the use of an antenna array: angle of arrival (AoA) and angle of departure (AoD).

![](https://3pl46c46ctx02p7rzdsvsg21-wpengine.netdna-ssl.com/wp-content/uploads/2019/03/resources_icons_white_paper-0.svg)

![](https://3pl46c46ctx02p7rzdsvsg21-wpengine.netdna-ssl.com/wp-content/uploads/2019/03/Figure_AoA.png)

## Direction Finding Using Angle of Arrival

In the angle of arrival (AoA) method, the device to which direction is being determined, such as a tag in an RTLS solution, transmits a special direction finding signal using a single antenna. The receiving device, such as a locator in that same RTLS solution, has multiple antennae arranged in an array. As the transmitted signal crosses the array, the receiving device sees a signal phase difference due to the difference in distance from each of the antenna in its array to the transmitting antenna. The receiving device takes IQ samples of the signal while switching between the active antenna in the array. Based on the IQ sample data, the receiving device can calculate the relative signal direction. The AoA method of direction finding is intended for use with RTLS as well as [proximity solutions](https://blog.bluetooth.com/bluetooth-proximity-solutions?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding), such as item finding and point of interest (PoI) information services.

## Direction Finding Using Angle of Departure

**![](https://3pl46c46ctx02p7rzdsvsg21-wpengine.netdna-ssl.com/wp-content/uploads/2019/03/Figure_AoD.png)

**

In the angle of departure (AoD) method, the device to which direction is being determined, such as a locator beacon in an IPS solution, transmits a special signal using multiple antennae arranged in an array. The receiving device, such as a mobile phone in that same IPS solution, has a single antenna.

As the multiple signals from the transmitting device cross the antenna in the receiving device, the receiving device takes IQ samples. Based on the IQ sample data, the receiving device can calculate the relative signal direction. The AoD method of direction finding is intended for use in [IPS solutions](https://blog.bluetooth.com/bluetooth-positioning-systems?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding), such as those used for wayfinding.

## A New Direction for Blue

Key proximity and positioning use cases stand to reap the benefits of the new Bluetooth direction finding feature.

**Item Finding Solutions**

Item finding solutions stand to experience a big bump in user experience. Once smartphone vendors integrate Bluetooth direction finding with AoA support into their phones, item finding solutions will be able to leverage directional information. Which means they'll not only be able to identify how close a misplaced item is, they'll also determine its direction, eliminating the need for guesswork when finding lost items.

**PoI Information Solutions**

PoI information solutions could also benefit from direction finding with AoA being added to smartphones. Imagine a room in a [museum with multiple exhibits](https://blog.bluetooth.com/ngv-bluetooth-location-services?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding) that has associated beacons. Currently, a PoI information application on a smartphone can inform a user of all the exhibits in the room and allow them to select one to receive additional information. With direction finding support, users will be able to simply point their smartphone at a specific exhibit to get more information on that item.

**RTLS Solutions**

By implementing direction finding, RTLS solutions could improve location accuracy down to centimeter level in the right deployment environment. RTLS with direction finding will enable a factory to track the location and flow of materials with greater precision while also alerting workers before they go into unsafe work areas.

**IPS Solutions**

IPS solutions also stand to benefit from direction finding support. Imagine a positioning system that can navigate a fan visiting a large stadium venue not just to their section but to their seat. Or a [shopper in a store](https://blog.bluetooth.com/mall-of-america?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding) not just to the area or aisle a product is on but to the shelf. In addition, IPS solutions with direction finding may require fewer locator beacons to achieve greater accuracy, bringing further efficiency to deployments. And the accuracy gained will also provide incremental data and knowledge on the interaction between products and consumers.

The Bluetooth community is continually enhancing the technology to address new market opportunities while meeting the ever-expanding needs of traditional markets and use cases. The addition of direction finding is the latest in a series of recent advancements, and it brings established, time-tested methods for determining signal direction to a proven, trusted radio.

[Download](https://www.bluetooth.com/bluetooth-resources/paper-enhancing-bluetooth?utm_campaign=location-services&utm_source=internal&utm_medium=blog&utm_content=AoA-AoD-direction-finding) this paper, _Enhancing Bluetooth Location Services with Direction Finding_, to learn more about how the Bluetooth community is enhancing Bluetooth location services solutions.
