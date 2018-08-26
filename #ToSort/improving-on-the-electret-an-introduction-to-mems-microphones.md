# Improving on the Electret: An Introduction to MEMS Microphones

_Captured: 2018-04-07 at 10:01 from [www.allaboutcircuits.com](https://www.allaboutcircuits.com/technical-articles/improving-on-the-electret-an-introduction-to-mems-microphones/)_

This technical brief explains the physical characteristics and the benefits of microphones based on MEMS technology.

A well-known recording component for simple, low-cost audio circuits is the electret microphone. Electrets belong to the category of condenser microphones, i.e., microphones that use a capacitive element to convert electrical signals from sound waves. Electret microphones are undoubtedly adequate in many applications; nevertheless, it's good to be aware that you now have another option: MEMS.

MEMS stands for "microelectromechanical systems" and refers to (very) small devices that include moving parts. You've probably heard of MEMS gyroscopes or accelerometers, but it seems to me that MEMS microphones are not so well known.

#### The Structure

In terms of the actual transducer element, a MEMS microphone is not fundamentally different from an electret. Both rely on a capacitive element that exhibits changes in capacitance corresponding to the air-pressure variations that we call sound.

But the capacitive element in a MEMS microphone is fabricated using (you guessed it) MEMS technology; in other words, the transducer is a microscopic component that fits right in with the microscopic semiconductor-based components in an integrated circuit. This innovation leads to microphone modules that are smaller and more user-friendly.

![](https://www.allaboutcircuits.com/uploads/articles/TB_MEMSM_1.JPG)

The above diagram gives you the general idea of how a MEMS mic is made. A single housing contains both the transducer and the signal processing circuit. One thing that separates MEMS microphones from typical ICs is the gap in the housing. We usually expect semiconductor devices to be sealed from the external environment, but in this case, we need something that allows sound waves to reach the transducer.

#### The Benefits

You might be inclined to approach MEMS microphones with the "if it's not broken, don't fix it" attitude. Why switch to MEMS when my electret is working just fine?

First, MEMS devices might provide enhanced audio performance. One manufacturer, [Knowles](http://www.knowles.com/eng/Products/Microphones/SiSonic™-surface-mount-MEMS), claims that MEMS mics offer "improved performance in varied environmental conditions." My guess is that you would need to carefully consider your various design goals and constraints in order to determine if MEMS would be significantly better than electret in terms of audio quality.

Second, MEMS is smaller. In the world of consumer electronics, smaller equals better, though in your application the size of an electret microphone might be perfectly adequate.

Third--and this is the big one--MEMS microphones offer high levels of integration that enable impressive functionality combined with ease of use.

#### Complicated for the Manufacturer, Simple for the Board Designer

Electret microphones need a preamplifier circuit. Even when you have an IC specifically designed for this task (such as the [MAX4466](https://www.allaboutcircuits.com/electronic-components/datasheet/MAX4466EUK-Maxim-Integrated)), you still need quite a few components:

![](https://www.allaboutcircuits.com/uploads/articles/TB_MEMSM_2.jpg)

MEMS microphones can eliminate this additional design effort by incorporating preamplifier circuitry into the microphone module. The output of the "microphone" is now a buffered (and, in some cases, amplified) analog audio signal. However, the output impedance might not be nearly as low as what you would see from a typical op-amp, so check the datasheet and design accordingly.

Actually, the integrated preamp is only the beginning. The signal-processing IC inside the microphone module is not limited to analog circuitry. So why not finish the job and digitize the analog waveform coming from the preamp? Now the "microphone" outputs digital audio data that can be sent directly to a microcontroller or digital signal processor.

![](https://www.allaboutcircuits.com/uploads/articles/TB_MEMSM_3.JPG)

> _Pulse density modulation is a common digital-MEMS-microphone output format._

#### Conclusion

MEMS microphones offer impressive features and, in certain applications, they are far superior to electret-based solutions. Keep them in mind for your next audio project.
