# The 5 Domain Experts You Need to Build an IoT Device

_Captured: 2018-04-11 at 16:46 from [dzone.com](https://dzone.com/articles/the-5-domain-experts-you-need-to-build-an-iot-device?edition=372193&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-04-11)_

According to a [Cisco survey](https://www.slideshare.net/CiscoBusinessInsights/journey-to-iot-value-76163389) (2017), over 60% of respondents admitted that they substantially underestimated the complexities of managing their own IoT initiatives. Even more alarming, the same survey also found that 75% of self-initiated IoT projects were considered a failure.

![](https://cdn-images-1.medium.com/max/800/1*H89FfPD212_m7W7EOo_SpQ.png)

However, [Cisco](https://newsroom.cisco.com/press-release-content?articleId=1847422) also found that most companies that consult IoT domain experts throughout the project's lifecycle finish on time. Companies that go it alone often exceed their initial timelines and find that they lack the internal expertise to keep the project up and running. Unfortunately, by the time companies realize that they need additional expertise, they are usually deep into the development process, making pivoting exponentially more costly.

The purpose of this guide is to help you assess the domain experts you need to build an IoT device and prevent you from getting stuck in the product development process. This guide also explains and defines many aspects of the IoT product development cycle to help you overcome the many complexities of building an IoT device at scale.

![Image title](https://dzone.com/storage/temp/8696034-domain-experts-copy.png)

## The Five Domain Experts

### 1\. Embedded Firmware Expertise

Firmware engineers develop and implement the reprogrammable content (firmware) that runs on electronic devices. You can think of firmware as the operating system (OS) that allows embedded devices to perform its basic functions. Firmware is usually written for special processors and objects that don't have obvious computer interfaces. When looking to scale your IoT device commercially, you need an embedded firmware engineer who is an expert at:

  * **Building a stable firmware architecture** that is scalable and well documented, using professional firmware toolchains and firmware languages like C and C++.
  * **Designing for constrained systems** like low-power MCUs with limited memory, no memory management, and no direct interfaces like keyboards or screens.
  * **Designing for stability and error recovery** including application watchdog timers, error correction, and auto-recovery from system faults.
  * **Paying special attention to inputs and outputs -- **this includes sensor data gathering, digital signal processing, local compression, and storage of data.
  * **Minimizing power consumption** by writing firmware that allows the device to enter sleep modes and consume the bare minimum energy required.
  * **Optimizing bandwidth** for cellular communication from your device to the cloud.
  * **Revising firmware continuously **with [OTA firmware updates](https://blog.particle.io/2017/12/18/over-the-air-firmware-the-critical-driver-of-iot-success-859927/) to improve stability and functionality of your fleet (this adds value without needing to change hardware).

While this is not a comprehensive list, the important point is that any embedded firmware expert you want on your team should be able to do these things at the minimum. If you're interested in learning more about designing for constrained systems, check out this white paper on [power management for the internet of things](https://www.particle.io/resources/IoT-Insights).

### 2\. Electrical Engineering Expertise

Electrical engineers design, develop, test and supervise the manufacturing of electrical equipment. They are experts at DFM (design for manufacturing) best practices and can help you design a prototype PCB with the best-performing and least expensive components. When examining electrical engineering expertise, look for someone who is an expert at:

  * **Designing, developing, and testing** printed circuit boards (PCBs, which function as the brain and sensor interface for your IoT device).
  * **Selecting and designing the right hardware components** that improve accuracy and stability, but also keeping costs in mind.
  * **Identifying potential design problems** by iteratively testing hardware designs on the bench and in the field. Doing so will allow electrical engineers to improve component selection and circuit designs based on real-world inputs.
  * **Using industry-standard electronic design automation** (EDA) tools like Altium and Eagle for PCB design. Experts can leverage built-in debugging and design practice features so coworkers and partners can understand and collaborate on the design.
  * **Optimizing, generating, and extending **battery life for IoT devices on the move or deployed in remote locations.
  * **Implementing antennas and designing for RF protocols **without impacting the connectivity of the product. IoT devices are often deployed in harsh RF environments so the antennas also need to be stable enough to sustain these conditions.
  * **Designing IoT devices for certification** (FCC, EMC, UL, ETL, CE, and more) so that your customers can buy and use your products with confidence.

Overall, electrical engineers need to stay updated on changing technologies in the wireless arena. If you're interested in learning more about the PCB design process, check out this article about [building your first PCB prototype](https://blog.particle.io/2018/03/06/proto-to-prod/).

![](https://cdn-images-1.medium.com/max/800/0*oPSyCeaJH-8zq6lb.)

### 3\. Mechanical Engineering Expertise

Your mechanical engineer is responsible for the physical functioning of your device in the world, in terms of how it interfaces with other mechanical systems and, potentially, human users. Mechanical engineers need to be experts at:

  * **Prototyping and designing enclosures **that fit the product's specifications and will be robust enough to survive for years.
  * **Assembling cables and wires **that have the correct connectors to interface with other systems and can transmit signals according to mechanical and electrical requirements
  * **Implementing switches**, relays, triggers, and other mechanical interfaces so your IoT device can trigger physical events (like opening a water valve or automatically braking a moving wheel).
  * **Designing products that can sustain environmental challenges**: water ingress, weather changes, temperature changes, vibration, pressure, shock, and more.
  * **Designing for ease of installation **and ease of maintenance.
  * **Overseeing operations** at mechanical facilities so your product can be supported at the lowest possible cost during manufacturing and out in the field.
  * **Design for manufacturing practices **so the finished IoT device will have the minimum necessary parts, and can be assembled in the factory using the minimum steps necessary, which translates to cost and time savings.

### 4\. Manufacturing Expertise

When deploying an IoT device to market, you need a manufacturing manager who can help you source and find ways to reduce hardware costs easily. They need to be experts at:

  * **Monitoring manufacturers' partners** to ensure they comply with project requirements (like cost and safety regulations).
  * **Project management techniques** so they can plan, design, and ramp up mass production of a project from beginning to end (i.e. CM selection and CM management).
  * **Sourcing authentic hardware** components (vs gray market or 'pirated' parts), while negotiating for the lowest possible costs.
  * **Ensuring lead times **are met in time for production and finding ways to source components at negotiated costs.
  * **Creating and managing the Bill of Materials **(BoM) which is the master list of every single component that must go into the finished product. (The BoM is the output of the hardware sourcing that is mentioned above. The BoM must align with DFM practices).
  * **Supply chain management**, which is the flow of goods and services. They need to be experts at tracking serial numbers, other IDs, and managing logistics (i.e. how will your finished product get from the factory floor, into warehouses, and into your customers' hands with the confidence that each IoT device is 100% trackable at every stage?)
  * **Regulatory and compliance** management, which means ensuring your IoT device can be legally shipped or stored in multiple markets.
  * **Liaising across countries, languages,** and timezones to coordinate operational teams and ensuring multiple stakeholders are informed and accountable.

### 5\. Manufacturing Testing Expertise

Manufacturing testing is different than manufacturing expertise because implementing quality testing metrics is a job within itself. Manufacturing testing experts need to be able to conduct and validate the following tests before an IoT device can be taken to market:

  * **Test Rig Development** -- You will need to _build a product to test your product_, which is known as the test rig. This rig interfaces with your IoT device directly on the assembly line and proves that all functions and interfaces behave as required.
  * **Test Script Development **-- This is the software that runs on your test rig and ensures that your product receives the correct device firmware. It also passes all provisioning information to supply chain management system.
  * **Provisioning coordination -- **This correlates with the manufacturing expert's tasks, which is to ensure that every device that is manufactured receives the correct serial number and is stored in the correct supply chain system.
  * **Environment and certification testing -- **Work with partners to ensure the finished device will meet legal requirements and potentially punishing, long-term environmental requirements (such as dropping the device onto concrete 100 times in 1 day).
  * **EVT (Engineering Validation Test)** -- This is the first wave of devices to come off of the manufacturing line (and before many of the final DFM steps are complete). It validates that your manufacturing process can implement core electronic and mechanical functions as required, but the IoT device itself will still not be ready to ship at this stage.
  * **DVT (Design Validation Test) **-- This is the 'fit and finish' test of your manufacturing process. It proves that all parts, including the enclosure and final cables/sensors/connectors, can be assembled properly. It also ensures that the IoT device has the correct look and feel needed for mass production. An IoT device that passes this test will _look_ ready to go, but it's not until PVT that you are ready to unleash the full-scale production.
  * **PVT (Production Validation Test)** -- This is the final mass production oversight test -- it validates that every single feature and function passes with flying colors, and that the IoT device is truly ready to manufacture at full scale. The first IoT device that passes PVT is the first _fully productized_ device that's ready to ship.
  * **Integration Testing** -- This test ensures that your IoT device tests positively on its own via the test rig and EVT/DVT/PVT manufacturing steps, but that it also tests positively when integrated in _your customer's_ end product.

Again, not a comprehensive list, but a short list of the major things you need to do when testing your IoT device.

### 6\. Everything Else

Of course, building a mass production IoT device requires a huge set of domain experts and specialized skills that go far beyond hardware and manufacturing. Here are some of the other skill sets to consider when building an IoT device for scale:

  * **Program management** -- Who will oversee the _entire_ project, covering all of the above as well as all of the below?
  * **Industrial design** -- This is especially important for consumer-facing products. This covers the look, feel, fit, and finish of a consumer product, including -- what color and texture, what type of material (plastic, metal, etc).
  * **Plastics tooling and molding** -- if plastic pieces are designed, how will they get made? This requires metal 'tools' to be carved out so that molten plastic can be injected, which is a project in itself.
  * **Software/cloud/mobile** -- How will you gather and display business intelligence about your IoT devices, either individually for insights or at massive scale? How will admins, technicians, and end users interact with these devices?
  * **UI/UX** -- If you design and build any software interfaces, how will users interact with those endpoints? Whether web or mobile?
  * **Data science** -- as your fleets grow to massive scale, how will you 'make sense' of the growing mountain of data to draw actionable insights for your business and your customers?
  * **Marketing** -- How are you going to let the world know about your amazing IoT device?

### The Bottom Line

Well, this is a lot of work. The purpose of this article isn't to make you feel discouraged though. Realistically, taking the time to scope and comprehend these requirements will save you time and lots of money down the road.

First, you should assess these requirements with own your organization's skill sets, experts, and resources. By doing so, you'll be able to increase your own knowledge on the gaps in your organization and be able to properly educate stakeholders on how to build a production IoT device. It's also worth mentioning that there are many engineering services that can provide you the domain experts and skill sets you need to build your IoT device from prototype to production.

In the end, it is important to remember that building a successful IoT device (or any type of product) is very hard. But you know this going into the project, so don't make it harder than it needs to be. By hiring or consulting these domain experts, you can substantially increase your chances of finishing your project on time and successfully launching an IoT product to market.
