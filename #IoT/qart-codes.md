# QArt Codes Posted on Thursday, April 12, 2012.

_Captured: 2017-09-12 at 09:20 from [research.swtch.com](https://research.swtch.com/qart)_

QR codes are 2-dimensional bar codes that encode arbitrary text strings. A common use of QR codes is to encode URLs so that people can scan a QR code (for example, on an advertising poster, [building roof](http://www.brandchannel.com/home/post/QR-Marketing-Google-Maps.aspx), [volleyball bikini](http://www.dailymail.co.uk/femail/article-2023726/Beach-volleyball-stars-sign-deal-advertising-bikini-clad-behinds.html), [belt buckle](http://www.flickr.com/photos/fluidforms/3524861901/), or [airplane banner](http://wtfqrcodes.com/post/18551054478/look-in-the-sky-its-a-bird-its-a-plane-its-the)) to load a web site on a cell phone instead of having to "type" in a URL.

QR codes are encoded using [Reed-Solomon error-correcting codes](https://research.swtch.com/field), so that a QR scanner does not have to see every pixel correctly in order to decode the content. The error correction makes it possible to introduce a few errors (fewer than the maximum that the algorithm can fix) in order to make an image. For example, in 2008, [Duncan Robertson](http://whomwah.com/2008/03/12/more-fun-with-qr-codes-and-the-bbc-logo/) took a QR code for "http://bbc.co.uk/programmes" (left) and introduced errors in the form of a BBC logo (right):

![](https://research.swtch.com/qr-bbc.png)

That's a neat trick and a pretty logo, but it's uninteresting from a technical standpoint. Although the BBC logo pixels look like QR code pixels, they are not contribuing to the QR code. The QR reader can't tell much difference between the BBC logo and the Union Jack. There's just a bunch of noise in the middle either way.

![](https://research.swtch.com/qr-bbc1.png)

Since the BBC QR logo appeared, there have been many imitators. Most just slap an obviously out-of-place logo in the middle of the code. This [Disney poster](http://blog.cliffano.com/2009/05/18/qr-code-usage-in-japan/) is notable for being more in the spirit of the BBC code.

There's a different way to put pictures in QR codes. Instead of scribbling on redundant pieces and relying on error correction to preserve the meaning, we can engineer the encoded values to create the picture in a code with no inherent errors, like these:

![](https://research.swtch.com/qart1.png)

![](https://research.swtch.com/qart2.png)

![](https://research.swtch.com/qart3.png)

This post explains the math behind making codes like these, which I call QArt codes. I have published the Go programs that generated these codes at [code.google.com/p/rsc](http://code.google.com/p/rsc/source/browse/qr) and created a [web site for creating these codes](https://research.swtch.com/qr/draw).

###  Background 

For error correction, QR uses Reed-Solomon coding (like nearly everything else). For our purposes, Reed-Solomon coding has two important properties. First, it is what coding theorists call a _systematic code_: you can see the original message in the encoding. That is, the Reed-Solomon encoding of "hello" is "hello" followed by some error-correction bytes. Second, Reed-Solomon encoded messages can be XOR'ed: if we have two different Reed-Solomon encoded blocks b1 and b2 corresponding to messages m1 and m2, b1 ⊕ b2 is also a Reed-Solomon encoded block; it corresponds to the message m1 ⊕ m2. (Here, ⊕ means XOR.) If you are curious about why these two properties are true, see my earlier post, [Finite Field Arithmetic and Reed-Solomon Coding](https://research.swtch.com/field).

### QR Codes

A QR code has a distinctive frame that help both people and computers recognize them as QR codes. The details of the frame depend on the exact size of the code--bigger codes have room for more bits--but you know one when you see it: the outlined squares are the giveaway. Here are QR frames for a sampling of sizes:

![](https://research.swtch.com/qart16.png)

The colored pixels are where the Reed-Solomon-encoded data bits go. Each code may have one or more Reed-Solomon blocks, depending on its size and the error correction level. The pictures show the bits from each block in a different color. The L encoding is the lowest amount of redundancy, about 20%. The other three encodings increase the redundancy, using 38%, 55%, and 65%.

![](https://research.swtch.com/qart17.png)

(By the way, you can read the redundancy level from the top pixels in the two leftmost columns. If black=0 and white=1, then you can see that 00 is L, 01 is M, 10 is Q, and 11 is H. Thus, you can tell that the QR code [on the T-shirt in this picture](http://www.flickr.com/photos/johncarney/3515851216/) is encoded at the highest redundancy level, while [this shirt](http://store.xkcd.com/xkcd/#QRCodeShirt) uses the lowest level and therefore might take longer or be harder to scan.

As I mentioned above, the original message bits are included directly in the message's Reed-Solomon encoding. Thus, each bit in the original message corresponds to a pixel in the QR code. Those are the lighter pixels in the pictures above. The darker pixels are the error correction bits. The encoded bits are laid down in a vertical boustrophedon pattern in which each line is two columns wide, starting at the bottom right corner and ending on the left side:

![](https://research.swtch.com/qart18.png)

We can easily work out where each message bit ends up in the QR code. By changing those bits of the message, we can change those pixels and draw a picture. There are, however, a few complications that make things interesting.

### QR Masks

The first complication is that the encoded data is XOR'ed with an obfuscating mask to create the final code. There are eight masks:

![](https://research.swtch.com/qart19.png)

An encoder is supposed to choose the mask that best hides any patterns in the data, to keep those patterns from being mistaken for framing boxes. In our encoder, however, we can choose a mask before choosing the data. This violates the spirit of the spec but still produces legitimate codes.

### QR Data Encoding

The second complication is that we want the QR code's message to be intelligible. We could draw arbitrary pictures using arbitrary 8-bit data, but when scanned the codes would produce binary garbage. We need to limit ourselves to data that produces sensible messages. Luckily for us, QR codes allow messages to be written using a few different alphabets. One alphabet is 8-bit data, which would require binary garbage to draw a picture. Another is numeric data, in which every run of 10 bits defines 3 decimal digits. That limits our choice of pixels slightly: we must not generate a 10-bit run with a value above 999. That's not complete flexibility, but it's close: 9.96 bits of freedom out of 10. If, after encoding an image, we find that we've generated an invalid number, we pick one of the 5 most significant bits at random--all of them must be 1s to make an invalid number--hard wire that bit to zero, and start over.

Having only decimal messages would still not be very interesting: the message would be a very large number. Luckily for us (again), QR codes allow a single message to be composed from pieces using different encodings. The codes I have generated consist of an 8-bit-encoded URL ending in a # followed by a numeric-encoded number that draws the actual picture:

http://swtch.com/pjw/#123456789...

The leading URL is the first data encoded; it takes up the right side of the QR code. The error correction bits take up the left side.

When the phone scans the QR code, it sees a URL; loading it in a browser visits the base page and then looks for an internal anchor on the page with the given number. The browser won't find such an anchor, but it also won't complain.

The techniques so far let us draw codes like this one:

![](https://research.swtch.com/qart5.png)

![](https://research.swtch.com/qart6.png)

The second copy darkens the pixels that we have no control over: the error correction bits on the left and the URL prefix on the right. I appreciate the cyborg effect of Peter melting into the binary noise, but it would be nice to widen our canvas.

### Gauss-Jordan Elimination

The third complication, then, is that we want to draw using more than just the slice of data pixels in the middle of the image. Luckily, we can.

I mentioned above that Reed-Solomon messages can be XOR'ed: if we have two different Reed-Solomon encoded blocks b1 and b2 corresponding to messages m1 and m2, b1 ⊕ b2 is also a Reed-Solomon encoded block; it corresponds to the message m1 ⊕ m2. (In the notation of the [previous post](https://research.swtch.com/field), this happens because Reed-Solomon blocks correspond 1:1 with multiples of g(x). Since b1 and b2 are multiples of g(x), their sum is a multiple of g(x) too.) This property means that we can build up a valid Reed-Solomon block from other Reed-Solomon blocks. In particular, we can construct the sequence of blocks b0, b1, b2, ..., where bi is the block whose data bits are all zeros except for bit i and whose error correction bits are then set to correspond to a valid Reed-Solomon block. That set is a [basis](http://en.wikipedia.org/wiki/Basis_\(linear_algebra\)) for the entire vector space of valid Reed-Solomon blocks. Here is the basis matrix for the space of blocks with 2 data bytes and 2 checksum bytes:

1
1
1
1
1
1
1
1
1
1

1
1
1
1
1
1
1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1
1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1

The missing entries are zeros. The gray columns highlight the pixels we have complete control over: there is only one row with a 1 for each of those pixels. Each time we want to change such a pixel, we can XOR our current data with its row to change that pixel, not change any of the other controlled pixels, and keep the error correction bits up to date.

So what, you say. We're still just twiddling data bits. The canvas is the same.

But wait, there's more! The basis we had above lets us change individual data pixels, but we can XOR rows together to create other basis matrices that trade data bits for error correction bits. No matter what, we're not going to increase our flexibility--the number of pixels we have direct control over cannot increase--but we can redistribute that flexibility throughout the image, at the same time smearing the uncooperative noise pixels evenly all over the canvas. This is the same procedure as Gauss-Jordan elimination, the way you turn a matrix into row-reduced echelon form.

This matrix shows the result of trying to assert control over alternating pixels (the gray columns):

1
1
1
1
1
1
1
1
1
1

1
1
1
1
1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1

1
1
1
1

1
1
1
1
1
1
1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1
1
1

1
1
1
1
1
1
1
1

1
1
1
1

1
1
1
1

1
1
1
1

The matrix illustrates an important point about this trick: it's not completely general. The data bits are linearly independent, but there are dependencies between the error correction bits that mean we often can't have every pixel we ask for. In this example, the last four pixels we tried to get were unavailable: our manipulations of the rows to isolate the first four error correction bits zeroed out the last four that we wanted.

In practice, a good approach is to create a list of all the pixels in the Reed-Solomon block sorted by how useful it would be to be able to set that pixel. (Pixels from high-contrast regions of the image are less important than pixels from low-contrast regions.) Then, we can consider each pixel in turn, and if the basis matrix allows it, isolate that pixel. If not, no big deal, we move on to the next pixel.

Applying this insight, we can build wider but noisier pictures in our QR codes:

![](https://research.swtch.com/qart7.png)

![](https://research.swtch.com/qart8.png)

The pixels in Peter's forehead and on his right side have been sacrificed for the ability to draw the full width of the picture.

We can also choose the pixels we want to control at random, to make Peter peek out from behind a binary fog:

![](https://research.swtch.com/qart9.png)

![](https://research.swtch.com/qart10.png)

### Rotations

One final trick. QR codes have no required orientation. The URL base pixels that we have no control over are on the right side in the canonical orientation, but we can rotate the QR code to move them to other edges.

![](https://research.swtch.com/qart14.png)

### Further Information

All the source code for this post, including the web server, is at [code.google.com/p/rsc/source/browse/qr](http://code.google.com/p/rsc/source/browse/qr). If you liked this, you might also like [Zip Files All The Way Down](http://research.swtch.com/2010/03/zip-files-all-way-down.html).

### Acknowledgements

Alex Healy pointed out that valid Reed-Solomon encodings are closed under XOR, which is the key to spreading the picture into the error correction pixels. Peter Weinberger has been nothing but gracious about the overuse of his binary likeness. Thanks to both.
