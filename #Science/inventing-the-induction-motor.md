# Inventing The Induction Motor

_Captured: 2017-09-23 at 10:22 from [hackaday.com](https://hackaday.com/2017/09/21/inventing-the-induction-motor/)_

![](https://hackadaycom.files.wordpress.com/2017/09/inductionmotor.jpg?w=800)

When you think of who invented the [induction motor](https://en.wikipedia.org/wiki/Induction_motor), Nikola Tesla and Galileo Ferraris should come to mind. Though that could be a case of the squeaky wheel being the one that gets the grease. Those two were the ones who fought it out just when the infrastructure for these motors was being developed. Then again, Tesla played a huge part in inventing much of the technology behind that infrastructure.

Although they claimed to have invented it independently, nothing's ever invented in a vacuum, and there was an interesting progression of both little guys and giants that came before them; Charles Babbage was surprisingly one of those giants. So let's start at the beginning, and work our way to Tesla and Ferraris.

## Arago's rotations (1824-1831)

The induction motor's invention began in 1824 in Paris with the publication of a very simple series of observations by [François Arago](https://archive.org/stream/polyphaseelectri00thomuoft#page/68/mode/2up/search/arago). He suspended a magnetic compass needle laying horizontally in the middle of rings of different materials. He then rotated the needle 45° and let go of it. The needle proceeded to swing back and forth, with the maximum angle of its swing gradually decreasing. Arago counted the number of swings before the angle decreased to 10°. With a wooden ring, it took 145 swings, with a thin copper ring it took 66, and in a stout copper ring it took only 33 swings. The presence of the copper somehow dampened the oscillations of the needle.

![Babbage-Herschel experiment and eddy currents](https://hackadaycom.files.wordpress.com/2017/09/babbage_herschel_experiment_eddy_currents_an.png?w=800&h=794)

> _Babbage-Herschel experiment and eddy currents_

Others followed that lead and in 1825 [Charles Babbage](https://en.wikipedia.org/wiki/Charles_Babbage) and Charles Herschel demonstrated an experiment wherein they spun a magnet under a copper disk and caused the disk to spin briskly. They also cut slits radially in the disk and observed that this diminished the effect. Attempting to quantify the effect of the radial slits, they found that if they assigned a value of 100 to the rotary force of an unslit disk, then a disk with one slit had a value of 88, two was 77, four was 48 and eight was 24. Just as with Arago's compass needle, the magnetic object was again somehow interacting with the non-ferromagnetic material.

In 1831, Faraday did his own experiments and came up with the explanation for the effect that we still use today. Eddy currents were induced in the copper from the relative motion between the magnet and the copper disk. These eddy currents formed in such a way as to create magnetic fields of their own. The interaction of the two magnetic fields push or pull on the disk, making it rotate with the magnet or slowing down if the magnet isn't moving.

Many more experiments were performed between 1824 and 1831, as well as in the years following, however, they all involved rotating either the magnet or the copper disk. The next big step forward was to find a way to rotate the magnetic field without rotating either physical object.

## Walter Baily (1879)

![Baily's 1879 induction motor and sequence](https://hackadaycom.files.wordpress.com/2017/09/walter_bailys_1879_induction_motor_and_sequence.jpg)

> _Baily's 1879 induction motor and sequence_

On June 28, 1879, [Walter Baily](https://books.google.ca/books?id=85AOAAAAIAAJ&pg=PA286&lpg=PA286&redir_esc=y#v=onepage&q&f=false) demonstrated his own Arago's rotations experiment. In it, he replaced the permanent magnet with four electromagnets. But instead of rotating the electromagnets, their magnetic polarities were alternated electrically in order to create the rotating magnetic field. A hand cranked commutator fed by two batteries controlled the currents running through the electromagnets. Such a battery and commutator system meant that the currents going to the electromagnets were not sine waves, but rather closer to square waves, not ideal for smooth rotation.

The cycling of the magnets were as shown. The letters indicate the poles facing the disk, with O indicating when the electromagnet was off. The arrow shows the direction from north to south and can also be replaced by the copper disk, making clear how it would rotate. This is a lot like the [drive mode of a modern stepper motor](https://en.wikipedia.org/w/index.php?title=Stepper_motor#Half-stepping), but remember that instead of pulling against permanent magnets, the rotating magnetic field is pulling against the field caused by induced eddy currents.

And that brings us to the dawn of the modern induction motor and Galileo Ferraris.

## Galileo Ferraris (1885)

![Galileo Ferraris motors](https://hackadaycom.files.wordpress.com/2017/09/galileo_ferraris_motors_1885.jpg)

> _Galileo Ferraris motors_

In 1885, [Galileo Ferraris](https://en.wikipedia.org/wiki/Galileo_Ferraris) demonstrated an induction motor that also involved using two pairs of electromagnets to create a rotating magnetic field, though he did this independently of Baily. His motor more closely resembled modern ones in that the electromagnets surrounded a cylinder. More significantly, however, he proposed creating a true rotating magnetic field for it by supplying two sine wave alternating currents 90° apart. He gave his first public demonstration of the motor in 1888.

Also, in March 1888 he published _Electrodynamic rotations produced by means of alternate currents_ wherein he showed a method for producing those 90° out-of-phase currents. See Figure 92 in the diagram. This would be done by supplying the electromagnets with branches from the same AC source. One branch would have resistance but no self-inductance and the other would have a small resistance but a high self-inductance. These would then feed the windings of the coils. He then described how he'd succeeded in doing experiments along those lines in 1885. In April 1889, Nikola Tesla [described this same method](https://archive.org/stream/polyphaseelectri00thomuoft#page/98/mode/2up) of _splitting the phase_ but only to be used for starting a synchronous motor (more on synchronous motors later).

## Nikola Tesla (1882 or 1887)

![US patent 382,279 Electro magnetic motor - Figure 1](https://hackadaycom.files.wordpress.com/2017/09/uspatent_382279_electromagnetic_motor_figure_1.jpg)

> _US patent 382,279 Electro magnetic motor - Figure 1_

And speaking of Nikola Tesla, he claims to have thought of the idea of the rotating magnetic field one afternoon in 1882 while walking in a park. But it wasn't until November 1887 that he filed his first patent for an induction motor, and the patent wasn't granted until May 1888. That was [US patent 382,279, Electro-magnetic motor](https://www.google.ca/patents/US382279?dq=382,279&hl=en&sa=X&ved=0ahUKEwj2ruf6ybHWAhWJw4MKHWGBDU0Q6AEIJjAA). Figure 1 from that patent is shown here. The motor is at the top and an AC generator is at the bottom.

In those overlapping dates of the Italian Ferraris' and Serbian Tesla's, lies a dispute which exists to this day. Ferraris made and demonstrated his motor in 1885 but not publicly until 1888. Whereas Tesla thought of the idea in 1882 but didn't file a patent until 1887. Both claimed to have come up with the idea for the rotating magnetic field independently, and that's not unusual when many experimenters are working on similar problems, all with the same novel technology.

Tesla's patent points out that the rotor rotates more slowly than the stator's magnetic field. Though not a new finding, it's an interesting and necessary feature of induction motors. In order for a magnet's magnetic field to induce current flow in a material like copper, for example, there has to be a relative motion between them. If the magnetic field and the copper rotor are rotating at the same speed then there is no relative motion and the rotor will slow down. That slowing down creates a relative motion and current is induced, speeding up the rotor. Basically, when the motor is first powered, i.e. the rotating magnetic field is first applied, the rotor begins to rotate. Its speed increases until a balance is found between the induced current and thus torque, and the mechanical load.

The ratio of the speed of the magnetic field being applied to the rotor, to the speed of the magnetic field created by the induced current is called _slip_. This difference in speeds is why an induction motor is often called an asynchronous motor. A type of motor where the speeds are the same, or synchronized, is called a [synchronous motor](https://en.wikipedia.org/wiki/Synchronous_motor).

Another interesting feature of the motor in Figure 1 of Tesla's patent is that rather than using copper plates in the rotor, Tesla uses copper coils in closes loops. You can see that the rotor is made up of two pieces, fixed at 90° to each other. The bulk of the two pieces are soft iron but each has a coil wrapped around it. The coils are simply closed loops and it's in these coils that the current is induced and it's from them that the magnetic field is formed.

## Closing Our Own Loop

While that was the invention of the induction motor, it was by no means the end of its development. We could talk about wound type motors vs. squirrel cage motors, different starting methods, speed control and more. This was now the dawning of the electrical age with power grids springing up all over the world, and the induction motor was just one of a multitude of new types of electric devices. So instead we'll direct you to our [Bryan Cockfield]'s article [demystifying the power grid](https://hackaday.com/2017/01/17/the-electrical-grid-demystified/), or perhaps you'd like to read up on [Nikola Tesla's collisions with Thomas Edison](https://hackaday.com/2017/01/25/tesla-vs-edison/), or about [Edison's involvement in inventing the lightbulb](https://hackaday.com/2017/03/20/how-many-inventors-does-it-take-to-invent-a-light-bulb/).

![solenoid motor](https://hackadaycom.files.wordpress.com/2016/02/motor1.jpg?w=800)
