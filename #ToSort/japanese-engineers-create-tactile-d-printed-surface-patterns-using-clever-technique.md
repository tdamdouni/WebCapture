# Japanese engineers create tactile 3D printed surface patterns using clever technique

_Captured: 2017-12-28 at 05:48 from [www.3ders.org](http://www.3ders.org/articles/20171221-japanese-engineers-create-tactile-3d-printed-surface-patterns-using-clever-technique.html)_

Japanese engineers Haruki Takahashi and Homei Miyashita have devised a 3D printing technique that controls printing thickness by increasing and decreasing the amount of material extruded during printing. The technique enables the 3D printing of tactile surfaces on standard FDM 3D printers.

![](http://www.3ders.org/images2017/japanese-engineers-create-tactile-3d-printed-surface-patterns-using-clever-technique-2.jpg)

Although it is possible to create intricate, patterned surfaces using a 3D printer, doing so can be tricky: the layer-by-layer procedure of additive manufacturing makes it difficult to obtain complex patterns, especially on a small scale, and individual layers of the print can easily become conspicuous in what is supposed to be a smooth, unbroken curve. Haruki Takahashi and Prof. Homei Miyashita, both of Japan's Meiji University, have devised a novel technique for 3D printing tactile surfaces that sidesteps what they call the "staircase effect," caused by the limitations of printer resolution.

According to Takahashi and Miyashita, the new 3D printing technique, developed over the course of two years, allows 3D printer users to dynamically control printing thickness, enabling them to 3D print aesthetic pattern sheets and tactile objects without the use of any extra hardware. The technique, a "method of generating and calculating a movement path for printing tactile sheets," is especially useful for creating precise, complex surface patterns with an FDM 3D printer, and can be implemented on ordinary machines.

Rather than create complete surface patterns using CAD software, the engineers' new technique relies upon modifying 3D printer gCode. The principle is simple: instead of setting a fixed extrusion thickness, the engineers program the printer gCode to vary the thickness in "micromovements" across a single layer. This produces interesting results. For example, the 3D printer can extrude a "line" of plastic which starts very fine and gets increasingly thick, by instructing the printer to extrude in steps of increasing thickness.

![](http://www.3ders.org/images2017/japanese-engineers-create-tactile-3d-printed-surface-patterns-using-clever-technique-1.jpg)

The advantage of using this technique is that it avoids the so-called "staircase effect." If a similar thin-to-thick pattern were designed on CAD software, a printer (set to a fixed extrusion width) might struggle to produce a similarly smooth gradient. By manipulating the gCode, however, the engineers are able to sidestep some of the limitations of printer resolution, creating all kinds of intricate tactile patterns with an even surface texture.

According to Takahashi and Miyashita, the technique could be used in various applications. Since the thin sheets of 3D printed plastic can be easily laser-cut, the materials can be used as replacements for all sorts of "luxurious" materials, such as leather. The engineers successfully created a tactile 3D printed watch strap using the printing technique, but the wide range of potential patterns means the process could be used to create almost anything.

Maybe you also like:

Vikas wrote at 12/22/2017 12:47:45 PM:

Is it open source? How do I convert the conventional gCodes from a slicer into the ones being talked about?
