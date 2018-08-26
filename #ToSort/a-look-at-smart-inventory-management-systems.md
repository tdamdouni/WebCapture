# A Look at Smart Inventory Management Systems

_Captured: 2018-03-07 at 15:29 from [dzone.com](https://dzone.com/articles/a-look-at-smart-inventory-management-systems?edition=366204&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-03-07)_

RFID (Radio Frequency Identification) technology is fast replacing obsolete ways and technologies of [asset tracking and inventory management.](https://www.peerbits.com/blog/how-can-beacons-help-asset-tracking-and-management.html) By tradition, asset tracking and inventory management in retail supply chains depended on these old-school methods:

  * Accounting Tools and Systems: Individual details of each item in an inventory are manually entered into a spreadsheet (e.g. Microsoft Excel)
  * Manual Systems: A person literally sits down in front every entry/exit point and writes down details of each item of an inventory on a piece of paper.

These old-school methods are the reason behind many prevailing problems, which augment as the size of the inventory increases, and the abovementioned methods stop working.

![Inventory-Management-main](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/Inventory-Management-main.jpg)

  * **Inconsistency in data entered:** Missing, wrong, or duplicate data
  * **High cost of staff training:** Training staff, depending upon the size of your inventory, can take anywhere between a few weeks to a few months.
  * **System is prone to human errors:** Without validation of any sort, such methods of asset tracking may lead to blunders and revenue loss
  * **Lack of a central customer database:** Inventory managers will have a hard time getting hands on the latest inventory information owing to a lack of a central database.
  * **Lack of security:** We all know the sort of security data written on pieces of paper and spreadsheets draw. A person just needs a phone with a camera or a thumb-drive to make copies.
  * **Slows down the operation:** A person manually entering data is much slower than an automated system that updates the database itself.
  * **Hidden Costs:** The old-school method will make you lose money owing to mistakes, typos, duplication, and slow operations.

Modern asset tracking requires the employment of the latest technology. For large inventories, paper-based and spreadsheet tracking and management systems are out of the question. In addition to RFID, barcode scanning is also used for asset tracking.

## RFID vs. Barcode

Manual scanning, wherein a person manually scans bar codes printed on each item at every strategic point, brought in some sort of automation to the process, but it has its own set of shortcomings against RFID.

Thus, although the barcode has been around for quite some time in the market, the focus is shifting fast towards RFID-based solutions since they have various advantages over traditional barcode-based solutions:

![RFID VS BARCODS](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/RFID-VS-BARCODS.jpg)

Not that it's clear that RFID is the best method of asset tracking. Let me introduce you to RFID and how it works. For a clear understanding, I'll use an example.

## Thorpe Pharma's Dilemma

Thorpe Pharma is a manufacturer of biotechnology and pharmaceutical equipment. Each manufactured unit costs several hundred thousand dollars and is made of high-precision components. Each component has a unique ID attached to it so to a manufactured unit.

The components are manufactured at various shops in the factory. From there, they are moved to the assembly department to assemble the final equipment. An assembled unit undergoes various quality checks before being packed in crates and moved to the shipping department.

Thorpe's customers call the service desk to lodge a complaint in case the equipment malfunctions. This could be a defect, component failure, or gaps in assembling. Whatever, the support person must diagnose the problem and assign a Service Engineer to it.

The components are ultra-sensitive and can't be commonly fixed at the customer's place. Thus, the service engineer replaces the malfunctioning component right at the site.

That is, components are always moving department to department and, as in the above case, equipment to equipment. As such, the managers, service engineers, and the sales force of the company must know the status of the components.

The service engineers must learn when a component arrives or moves out. Moreover, the engineers must be able to track a component from the day it was manufactured.

## A Barcode-Based Solution

Thorpe employed barcode technology to track the movement of components. However, with so many components on the move, tracking the valuable inventory and the moving assets was a nightmare for Thorpe's management. We developed a complete solution for asset tracking, inventory management, and [fleet management](https://www.peerbits.com/blog/significance-fleet-management-solution-for-logistics-industry.html) using RFID technology for the company.

A unique item identification number is printed on an adhesive sticker and pasted on each component -- and the assembled unit. At every strategic point, Thorpe personnel scan the bar-code with a barcode scanner. The scanned data reaches a program that processes and records them in a relational database table.

## How RFID Technology Works

In RFID-based asset tracking and management solutions, any asset to be tracked is fitted with an RFID tag. RFID tags, in their thin, microchip-like structure, sandwich an electronic radio transmitter, an antenna, and a tiny battery.

![tag-layer-main-component](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/tag-layer-main-component.jpg)

Like barcodes, with the help of a little adhesive, they can be stuck to any surface. They can also be attached to identity cards, people, and even farm animals. Each RFID tag has a unique identification number (UIN) attached to it. It sends out a radio signal carrying the UIN. Thus, a receiver device, called the RFID reader/scanner, extracts the UIN of every tag in its range and updates to a database.

## Types of RFID Tags and Readers Available in the Market

There are many types of RFID tags and reader available in the market. While tags cost anywhere between $1-$20, RFID readers can go as much as $3,000 and $10,000-20,000 per portal for hardware, installation, and configuration of Fixed Position passive RFID solutions.

**For tags:**

  * Basic passive RFID: 10 cents USD each - Good for paper or other non-metal, liquid material. Will not work for IT or metal assets
  * Metal passive RFID: $1 USD each - Larger passive tags that work on metal surfaces. Required for servers or metal equipment, especially in a data center
  * Active RFID: $15-$20 USD each - Powered RFID tags that emit a signal every 30 seconds. Active RFID is fully automated and highly accurate. No human involvement is required and has nearly 100% read rates. Gives immediate notification as things move around or disappear

**For readers:**

  * Handheld - Passive RFID handheld readers. A human being waves the scanner near assets. Great for manual auditing of a location, data center rack, etc. About $3,000 each.
  * Fixed Position passive RFID - Portal readers installed in a doorway that detect assets moving through. Figure on $10,000-20,000 per portal for hardware, installation, and configuration
  * Active RFID readers -- Zonal readers that cover about 3,000 square feet and detect active RFID tags in their zone. Fully automated, notifying administrators and updating the database in real time. Figure on $1,250-$1,500 each.
  * Active RFID Rack/Room Locators -- These work in conjunction with Active RFID readers to report the precise rack or room location of the active RFID-tagged asset. Figure on $150-$200 each.

## Communication Protocol and the Technology Stack

The ability to scan and read from different angles and through a certain material, resistance against harsh conditions, and robustness has put RFID among the best methods to [transform fleet management systems.](https://www.peerbits.com/blog/gps-vehicle-tracking-can-transform-fleet-management.html)

**RFID supports two ways of communication protocols to facilitate tags and the reader work in liaison.**

### **1.TTF Protocol**

Tag the communication as soon as it detects the reader field. It will simplify the tag logic, but it is less secure because the tag doesn't care what it is communicating with as long as sufficient field strength is available.

### **2\. ITF Protocol**

This tag waits for interrogation by a reader before transmitting information.

Security-wise it is good so it is recommended for our smart inventory management system.

### **Technology Stack**

Creating a program to interact with readers: Java, phpMyAdmin, and SQL.

Creating appropriate database schema so that all required information can be determined: History, times, current tags, past tags, etc.

### **Tag List and Reservation System Considerations**

  * Truncate table?

  * BST?

  * Appropriate DB vs. software workload sharing

  * Appropriate queries

## System Architecture of RFID Subsystem

Modern asset tracking and inventory management solutions rely on an RFID subsystem of a logistics mobility solution that supports a number of application domains. Various software components working in unison to extract and process information, including UIN, from RFID tags form an inventory management solution.

In a typical enterprise setup, various RFID readers are placed inside warehouses, transports, and strategic points. Data captured by the readers is processed by the host computer before sending it to database storage.

The database storage is, on the other hand, connected to the RFID application, which includes an entity framework and RFID reader API. The host computer can process data from various readers at the same time. It processes the information and buffers them for a predefined time period.

## Middleware Architecture and the Database

The Asset Tracking and Inventory Management (ATIM) solution has a SQL Server database as its backend. The ATIM is accessed through a web interface that can be deployed on the Intranet server of the enterprise, a virtual wide area network (WAN) -- or it can be IP-based.

An operator can interact with the interface using a web browser (Chrome, Firefox, etc.) on their computer, tablet, or smartphone. The web app can also be packed to create an Android and iOS app.

To integrate the RFID information and the ATIM solution, a middleware implementation is required.

![Middleware-Architecture](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/Middleware-Architecture.jpg)

The middleware implementation coordinates between the ATIM database and the RFID subsystem database. Moreover, it updates the movement history of each component in the ATIM database, sending out notifications to personnel on their smartphones.

## The Asset Tracking and Inventory Management (ATIM) Solution

In RFID-based ATIM solutions, each tag is authorized by means of a desktop reader. The authorization tells the solution that this tag is now a part of the inventory and must be tracked at each level. The tag is then attached to the package to be tracked. The packages are packed inside crates. The integrated reader scans packages before they are picked up by forklifts and placed in a warehouse.

![RFID-wearhouse-system](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/RFID-wearhouse-system.jpg)

A person carrying an RFID reader scans the entire warehouse for tags. If the warehouse management system detects a missing RFID tag, it reports to the ATIM quality operator to look into it. If the inventory doesn't report any missing package, the crates are forklifted again and unloaded to a truck for transportation.

![architecture-of-rfid-tags](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/architecture-of-rfid-tags.jpg)

An RFID reader placed at the unloading points assure no package goes inside the truck without being tracked by the reader. Again, the data is validated against the tags authorized by the desktop reader.

The illustration below shows a modern retail implementation using RFID -- dubbed RFID Retail 3.0.

![RFID-retails](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/RFID-retails.jpg)

## Areas of Application of RFID Technology

The key application area of RFID tracking is in the manufacturing, service, and retail chains. However, it can be used in many other places. Academically speaking, RFID tracking can be used anywhere something needs to be tracked. Some of the application are:

  * In healthcare, hospital staff can track patients' health by having them wear RFID-enabled wristbands. Doctors and nursing staff can check detailed information of the patient on their handheld computers.
  * In large farms, dairies etc., RFID tags can track cattle count. Active RFID tags in the form of ear tags are both cheap and light.
  * RFID tracking can be used to track employees' movement in and out of the workplace
  * In the hospitality industry, access to a room can be controlled by an RFID tag.
  * In cells, RFID tracking can monitor activities of inmates, which will ease the job of security personnel.
  * In aviation, RFID technology can track baggage with precision.
  * In transportation, RFID tags can be attached to VIP vehicles: police patrol teams, ambulances, fire brigades, etc. When they arrive, a red signal turns to green to let them pass and reverts as soon as they pass.
  * RFID tags can detect empty parking spaces in a parking lot.

## Return on Investment (RoI)

The ROI of RFID depends on your labor costs and the value of real-time data accuracy. If you don't need real-time data and labor is cheap, use passive RFID and handhelds. If labor is expensive and real-time data is critical, invest in active RFID.

So, each organization has a unique profile of asset receiving, distribution, and volume. And, of course, there is always the issue of capital expenditures.
