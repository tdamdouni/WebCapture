# To Build the World’s Smallest Atomic Clock, Trap a Nitrogen Atom in a Carbon Cage

_Captured: 2017-12-25 at 15:10 from [spectrum.ieee.org](https://spectrum.ieee.org/semiconductors/materials/to-build-the-worlds-smallest-atomic-clock-trap-a-nitrogen-atom-in-a-carbon-cage)_

![illustration of a caged atom](https://spectrum.ieee.org/image/Mjk4NjA1MQ.jpeg)

> _Illustration: Emily Cooper_

**For Fridtjof Nansen,** 13 April 1895 started well. Six days earlier, the Norwegian explorer had set a new record for the closest approach to the North Pole, and now he was moving quickly over unbroken sea ice toward Cape Fligely and home. But then came a sickening realization: In his eagerness to break camp, he had forgotten to wind the chronometers. He had lost track of precise time, and thus the ability to track his longitude.

Although Nansen couldn't have lost his position by more than a few minutes, it forced him to take a circuitously conservative route to avoid being swept into the North Atlantic. His expedition thus had to endure a hungry winter, camped on an unknown shore. Not until June the following year did he encounter other explorers and learn his true position--on Cape Felder, in Franz Josef Land.

Today, anyone with a smartphone can determine their time and position with ease. Satellites of the Global Positioning System (GPS) broadcast clock signals across the globe with uncertainties below 100 nanoseconds, or one ten-millionth of a second. These time signals carry the information needed for precise navigation: Because radio waves travel at exactly 0.299,792,458 meters per nanosecond (apart from minuscule variations due to refraction in the atmosphere), comparing signals from different satellites makes it possible to determine a position within a few meters. That's why GPS has [transformed seismic monitors](https://www.earthmagazine.org/article/precise-fault-how-gps-revolutionized-seismic-research), [drone delivery](https://spectrum.ieee.org/the-human-os/robotics/drones/africa-leads-the-world-on-drone-delivery), and many other applications.

But GPS can't solve all timing problems. Central to the system are atomic clocks carried on each satellite. Although these clocks are extremely stable (and regularly calibrated by comparing them with ground-based atomic clocks at national standards laboratories), there are many ways to go wrong when transferring timing information to the user--jamming, spoofing, unintentional interference, solar storms, even reflections from buildings. But what if we could put this precision directly in the hands of the user by shrinking the atomic clock itself so it could work inside the GPS receiver? Would we, like Nansen, then want to carry our very best clocks with us?

In research [now](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.119.140801) published at _[Physical Review Letters](https://arxiv.org/abs/1705.04817)_, we show that such a mobile clock is possible. We hope to make one soon.

**The core of** an atomic clock is a vacuum chamber containing a thin cloud of vaporized metal, usually cesium. Atoms in the vapor resonate at a precise frequency, meaning that their electrons will accept energy only from photons having just the right amount of it. If those photons have a little too much or too little energy--that is, if their frequency is a little too high or too low--the absorption falls off markedly. This is the key feature of an atomic clock.

![img](https://spectrum.ieee.org/image/Mjk4NjA3MQ.jpeg)![img](https://spectrum.ieee.org/image/Mjk4NjE3Nw.jpeg)

> _Photo: National Physical Laboratory_

Here's how it works. An electrical oscillator creates a microwave frequency very close to the energy level of the atom we are using for our clock. If the oscillator deviates slightly from the correct frequency, the absorption changes, the change is detected by a laser, and the laser's signal is used to tune the oscillator. This feedback loop corrects the oscillator's imperfections.

Unlike the pendulum of a clock or the mechanical mechanism of a watch, atoms do not suffer from manufacturing error or wear; with proper isolation from the environment, their resonant frequency is set by the laws of physics. Achieving the necessary level of isolation in practice means that the best atomic clocks take up entire rooms. Commercial atomic clocks are usually the size of suitcases.

In 2004, in a tour de force of microfabrication, scientists at the National Institute of Standards and Technology managed to shrink this entire setup into a stack of components a few millimeters high. Such "chip-scale" atomic clocks are now available commercially and are used in niche applications, such as military communications and underwater navigation. But this miniaturization comes at a price--and not just in manufacturing cost: Because so many of the atoms interact with the chamber walls, the tiny size of the vacuum chamber can lead to small changes in the clock frequency, while the heater that generates the vapor constitutes a hefty power drain for a portable device. It'll be a long time before this technology makes it into your cellphone.

Fortunately, there is an alternative, proposed in 2008 by Andrew Briggs and Arzhang Ardavan at the University of Oxford, in England. Instead of using a chamber to trap atoms, this method makes use of nature's own trap: an endohedral fullerene.

![illustration of carbon atom](https://spectrum.ieee.org/image/Mjk4NjA3OA.jpeg)

> _Illustration: Emily Cooper_

Endohedral fullerenes, or endofullerenes, are remarkable molecules that almost seem to defy ordinary laws of chemical bonding. The outside is a fullerene (named after Buckminster Fuller, champion of the geodesic dome), a hollow ball of atoms that can function as a container. An atom or a smaller molecule can fit inside without bonding to the shell and is thus protected from its environment--even though an atomic cage filled in this way has properties similar to those of an empty fullerene.

Without doubt the most extraordinary of any such endohedral fullerene is N@C60--a nitrogen atom inside a 60-carbon fullerene cage, which resembles a soccer ball. It's as though the nitrogen atom floats inside the fullerene, retaining its atomic characteristics. Noble gas elements, such as helium and neon, have also been incorporated in C60. These are very inert species, unlike nitrogen, which is one of the most reactive elements known. And it turns out that nitrogen is key for making an accurate atomic clock.

N@C60 is a molecule that, given the reactivity of nitrogen, should not exist. Nevertheless, there are several ways to synthesize N@C60. Extreme conditions are needed for all of these methods, because pushing the nitrogen atom through the carbon cage is thermodynamically unfavorable--the chemical equivalent of pushing water uphill. Once the molecule is formed, however, the fullerene cage isolates and stabilizes the nitrogen atom, so the products synthesized can be collected and stored.

At our laboratory at the University of Oxford, we make these caged molecules with what's called ion implantation. Heat is used to vaporize fullerenes in a vacuum chamber, where they waft onto a surface. This process gradually builds up a C60 film on that surface.

While the C60 film is growing, nitrogen ions are shot onto the surface of the film. Some of those nitrogen ions get trapped in the growing C60 film, forming the desired molecule. The yield, however, is very low: For every molecule of N@C60, there will be about 10,000 molecules of nitrogenless C60.

Purifying N@C60 is hard because C60 and N@C60 are chemically almost identical. The key word here is _almost_. Small differences in molecular weight and polarizability between the molecules mean that it's possible to separate them by applying a technique called high-pressure liquid chromatography, or HPLC. We were the first to develop this technique in 2004, and we still do it in the same way at [Designer Carbon Materials](http://www.designercarbon.com/), the company we spun off from Oxford in 2014.

Our company has begun to sell N@C60 and other bespoke endohedral fullerenes to research groups around the world. If you need some, we'd be happy to sell you however much you want: We charge £200 million per gram.

In standard chromatography, substances having different chemical characteristics are separated by making them run a kind of gauntlet--an obstacle course that blocks the passage of one thing more than the other. HPLC works by using a pumped solvent (hence the term "high pressure") to strip off the laid-down film of carbon fullerenes in such a way that the desired molecules--the fullerenes encasing nitrogen--are carried away preferentially. Because of the limited content of N@C60 in the crude mixture, this process must be repeated many times. That recycling can achieve complete separation between C60 and N@C60.

![illustration showing vacuum chamber](https://spectrum.ieee.org/image/Mjk4NjA4NA.jpeg)

> _Illustration: Emily Cooper_

Back to the atomic clock: We start with an oscillator that generates a radio signal close to the frequency that the nitrogen will absorb. We transmit the signal via an antenna to a cell containing a sample of the molecules, either as a powder or in solution. If the oscillator is correctly tuned, power is absorbed. If we see a reduction in the absorbed power, we'll know that the oscillator has drifted away from the target frequency. Using a feedback mechanism, the oscillator can then be tuned back to the point of maximum absorption. Because this frequency is precisely known, an accurate time reference follows by simply counting cycles of the stabilized oscillator. We manage the feedback by modulating the oscillator frequency and having the detector look at that modulation. If the oscillator is set correctly, the modulation of the output is zero; if the oscillator's central frequency has deviated, the sign of the output modulation tells us which side of the resonance it has moved to.

Endohedral fullerenes such as N@C60 are outstanding reference materials because, as [we showed in 2006](http://aip.scitation.org/doi/10.1063/1.2147262), the transitions between their quantum-mechanical spin states have some of the most precisely delineated frequencies of any molecule. If you draw a graph of the materials' response to stimulating radiation, it will show a very narrow peak at the resonant frequency. Also, the fullerene cage prevents the walls of the container from affecting the frequency. One external influence does, however, penetrate the fullerene cage and can alter the relevant frequencies: a magnetic field. Because the world is full of uncontrolled magnetic fields--for example, from electric motors, steel vehicles, and Earth itself--protection from them is crucial for a stable clock. What Briggs and Ardavan realized is that for the N@C60 molecule, applying a small, static magnetic field can tune the energy levels in such a way that all magnetic influences on the resonance frequency cancel each other out.

**The point,** of course, is to one day incorporate a complete atomic clock into one chip. In this design, the entire operation is based on radio-frequency electronics, avoiding the need for optical elements, as used in conventional atomic clocks. And unlike a vapor-based clock, there would be no need to maintain a vacuum chamber and no power-hungry heater to drain a battery. An endofullerene-based atomic clock could thus be small, light, and energy efficient. Potentially, it could replace many of the quartz oscillators used in nearly every present-day electronic device to keep time.

Our progress toward that goal reached a key milestone this year, when [we showed](https://arxiv.org/abs/1705.04817) that the energy levels in our carbon-shielded nitrogen ion are insensitive to magnetic field noise. We have not yet incorporated the material into a prototype clock, although we hope to do so soon.

![<strong&gtDissolved Fullerenes:</strong&gt The purified nitrogen-trapping fullerenes are shown here in solution.](https://spectrum.ieee.org/image/Mjk4NjE1NA.jpeg)

> _The purified nitrogen-trapping fullerenes are shown here in solution._

1/3

Historically, every generation of portable timekeepers has led to new possibilities. Early applications are likely to take advantage of the fact that a precise clock is also a precise frequency synthesizer. For example, in wireless communication, multiplexing channels into one frequency band requires every transmitter to keep strictly to its assigned carrier frequency. (This is the reason that some cellphone towers are already equipped with atomic clocks.) As future networks, such as the Internet of Things, crowd into a limited spectrum, portable and stable clocks will become increasingly necessary.

For a similar reason, GPS receivers will benefit from onboard clocks. This is perhaps surprising, given that the GPS signal itself carries time information, but it happens because the signal from the satellite is weak--comparable to the power of a lightbulb transmitted across a continent. Landscape features, buildings, and interference make it harder to detect. To track this weak signal, the receiver must precisely lock onto the broadcast frequency. The more stable the local frequency reference, the faster and more reliable this tracking can be.

In hostile environments, such as battlefields, this becomes even more important. The GPS signal is vulnerable to jamming, and effective (but illegal) jammers are widely available and likely to be encountered in future wars. With precise timing information, GPS receivers could isolate the true signal above the noise of the jammer. The receivers could even allow navigation to survive partial destruction of the satellite network.

Present-day receivers must determine their positions by using signals from four or more satellites simultaneously, but a sufficiently accurate clock could instead use successive signals from a single satellite. Other defense applications include frequency-hopping communication, bistatic radar (in which an attacker stealthily acquires a radar signal from a target illuminated by a distant transmitter), and sensitive monitoring of enemy communications. For these reasons, portable clocks are of great interest to militaries in several countries.

Finally, there may be completely new applications. For example, warehouses, post offices, and even subways may in future be equipped with their own local positioning systems using small-scale wireless base stations. Parcels, equipment, and people could then be tracked without needing anyone to sign off on the delivery of a package or log its position at every location. Even driverless cars would benefit from an onboard device that keeps very accurate time in challenging terrains, such as tunnels, where satellite GPS signals are unavailable.

For these possibilities to be realized, many elements must come together. First, it will be necessary to optimize the stability of the atomic resonance frequency on which the clock depends. For the technology to be competitive, the frequency fluctuations must be well below one part in a million, despite variations of temperature, magnetic field, and chemical environment. Second will be the task of miniaturization--of shrinking sample cell, magnet, and radio-frequency electronics down to a chip-scale device. Third is the need for low power consumption. Last is the need to manufacture endohedral fullerenes on an industrial scale, materials that so far exist only in milligram quantities.

Despite this, endohedral fullerenes are already starting to appear on the market. The technology firm LocatorX, of Jacksonville, Fla., has licensed the Oxford atomic-clock patent and is developing it for commercial use.

For miniaturized atomic clocks to be incorporated in everyday devices, we must push many different areas in science and engineering to their limits. But the rewards are fantastically important. We look forward to the day when the hearts of endohedral fullerenes beat time all around us.

_This article appears in the December 2017 print issue as "Keeping Perfect Time With Caged Atoms."_

## About the Authors

[Kyriakos Porfyrakis](http://www.materials.ox.ac.uk/peoplepages/porfyrakis.html) is an associate professor of materials at the University of Oxford. [Edward A. Laird](http://www.materials.ox.ac.uk/peoplepages/laird.html) is a Royal Academy of Engineering Research Fellow there.
