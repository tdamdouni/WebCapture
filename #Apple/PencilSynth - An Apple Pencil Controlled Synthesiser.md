# PencilSynth - An Apple Pencil Controlled Synthesiser

_Captured: 2015-11-25 at 12:44 from [flexmonkey.blogspot.de](http://flexmonkey.blogspot.de/2015/11/pencilsynth-apple-pencil-controlled.html?m=1)_

Here's another [Apple Pencil](http://flexmonkey.blogspot.co.uk/search/label/Apple%20Pencil) experiment, [PencilSynth](https://github.com/FlexMonkey/PencilSynth) is an [AudioKit](http://audiokit.io/) powered synthesiser (mis)using the Pencil as a joystick controller. It's based on AudioKit's [TouchRegions](http://audiokit.io/examples/swift/TouchRegions/) demonstration and works like this:

  * Given:
  * The Pencil's horizontal position on the screen defines the output frequency:

let frequency = touch.locationInView(view).x / view.bounds.width

  * The Pencil's vertical position on the screen defines the output modulating multiplier:

let modulatingMultiplier = touch.locationInView(view).y / view.bounds.height

  * The Pencil's altitude angle defines the output carrier multiplier:

let carrierMultiplier = (halfPi - touch.altitudeAngle) / halfPi

  * The Pencil's azimuth angle defines the output modulation index:

let modulationIndex = (pi + touch.azimuthAngleInView(view)) / (pi * 2)

Those four normalised values are plugged into an instance of [FMOscillator](https://github.com/FlexMonkey/PencilSynth/blob/master/PencilSynth/FMOscillator.swift) (which is taken directly from the TouchRegions demo):

oscillator.frequency.value = (oscillator.frequency.maximum - oscillator.frequency.minimum) * Float(frequency)

oscillator.modulatingMultiplier.value = (oscillator.modulatingMultiplier.maximum - oscillator.modulatingMultiplier.minimum) * Float(modulatingMultiplier)

oscillator.carrierMultiplier.value = (oscillator.carrierMultiplier.maximum - oscillator.carrierMultiplier.minimum) * Float(carrierMultiplier)

oscillator.modulationIndex.value = (oscillator.modulationIndex.maximum - oscillator.modulationIndex.minimum) * Float(modulationIndex)

The orientation and rendering of the "virtual pencil" is taken straight from my [PencilController](http://flexmonkey.blogspot.co.uk/2015/11/pencilcontroller-using-apple-pencil-as.html) demo.

The GitHub repository contains the AudioKit source, but all my code exists in the [view controller class](https://github.com/FlexMonkey/PencilSynth/blob/master/PencilSynth/ViewController.swift).

In conclusion, the [Apple Pencil](http://www.apple.com/uk/apple-pencil/) opens up a world of new interaction design paradigms (despite what [Jony Ive may tell us](http://www.macrumors.com/2015/11/17/apple-pencil-jony-ive/)!). PencilSynth and my [Pencil based image processing app](http://flexmonkey.blogspot.co.uk/2015/11/pencilcontroller-using-apple-pencil-as.html) are, I think, demonstrations that the Pencil is an excellent input device for controlling continuous values across multiple dimensions.

As always, the source code for this project is available at [my GitHub repository here](https://github.com/FlexMonkey/PencilSynth). Enjoy!
