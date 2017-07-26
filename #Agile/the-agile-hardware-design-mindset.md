# The Agile Hardware Design Mindset.

_Captured: 2017-03-08 at 09:17 from [www.innovel.net](http://www.innovel.net/agile-hardware-design-mindset/?utm_content=buffer454de&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Moving to Agile development in hardware is more about mindset than it is about technological limitations. Let's consider some of the limitations that are often used to resist Agile hardware development, and show how these limitations are more to do with thinking then with technology.

**PCB board design and layout.  
**  
We can't do Agile because we need to complete the full board design before sending the design for PCB fabrication and population of parts. Manufacturing is costly and takes a lot of time, so we want to minimize these costs.

Let's examine each of these points:

**Myth: Manufacturing a PCB takes a lot of time.  
**

![](http://www.innovel.net/wp-content/uploads/2014/03/automatedopticalinspection-300x188.jpg)

Facts: The last 30 years of continuous high speed innovation in PC motherboards and mobile phones has driven the PCB manufacturing business to be very quick and responsive. A five minute search for fast turnaround PCB manufacturers revealed many companies that can turn an 8 layer PCB in 24 hours. With overnight shipping, you can have your PCB in 2 days. If you plan ahead with the manufacturer to get parts ordered so it can be populated, this can be done at the same time.

**Myth: Manufacturing a PCB is costly.  
**  
Facts: The costs for quick turn around PCBs are trivial when compared to the cost of an engineer waiting for hardware. You can calculate costs from a variety of quick turn manufacturers at <http://www.ladyada.net/library/pcb/costcalc.html> For a 3″x5″ PCB the highest cost for a 2 day turn around was $215, shipping included. For comparison, that average loaded cost of an engineer to their employer is (salary, benefits, office, etc.) is $80-200 per hour. An engineer who spends one day waiting for hardware is far more expensive then the fastest most expensive quick turn PCB manufacturer.

**Myth: We need to complete the full design.  
**

![](http://www.innovel.net/wp-content/uploads/2014/02/lart-jtag-1-150x150.jpg)

Facts: A well designed PCB is modular, with modules for CPU, memory, I/O, RF, etc. Each module is designed as a unit, with interfaces to other modules, just like software. Therefore we can design a module, or part of a module, and that completed design can be treated as a testable deliverable. For example, the CPU and the memory could be designed and shipped as a populated PCB ready for developers to start using. The developers can start to use that platform for coding while the hardware designers work on the next module. The hardware designers will need to implement some features, like a JTAG or USB port and terminate some pins so developers can use the PCB, but that is a small price to pay in exchange for getting hardware into the hands of the software developers.

**Deploying iterative and Incremental hardware development.  
**

![](http://www.innovel.net/wp-content/uploads/2014/03/stacked-PCBs.jpg)

> _[stacked PCBs](http://www.innovel.net/wp-content/uploads/2014/03/stacked-PCBs.jpg)_

If we change how we think of hardware from being a single physical device that has to be designed, to a set of functional modules that are deployed as hardware, then we can map the manufacturing process of PCBs to the deployment of code into production. If we can deploy functional modules into a physical device (PCB+parts) in a few days, then we can deliver hardware functionality using an iterative and incremental approach. For example we could deploy a PCB with a basic input output (I/O) circuit that meets our simplest design criteria. This circuit would be deployed into hardware and then could be used by developers for coding and testers. If it is determined from programming and testing that the simple I/O design needs changes, a revision of the I/O could be completed to make the desired improvements. This ensures that the designers are delivering a design that meets the needs of the developers and testers. Once the developers and testers were satisfied, the I/O could be evaluated by the customer to gain their feedback and ensure it meets their needs.

**Iterative and Incremental firmware with the hardware.  
**  
If hardware is thought of as deployed functional modules, then firmware is the glue that enables these modules to provide customer value. Firmware engineers have numerous well understood options for software development when there is no hardware. Software simulators, emulators, evaluation boards, and FPGAs all provide different options. With every design there are business priorities and technical risks. Based on these risks and priorities the developers need to figure out how to slice the design into components of firmware and hardware that will deliver the most business value and risk reduction with each iteration. For example if I/O is risky then the hardware and firmware developers should figure out how to build, code and test the I/O module before the CPU module. For example this could be accomplished using an I/O PCB that interfaces to a CPU evaluation board.

**Using business value to drive product design.  
**  
We are faced with the continual expansion of software into the hardware space. Shrinking device sizes, massive gate arrays, generic open source platforms like Arduino, and smart phones all are changing the hardware development game. However software will always need something to run on, and as more devices connect to the internet, the importance of real world interfaces will continue to expand. Great hardware developers like Hewlett and Packard always emphasized getting out of the lab and meeting your customers. As hardware is increasingly used to wire up the connected world, it is more important than ever that hardware designers find ways to quickly respond to the changing needs of their customers. Agile principles and values provide good ideas to help you get there… just replace the word software with firmware or hardware :).

![PCB Art by Artist Steven Rodrig](http://www.innovel.net/wp-content/uploads/2014/03/PCBArtbyArtistStevenRodrig.jpg)

> _Artwork "Post Apocalyptic Data Hunter: RONIX" by Steven Rodig at PCBCreations.com_
