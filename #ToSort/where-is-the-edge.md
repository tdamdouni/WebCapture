# Where Is the Edge?

_Captured: 2017-05-05 at 23:55 from [dzone.com](https://dzone.com/articles/where-is-the-edge?edition=297993&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-05)_

Edge computing has data, applications, and services at the logical extremes of a network near the sensors or in the devices generating data, and away from centralized cloud data centers. Data management, communication, and some analytics occur at the source of the data i.e., in each device which is much smaller in scale compared to the cloud. This "small data" approach allows each local device to assess its own health and performance - particularly when immediacy of decision making is critical. With pre-processing at the edge, "Big Data" in the cloud becomes easier to manage.

## Defining the Edge

The edge includes intelligent devices like instruments, special purpose computers like PLCs, and more general purpose computers like Raspberry Pis. These devices often have edge computing functions including a network connection, storage and some software specific to the device. The edge also includes sensors that connect to network gateways having the edge computing resources.

![Edge Computing Architecture](https://cdn2.geready.com/digital/sites/default/files/Edge-computing-architecture-580x345.jpg)

An automotive analogy illustrates this distinction between edge and cloud computing. Electric cars contain software to assess the health and performance of the batteries. This battery management system reads data from the sensors, stores it in the car, and uses analytics to alert the driver when health degrades i.e., small data with edge computing. When connected to the internet, the data is uploaded to the cloud where more advanced analytics assess performance across a range of cars, driver profiles, driving conditions and climates. This helps engineers design better batteries and cars i.e., big data with analytics in the cloud.

![Common Edge Devices](https://cdn2.geready.com/digital/sites/default/files/Edge-devices-580.jpg)

## What Happens at the Edge?

At the edge, we have data storage, buffering, communication, filtering/preparation, transportation, and limited analytics (compared to what is available in the cloud). Typical applications involve algorithms to assess equipment health and alert the operator when issues arise. In addition, analytics for improved process control have recently started to emerge. On the cloud, similar applications for health monitoring and process optimization exist, but with the added capability to aggregate data from many IoT devices. The higher volume of data with its inherent added intricacy are combined with more advanced analytics to anticipate issues further into the future. Thus, strategic decision support is best in the cloud. The more immediate, tactical decisions can be done at the edge.

## Why Use the Edge in Industrial Environments?

In an industrial IoT system with only centralized resources, a network interruption becomes lost data, delayed problem identification, and lost alerts. This could involve loss of predictive maintenance alerts causing unplanned downtime, or missed opportunities for process optimization.

Resources at the edge help to mitigate these network outage issues. Related constraints with similar impact include network latency (delay) and bandwidth (throughput). Edge computing helps to mitigate a single point of failure for a more robust IIoT solution when part of the network is compromised by physical (hardware), virtual (software) or security failures.

Usually, most edge data are noise to the larger system in the sense that it has no real use. For example, when monitoring condition, do the centralized resources want the data when nothing changed? When meaningful change is detected, then the data needs to be transferred. It does no good to use data transport, storage and processing resources putting data into the cloud when it is not useful.

## Recommendation

Industrial IoT applications often involve mission critical objectives for asset intensive industries like reducing unplanned downtime, improving worker safety and enhancing asset performance. Edge computing assures a robust architecture more resilient to issues with the network or centralized resources. Today, many original equipment manufacturers (OEM) provide condition monitoring services to their customers. For particularly critical machines, end users have developed condition monitoring applications when this service is not available from the OEM. Both types of users of IIoT solutions should consider edge computing to make their solution simpler (data pre-processing at the edge) and more robust (no single point of failure).
