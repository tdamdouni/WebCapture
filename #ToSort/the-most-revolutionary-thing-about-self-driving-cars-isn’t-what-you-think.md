# The Most Revolutionary Thing About Self-Driving Cars Isn’t What You Think

_Captured: 2017-07-10 at 17:20 from [dzone.com](https://dzone.com/articles/the-most-revolutionary-thing-about-self-driving-ca?oid=twitter&utm_content=buffer3c790&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The [hype around autonomous vehicles](https://mesosphere.com/blog/2017/06/19/the-most-revolutionary-thing-about-self-driving-cars-isn-t-what-you-think/) has reached a fever pitch, with most people focused on the immediate innovation and novelty of driverless cars.

Headlines in leading publications reinforce the hype: "[Driverless cars inspire a new gold rush in California](https://www.ft.com/content/c124465c-3ed7-11e7-82b6-896b95f30f58)."

The potential has been reinforced by Intel recently spending $15 billion to buy Mobileye, which makes self-driving sensors and software. As this purchase highlights, and what many have yet to grasp, is that the true transformation isn't the car, but the underlying digital technology.

Following the gold rush analogy, the real work is being done by those wielding the picks and shovels. Consider laser-based lidar (light detection and ranging) technology. Lidar sensors send out a pulse of light and measure the reflective return to determine the distance between objects, generating a precise 3D map of the car's surroundings.

## Data by the Terabyte

These sensors and other necessary systems such as GPS lead to estimates that each autonomous vehicle will generate and consume roughly four terabytes of data for every eight hours of driving.

Four terabytes is the amount of data it takes to store over 1.2 million photos -- in other words, a huge amount of data!

And much of that four terabytes will need to be acted upon very quickly.

At 65 miles per hour, the one-second latency we might find acceptable in our favorite app could mean the difference between a car detecting and reacting to an object in time or being in a deadly accident.

The ability to respond in near real-time requires massive amounts of computing power available in close proximity to each car.

## CPUs on Board

In many ways, cars are becoming big computers on wheels. How big? Already today, the average car can have between 25 and 50 central processing units (CPUs), even without autonomous driving, controlling blind-spot and pedestrian collision warnings, automated breaking and maintaining a safe-distance via smart cruise control, and many others.

Many of these CPUs are networked, communicating with each other via an [onboard network](https://en.wikipedia.org/wiki/CAN_bus).

In effect, each self-driving car is becoming its own powerful data center.

According to a [report](http://news.ihsmarkit.com/press-release/automotive/autonomous-vehicle-sales-set-reach-21-million-globally-2035-ihs-says) from IHS Automotive, the number of self-driving vehicles on roads worldwide is expected to grow to 21 million by 2035.

![Autonomous Car Sales by 2035](https://mesosphere.com/wp-content/uploads/2017/06/AutonomousCareSales.png)

The amount of data being generated and managed for 21 million vehicles is staggering. Even with networking advances such as 5G to transmit data from each car to the cloud and back, it's difficult to fathom how this much information can be quickly analyzed, at least with current and near-horizon technologies.

## Moving to the Edge

Add in other modes of transportation such as airplanes, ships, and any number of increasingly smart objects like wind turbines or smart houses and one can catch a glimpse of the enormous amount of information that will need to be processed.

To accommodate this huge amount of data, many companies today are moving their computing into the cloud, but ironically the future will [increasingly be on the edge](http://a16z.com/2016/12/16/the-end-of-cloud-computing/).

The goal with edge computing is to act on data quickly without the latency incurred by transmitting across a wide area network.

For an autonomous car, data that needs to be acted upon locally -- for example, responding to an encroaching vehicle -- will be processed at the source.

Other data where latency is less of an issue, perhaps the road and weather conditions at a location or crowd-sourced data, such as the Waze traffic awareness app, can be pushed to the cloud.

Coordinating the computing and communications between self-driving cars and other edge elements will increase the need for hybrid and private clouds, and coordination between and across them, requiring a great deal of automation.

## Open Source Opportunity

Fortunately, a handful of companies has been preparing for this eventuality.

Google, for example, uses nearly a million servers in its daily operations. To manage this enormous complexity, the company created its own software known as "Borg."

Borg has served as an inspiration for another computing management system: the open source Mesos platform. Mesos is now used by many leading companies including Twitter, Verizon, and Bloomberg.

These are big names, but more importantly, because this is open source software, what used to just be the realm of the most innovative software companies is now readily accessible to anyone - providing companies of all sizes the opportunity to build the next world-changing innovation.

These next generation platforms can manage huge, distributed data centers and clouds, and can be extended to include objects at the edge.

## Dynamic Capabilities

What's more, these systems also improve the efficiency of all the computers under management by dynamically allocating capability when needed, thus improving utilization.

While hardware was once more capable than software, that dynamic has changed.

Distributed computing platforms like Borg and Mesos enable far greater capacity and application diversity than would otherwise be possible.

Harnessing available computing resources to their fullest -- whether in smartphones, PCs, servers, and soon in self-driving cars -- will not only improve productivity but will open new possibilities.

For example, applying computing resources for greater social good, like what is done with the search for extraterrestrial intelligence (SETI).

Based at UC Berkeley, SETI uses Internet-connected computers, including many home-based PCs to help analyze radio telescope data.

## Clouds Everywhere

Imagine the applications that could be designed using advanced computing management platforms.

Imagine, too, a world where there are clouds everywhere; where the devices we use are not just networked but share the burden of huge volumes of data and instantaneous decisions; where software is seamlessly managed across infrastructure wherever in the world it resides; and where these technologies are available as open source to any company.

That's a truly exciting wave of innovation.

The advent of self-driving cars will force many changes in how computing and communications systems are architected, both through hardware and software. It's these advances in data management, combined with edge computing that will enable driverless cars, smart cities and homes, and other connected technologies.

These foundational information technology elements enable the Fourth Industrial Revolution by laying the groundwork for breakthroughs in [artificial intelligence](https://en.wikipedia.org/wiki/Artificial_intelligence), [robotics](https://en.wikipedia.org/wiki/Robotics), the [Internet of Things](https://en.wikipedia.org/wiki/Internet_of_things), [autonomous vehicles](https://en.wikipedia.org/wiki/Vehicular_automation), [3D printing](https://en.wikipedia.org/wiki/3D_printing), [nanotechnology](https://en.wikipedia.org/wiki/Nanotechnology), and other emerging technologies.

Learn more about the [2017 Technology Pioneers](http://widgets.weforum.org/techpioneers-2017/).
