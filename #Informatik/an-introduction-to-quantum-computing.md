# An Introduction to Quantum Computing

_Captured: 2017-12-28 at 19:59 from [dzone.com](https://dzone.com/articles/an-introduction-to-quantum-computing-ankit-sharmas?edition=347140&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-28)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

There is a lot of buzz about quantum computing, and Microsoft has officially announced a Quantum Development Kit and Q#, the language for quantum computing. In this article, I am going to cover some of the basics of quantum computing and also set up an environment on our local machine with Visual Studio 2017 to get started with quantum programming.

## **What Is Quantum Theory?**

Quantum theory is the branch of physics that deals with the world of atoms and the smaller subatomic particles inside them. The laws of physics are different at the atomic level and the classic laws of physics that we can observe in our daily life won't apply here.

## **Limitations of Classic Computers**

Classic computers (the machines we use in our daily lives, including laptops, desktop, servers, etc.) have made our life very simple and fast. We have achieved a lot of things and the world has completely changed with the advent of computers in the last century. But classical computers have some limitations, too.

A classic computer uses transistors to form logical switches that either allow electric currents to pass through them (switch "on") or restrict the current flow (switch "off"). Over time, the size of the transistors has become very small, which allows us to fit millions of transistors onto a small chip, giving rise to small portable computers with increased computing power (i.e. smartphones) -- but we are approaching a physical limit of making the transistor smaller. Today, transistors have already achieved the size of 1 nanometer. On an atomic range (less than 1 nanometer), the electrons behave weirdly and don't follow the principles of physics that are normally applicable to larger objects. On the atomic scale, the electrons have the [quantum tunneling](https://en.wikipedia.org/wiki/Quantum_tunnelling) effect, i.e. it sometimes behaves like a wave and passes through closed logical switches, as well, thus nullifying the presence of a logical switch. Since we can't have a perfect transistor switch at such small sizes, we have reached a final limit of how many transistors we can fit in a small area, keeping the transistors just big enough to avoid the quantum tunneling effect. This, in turn, holds us back from increasing the computation power of our computers.

There are a lot of problems that grow exponentially in terms of computation, and due to the limitation of classical computers, it will take years to solve them. We need to look for a more efficient way to solve these problems. The answers lie in quantum computers.

## **What Is a Quantum Computer?**

Quantum computers are machines built on the principles of quantum mechanics that take a new approach to processing information, thus making them super powerful. Quantum computers use Qubits to process the information.

### **What Is a Qubit?**

The fundamental unit of processing information in a classical computer is a bit that can hold binary values (0 or 1). The analogous to the bit is Qubit (short for the quantum bit) in quantum computers. Qubits have special properties that help them solve complex problems much faster than classical bits. One of these properties is superposition that states that instead of holding one binary value (0 or 1) like a classical bit, a Qubit can hold a combination of "0" and "1" simultaneously. When multiple Qubits interact coherently, they can explore multiple options and process information in a fraction of the time compared to the classical, even the fastest non-quantum, systems.

![](https://i1.wp.com/ankitsharmablogs.com/wp-content/uploads/2017/12/220px-Bloch_Sphere.png?resize=220%2C250)

> _Figure 1: Representation of a Qubit (Wikipedia)_

In reality, Qubits would have to be stored by atoms, ions, or even smaller things such as electrons and photons.

### **What Is the Superposition Principle?**

[Superposition](https://en.wikipedia.org/wiki/Superposition_principle) is essentially the ability of a quantum system to be in multiple states at the same time -- that is, something can be "here" and "there" or "up" and "down" at the same time. This behavior is only observed at an atomic level.

A Qubit can exist in Superposition of 0 and 1, i.e. it can store a 0, a 1, both 0 and 1, or an infinite number of values in between. They can also create a complex superposition of 0 and 1 by interacting with other Qubits. The total number of superpositions that are possible with _n_ Qubits is 2n.

### **What Is Entanglement?**

[Entanglement](https://en.wikipedia.org/wiki/Quantum_entanglement) is an extremely strong correlation that exists between quantum particles -- so strong, in fact, that two or more quantum particles can be inextricably linked in perfect unison, even if separated by great distances. This means that the quantum state of each particle cannot be described independently of each other. The particles are so intrinsically connected that they can be said to "dance" in instantaneous, perfect unison, even when placed at opposite ends of the universe.

The states of entangled Qubits cannot be described independently of each other. This means that if we measure one Qubit, we also get some information about what will happen if we measure another Qubit.

Superposition and entanglement are two fundamental principles of quantum computing.

### **What Is a Topological Qubit?**

The Qubits sounds interesting but they are highly unstable and even a little disturbance in the system can throw up the whole operation. So, Microsoft is working on to create a more stable Qubit called Topological Qubit. It can store information in a more stable form as compared to other Qubits. Topological Qubit will allow Quantum computer to scale with much higher rate and allow us to build a quantum computer large and stable enough to solve our most challenging problems.

## **What Quantum Computers Are Better at Than Ordinary Computers**

One important point that we should keep in mind is that quantum computers aren't replacing classic computers. But there are few problems that quantum computers can solve with tremendous speed compared to a classic computer. One of such problem is the factorization of a large number, i.e.: if m=p*q, such that p and q are prime, then given the value of m, find the value of p and q.

Another type of problem is where classic computers are unable to give accurate output, such as finding the bond length on chemical compounds such as calcium monofluoride (CaF) and sodium diatomic (Na2).

## **How to Set Up a Quantum Computing Dev Environment on Your Local Machine**

**Prerequisite**: You need Visual Studio 2017 installed on a 64-bit Windows machine. It won't work for the 32-bit installation of Windows or lower versions of Visual Studio.

You can start working on Quantum computing from your local machine also. Microsoft has launched Quantum Development Kit which you can download from [here](https://marketplace.visualstudio.com/items?itemName=quantum.DevKit).

Once you click **Download**, a file `QsharpVSIX.vsix` will be downloaded. You just need to install it like any other program and it will integrate the development kit into your Visual Studio 2017. You need to restart Visual Studio for changes to take effect.

Now open VS 2017 and navigate to **File** > **New** > **Project**.

It will open a dialog box. Select Visual C# from the left menu and then select **Q# Application** from the installed template. Give your project a name and click **OK**.

![](https://i2.wp.com/ankitsharmablogs.com/wp-content/uploads/2017/12/SS_1.png?resize=648%2C396)

> _In the Solution Explorer, you can see the file structure as below._

![](https://i2.wp.com/ankitsharmablogs.com/wp-content/uploads/2017/12/SS_3.png?resize=299%2C184)

Here, `Operation.qs` is the file containing Q# code and `Driver.cs` is our regular C# code file. This is because a quantum computer is like a code processor; we will call the code of Q# file from our main method, which is in the C# file. We can write and simulate a quantum program in this solution file.

Simulating quantum computing will put a lot of load on your system hardware. So, it's recommended to use a system having high RAM (8 GB or more). You can also use Azure Quantum Simulator, which is hosted in the cloud and can be used to simulate a high number of Qubits.

## **Challenges for Quantum Computers**

Currently, we have quantum computers with the strength to manipulate less than 20 Qubits. Google, IBM, and Microsoft are a few names that are working to create a large-scale quantum computer. IBM has even announced a prototype for a 50-Qubits quantum computer. Another challenge is to make the system stable as the number of Qubits increases.

The field of quantum computing is vast, as it incorporates the concepts from quantum physics, superconductors, nanotechnology, and more. Each of these is itself a sophisticated field that is still being fully developed, so building a physical system that follows principles of all these fields is a real challenge.

It will still take at least ten years or even more until we have a quantum computer large and stable enough to solve most of our challenging problems.

## **Conclusion**

The potential of quantum computers is tremendous, and we can achieve a lot that was thought to be nearly impossible with classical computers. We can synthesize new medicines, develop new catalysts, accelerate the development of artificial intelligence, and a lot more. In this article, I have covered a few basics of quantum computers. Please post your valuable feedback in the comments section.

You can always refer to links given below to get more knowledge on quantum computers:

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.
