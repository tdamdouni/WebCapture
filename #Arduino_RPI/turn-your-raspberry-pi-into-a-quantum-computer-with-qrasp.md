# Turn Your Raspberry Pi into a Quantum Computer with Qrasp

_Captured: 2019-03-08 at 09:26 from [blog.hackster.io](https://blog.hackster.io/turn-your-raspberry-pi-into-a-quantum-computer-with-qrasp-4ccde390a48a?mc_cid=731580a1dd&mc_eid=1c68da4188)_

We've been hearing about the potential of quantum computing for decades now, but the idea of working with an _actual _quantum computer has always seemed like a distant possibility. That all changed recently when the first commercial quantum computer, the IBM Q System One, was introduced. Now, quantum computing is actually possible. Hassi Norlen wanted to experience that for himself, so [he decided to create Qrasp -- a Raspberry Pi quantum computer](https://medium.com/qiskit/qrasp-a-wee-quantum-computer-74ef7f927b1e).

![](https://cdn-images-1.medium.com/freeze/max/60/1*DfS8H3CVgdhv_szDDTvu6w.gif?q=20)![](https://cdn-images-1.medium.com/max/1600/1*DfS8H3CVgdhv_szDDTvu6w.gif)

The [IBM](https://www.hackster.io/ibm) [Q System One](https://www.research.ibm.com/ibm-q/system-one/) is, quite obviously, a major technological breakthrough. Quantum computing is fundamentally different than traditional computing, and far more difficult to achieve. But we're reaching the physical limits of conventional computing, simply due to the fact that transistors -- the basic units of computers today-- are about as small as they can physically be. Quantum computing relies on sub-atomic qubits, which are smaller and, more importantly, can be worked with simultaneously in parallel.

As amazing as the IBM Q System One is, however, it isn't something you can own yourself. It's a quantum computer that is only accessible as a cloud service. Norlen wasn't satisfied with that, and wanted the ability to do quantum computing in his own home. To do that, he turned to a surprising device: [the humble Raspberry Pi](https://www.hackster.io/raspberry-pi).

The result is Qrasp, and you can build one yourself. To be clear, this doesn't somehow turn the Raspberry Pi into a _real_ quantum computer. Rather, it uses software called Qiskit to simulate a basic quantum computer. From a practical perspective, it's a lot like running a quantum computer emulator on the Raspberry Pi. You won't get the true benefits of quantum computing, but you can experience the way it works.

Qiskit is based on [Python](https://www.hackster.io/python-on-hardware), which means it can run natively on a Raspberry Pi. Norlen's Qrasp code takes advantage of that to run quantum computing simulations directly on the Pi, without even requiring internet access. Visualized results of those quantum computations are then displayed on a Sense HAT [RGB LED matrix display](https://www.hackster.io/displays). If you want to get a taste of quantum computing, Qrasp is a really affordable way to do so.
