# Specific reasons why a top left origin is better/worse than a bottom left origin for computer graphics

_Captured: 2016-06-02 at 09:17 from [programmers.stackexchange.com](http://programmers.stackexchange.com/questions/252386/specific-reasons-why-a-top-left-origin-is-better-worse-than-a-bottom-left-origin)_

I believe it is somewhat bound up with development of technology and applications.

## The case

Text sent over serial communications, goes first character first, second character second, and so on. IMHO, it makes no sense to do otherwise because we can start reading as soon as the message starts, and we don't need any extra layout information. For western languages, that is top left, to bottom right. This started with the telegraph. The West developed much of the technology, so it makes sense that we made it easy for ourselves.

Text stored in computer memory is easiest to receive low address to high address, and easiest to manipulate when it is in the same order as we read it, first character at the lowest address, last character at the highest address.

Early text terminals did not store pixels, but instead stored character codes, and converted character codes to pixels on the fly (in hardware). So storing the received character codes in screen memory was the simplest option. Early personal computers did the same, and for some personal computers, the screen memory was just ordinary memory. So it uses less resources, or is easier to make, and easier to program for screen memory and in-memory text to store characters in the same order.

Screen memory must be serialised to an image representation in the order the screen needs it, i.e. for the electron gun to paint it. Technically, the electron-gun scan direction may be arbitrary, and could start in any corner, but IMHO culturally it makes sense for western language readers. Hence existing display devices (CRT's painting top-left to bottom-right) worked perfectly as computer displays.

It makes sense for western languages to have the _text_ 0, 0 origin for a text display start at the top left.

IMHO, it makes a lot of sense to match a graphics device 0,0 origin to the textual display origin (though, IIRC, some devices did not!).

## More Detail

The in-memory screen image is a chunk of memory with linearly increasing addresses. So the electronics to retrieve memory for display would be a more convenient if the screen-refresh counter started at '0' (i.e. the start of image memory), and just incremented in synch with drawing the screen. Simple DMA systems do this. It would then make some more sense that the graphic coordinate system map to that memory address simply. Minimum complexity would argue for aligning screen refresh addressing with graphics coordinate addressing; and they would share an origin.

The opposite case, where the two addressing schemes work in the opposite direction seems to increase hardware complexity for no apparent hardware benefit. At the time these decisions were being made, hardware was expensive.

However, I think the story starts with text terminals, remote text display devices for shared computers. Some old fashioned 'dumb character terminals' (which were CRT based) were addressed from the first line down, when they moved to a character position. So if you think about textual displays as a starting point, it might make more sense than starting with graphics.

Top-left origin makes sense for things like textual menu's and textual user interfaces (e.g. forms), which is typically read top to bottom left to right in western languages.

It is easy to write text onto a screen starting top left (western language), and it is somewhat independent of screen resolution; just let the device fold text or scroll when a boundary is reached.

Further, it took quite a lot of processing power to scroll the text up the screen (yes, seriously), and that visual effect was quite unpleasant (scrolling an entire row of text by a character height, on a long persistence phosphor screen), so it would make some sense to make it easy to start writing at the top of the screen, and minimise scrolling.

Typically the screen could be cleared completely, and the cursor set top left with a single command. Also it might be using communications systems with under 300 characters/second, 2400 baud (I know people who read faster than that).

Those display devices would typically wrap onto the next line automatically and silently (yes, seriously).

So it takes _no_ maths to write (western) text, top to bottom, staring at the top, the devices can be quite simple, and the comms quite slow.

So, the display is doing some of the work autonomously, it is _not_ all done by the program, and in-terminal processing is limited. It might even struggle to receive text, and write it if it had to scroll every line it receives.

The terminal is connecting to the computing system over public telephone lines, using modems, their is limited bandwidth (say 2400 baud). The shared computer might not know what type of terminal is connecting.

It is practical to write from the top left, using little more than tab, line-feed, return and clear screen. As long as the developer ensures the textual menu does not scroll off the screen on the smallest screens, then it is somewhat deice and screen resolution independent. The effect is quite pleasing because the screen text 'stays still', making it easy to read before the whole screen is finished, rather than flickering with scrolling.

Driving round the screen (e.g. using cursor keys), or jumping to a specific character location is straightforward because the in-memory coordinates of the text and the screen coordinates are 'the same'.
