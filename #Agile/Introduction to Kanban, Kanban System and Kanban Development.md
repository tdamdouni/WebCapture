# Introduction to Kanban, Kanban System and Kanban Development

_Captured: 2016-10-31 at 12:57 from [managementyogi.blogspot.de](https://managementyogi.blogspot.de/2016/10/Introduction-to-Kanban-Kanban-System-and-Kanban-Development.html?m=1)_

**I**magine this situation: You have food items in your refrigerator. Some of them are running out. You figure out what items you need — when and in what quantity — and put sticky notes on the door of the refrigerator. Let’s call those “withdrawal cards.” As one of the items is running out, you pull off a withdrawal card and go to the nearest supermarket to replenish those items.  

![](https://2.bp.blogspot.com/-6_bVq4Y8YzI/V_ynZSOveOI/AAAAAAAAB9k/Y1xGrc81nqQdn77RZdx4avk7ZHgWVgk6QCPcB/s280/Refri.png)

  
The supermarket manager also has a similar card system, which signals that
those items are being emptied from its shelves. Let us call the cards used by
the supermarket “production cards.” As the items fall below a certain limit
due to withdrawals by customers like you, the store manager informs the
supplier by this card. The supplier can check the production card sent,
produces the quantity mentioned on the card, and has those items replenished
in the supermarket.  
  
If any other food item in your refrigerator is running out, you pull off
another sticky note and follow the same process. The supermarket does the same
with its production cards, and the supplier follows up.  
  
Congratulations! With the help of signaling cards — sticky notes and
production cards — you have just experienced “Kanban” and the “pull system.”  
  
Concepts on Kanban and Kanban development are important to understand if you
plan to prepare for the **[Project Management Institute’s Agile Certified
Practitioner](https://www.pmi.org/certifications/types/agile-acp)**
credential. Also, in the recently updated exam for the Project Management
Professional Kanban has been introduced as one of the knowledge and skills in
its exam content outline.  
  
**What is Kanban?**  
  
Kanban is a Japanese word for signal card, signboard, visible card or
instruction card. Kanban signals are typically physical in nature, such as
containers or cards, but they can take the form of a fax (“faxban”) or an
email or even something web-based (“e-kanban). Kanban was first used by
Taiichi Ohno on the factory floors of Toyota Motors. The Kanban system — so
called because it uses Kanban – later became an integral part of Toyota
Production System (TPS)1.  
  
In our example, we have two signaling cards — the withdrawal card (the sticky
note) and the production card. Because they act as signals for us, let’s refer
to those signal cards as “withdrawal Kanban” and “production Kanban.”  
**_  
_** **_Why would you and the supermarket use Kanban?_**  
  
Kanban is used to reduce waste. Waste (called “Muda” in TPS) surfaces in
several parts of the production process: overproduction, waiting, defects etc.
However, one of the major sources of waste is overproduction, which happens
when we produce more than what is needed or before it is needed. Kanban stops
this waste, because the system is based on a pull system and has a just-in-
time (JIT) approach.  
  
Consider the typical “push” scheduling system. In this approach goods
(inventory) will be pushed into the supermarket by the suppliers whether they
can sell it or not. This leads to waste. If you’re using a push system in your
home, you would stuff the refrigerator with food items (again inventory)
whether you immediately need them or not. Sometimes, you may end up not even
using those items, because you end up going out or leaving town or forgetting
you have them.  
  
**Just in Time and the Pull System**  
  
In a pull system, unlike the push system, you (the “downstream” process) buy
the items from the supermarket (the “upstream” process) based on a signal card
— those sticky notes on the fridge. This we have named “withdrawal Kanban.”
This approach is just in time because you’re getting the items as and when you
need them and in the quantity that you need. It’s also a pull system, because
you’re pulling the items from the supermarket as and when you need them.
They’re not pushed to you from an upstream process.  
  
Similarly, the supermarket (now acting as a downstream process) fills up on
items given by the supplier (the upstream process) only when you and other
customers have pulled the items from the supermarket’s shelves. The signal to
produce is triggered by another signal card, the production card or production
Kanban. The complete workflow for these steps is shown in this figure.2  
  

![](https://4.bp.blogspot.com/-Q3vd2qNiJx8/V_ynptX8cUI/AAAAAAAAB9k/HQNKRL7g8x8eSB6KkPn4IfWIeNz9Ql2WgCPcB/s280/2%2BCard%2BScheduling%2BSystem.png)

  
This two card scheduling system is the Kanban system in its most basic form.
The cards used in the system act as the signals and hence are known as Kanban
cards (or simply Kanban).  
  
A Kanban is literally attached to storage or a container and comes in the form
of laminated plastic card. If the card is attached to the container and sent
from a downstream center to an upstream center, then the upstream center will
fill up the items in the Kanban tray (the tray to which Kanban is attached).
Then it will send the tray to the downstream center. However, if an empty tray
is coming without any Kanban, then the upstream center doesn’t send the filled
up tray back.  
  
The two card just-in-time/pull system with Kanban cards can be scaled to
include other upstream processes, as shown below. Here again the downstream
processes are pulling work items as and when needed (just in time) and the
upstream processes are replenishing the items. This is also known as the
“Pull-Replenish-Pull” system or “Replenish-Pull-Replenish” system.  

  

![](https://4.bp.blogspot.com/-w8TU7f2UAfY/V_yn1ysIZYI/AAAAAAAAB9k/HzeG1F5HhJk0BeVvc_mlATCxZPXeJ7JVgCPcB/s280/Multi-Pull.png)

  
Here we have put pull systems between processes (or work flow states) to give
correct production instruction to the upstream process. Still in this system,
some waste will be there — simply because certain inventory lies in the
supermarket, which is inevitable. The ideal condition would be to have a
continuous flow. That’s what is strived for in Kanban systems: “Flow where you
can; pull where you must,” as Jeffrey Liker eloquently expressed it in his
book, The _Toyota Way: 14 Management Principles from the World’s Greatest
Manufacturer_.  
  
The key takeaway here is that we visualize the work and work flow with the
help of Kanban. Remember that a Kanban card is attached to a tray (or bin of
parts) to move. Hence, primarily it is about visualization and taking action
based on that.  
  
**Work in Progress**  
  
The number of Kanban cards tells the amount of items that are being worked
upon — work in progress (WIP). Why? Because Kanban cards are physically
attached to the Kanban tray; hence, they’re fixed in number or limited. By
limiting the Kanban cards, we limit the work in progress and minimize
overproduction and also minimize waste. Limiting work in progress, along with
the pull system, also forces us to focus on the items needed by the customer
and work only on them.  
  
**Managing the Flow**  
  
It’s possible that in the Kanban system there will be “work states,” when work
items are being developed or processed, and “wait states,” when the system is
idle. For example, when the Kanban tray is moving with an attached Kanban
card, it’s in a work state. But when the food items are lying in the
supermarket without being used by customers, they’re in a wait state.  
  
By managing flow, we manage the work states and wait states and also find out
if there are any bottlenecks in the system. This leads to continuous process
improvement, called “Kaizen” in TPS.  
  
So, here are the key characteristics of a Kanban system:  
  

  * Just in time
  * Pull system
  * Visual management
  * Limited work in progress
  * Management of flow
  
Now, let’s cover how these can be applied in Kanban development for products,
including software products.  
  
**Kanban Development**  
  
Kanban development mainly revolves around a visual board. This board is
divided into various work flow states. These can be in a very simple form such
as “to do” “doing” and “done.”. Otherwise, we can have multiple work flow
states as they happen in software development: “analysis,” “design,”
“development,” “testing” and “deployment.”  
  
Also, in product development there can be many types of tasks or work items.
For example, in software development they might be: new requirement,
requirement change, critical issues, bugs, refactoring work, impediments,
blocking issues, or documentation work. Each can be represented with various
color codes or color coded spots on top of a plain card. You can also use
various shapes for the cards: triangular, slanted, diamond. Each card is a
Kanban card presented on the visual board. After all, visual management is one
of the key aspects of Kanban development.  
  
A sample visual board for Kanban development is shown below. I have kept it
simple with one-colored sticky note (yellow) to denote one type of Kanban card
depicting a particular type of work item. There are three work flow states —
“TODO,” “DOING” and “DONE.”  
  
  

![](https://2.bp.blogspot.com/-kVdmUCvYwOw/V_yn9O71xYI/AAAAAAAAB9o/07hvc8mBB_MKYc6IhJF-HwrfCMF3vcIBwCPcB/s280/Visual%2BBoard%2B2.png)

  
The system shown above is pull, because the downstream process pulls the items
from the upstream process and starts working. For example, items under “TODO”
are pulled from the “Backlog of Items.” The work items are prioritized. This
system, as we have seen before, also minimizes waste. You may say this looks
very much like task boards used in other Agile development approaches.
However, there’s a distinction — the WIP limits. On top of every work flow
state, there’s a WIP limit, marked in the red boxes.  
  
How do you know what the WIP limit should be? Through experimentation. The
Kanban system itself doesn’t specify the limit; you have to figure out the
right WIP limit for your system’s workflow states.  
  
To manage the flow, you can add (or remove) wait states to the work flow
states. Remember the quote, “Flow where you can; pull where you must”? This
adds a certain amount of slack to the system, when continuous flow isn’t
sustainable. In the figure below, a wait state — “Analysis” — has been added
into the “TODO” workflow state to have some slack. From the “Selected” column
under the “TODO” workflow state again we have flow. Of course, you can strive
for continuous flow by removing unnecessary wait states.  
  
  

![](https://3.bp.blogspot.com/-ElVO1iigW58/V_yoDk50VkI/AAAAAAAAB9o/qbB0X74Xm3Y0gRGZ71i82j5htTC2bSgwACPcB/s280/Visual%2BBoard%2B3.png)

There you have it. The basics of Kanban, the Kanban system and Kanban
development. Now if you’ll excuse, I’m hungry. I need to go grab a withdrawal
card.  
  
_Notes_  
  
_1 The Birth of Lean: Conversations with Taiichi Ohno and other founders of
TPS, written by Koichi Shimokawa and Takahiro Fujimoto._  
_  
_ _2 Learning to See: Value stream mapping to add value and eliminate Muda,
written by Mike Rother and John Shook._  
  
This article was first published by [MPUG on 19th July,
2016](http://www.mpug.com/articles/introduction-to-kanban-kanban-system-and-
kanban-development/).

