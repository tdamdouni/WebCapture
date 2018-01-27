# Base64 Encoding: A Visual Explanation

_Captured: 2017-11-14 at 21:14 from [dzone.com](https://dzone.com/articles/base64-encoding-a-visual-explanation?edition=334873&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-14)_

Base64 encoding appears here and there in web development. Perhaps its most familiar usage is in HTML image tags when we inline our image data (more on this later):

As a programmer, it is easy to accept this random-looking ASCII string as the "Base64 encoded" abstraction and move on. To go from raw bytes to the Base64 encoding, however, is a straightforward process, and this post illustrates how we get there. We'll also discuss some of the why behind Base64 encoding and a couple places you may see it.

## A Visualization

The gist of the encoding process is captured in the interactive CodePen linked via the image below (or [here](https://codepen.io/lewistg/pen/MEQbmB)). Type in some ASCII characters in the top input and hit the "Encode" button.

![Image title](https://dzone.com/storage/temp/7139353-visualization-preview.png)

If you run a few strings through this visualization, you may notice that the encoding process is simply a pair of nested loops. The outer loop iterates over the data in 24-bit increments; the [spec](https://tools.ietf.org/html/rfc4648) refers to these as "input groups." The inner loop iterates over each input group 6 bits at a time. Each 6-bit value is interpreted as an unsigned integer that is used to index an alphabet of 64 characters. The indexed alphabet value is the output. With the help of [ES6 generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*), this encoding process can be implemented with just a handful of functions:
    
    
       for (let group of groups24Bits(bytes)) {
    
    
          for (let value of values6Bits(group)) {
    
    
       for (let i = 0; i < bytes.length; i += 3) {
    
    
          yield bytes.slice(i, i + 3); // 3 bytes/3 octets/24 bits
    
    
       const paddedGroup = Uint8Array.from([0, 0, 0]);
    
    
       let numValues = Math.ceil((group.length * 8) / 6);
    
    
       for (let i = 0; i < numValues; i++) { let base64Value; if (i == 0) { base64Value = (paddedGroup[0] & 0b11111100) >> 2;
    
    
          } else if (i == 1) {
    
    
             base64Value = (paddedGroup[0] & 0b00000011) << 4; base64Value = base64Value | ((paddedGroup[1] & 0b11110000) >> 4);
    
    
          } else if (i == 2) {
    
    
             base64Value = (paddedGroup[1] & 0b00001111) << 2; base64Value = base64Value | ((paddedGroup[2] & 0b11000000) >> 6);
    
    
          } else if (i == 3) {
    
    
       for (let j = 0; j < numPaddingValues; j++) {

If there is an "interesting" part to the encoding process, it is the ending conditions where we must apply padding. Each input group is required to be 24 bits long (or equivalently three 8-bit bytes). (It seems likely the spec writers chose 24-bit input groups since 24 is the least common multiple of 6 and 8.) In the implementation given above, we pad the final group with bytes of zeroes when the final input group is only 1 or 2 bytes long. As we iterate over this final input group, if the 6-bit value consists entirely of padding bits, then = is the output character, the designated padding character. If, however, the 6-bit value straddles "real" bits and padding bits--as can be seen in the input "foob"--then the alphabet is still indexed and the padding bits are taken to be zeroes.

## A Couple Usages

You will not find any mention of "HTML" in the Base64 spec. Instead, the authors simply mention that Base64 encoding is used in environments where, "perhaps for legacy reasons," the "storage or transfer" of data is limited to ASCII characters. More or less, this idea sums up the browser and its heavy consumption of HTML, JSON, CSS, and JavaScript. Increasingly, this text is encoded using [UTF-8](https://jira.lucidchart.com/browse/UTF-8), a superset of ASCII. In this text-heavy ecosystem, Base64 encoding finds various niche applications.

### Data URLs

The first part of a URL is the scheme. It is the prefix string that goes before the first colon; for example, it is the https in _https://example.com_ or the beginning ftp in _ftp://ftp.funet.fi/pub/standards/RFC/rfc4648.txt_. The scheme tells the client (a browser or a different network app) how to retrieve the resource and what protocol to follow. The scheme prefix also makes URLs extensible and suitable for future protocols. If a new protocol comes along, we can create a new URL scheme for it and still identify resources by URL.

The `data` scheme is one such extension, which we saw in the image encoded in the introduction. This scheme tells clients, "My resource's data is located right here in the rest of this URL string." URLs that use the data scheme follow this format:

You can find more particulars about this format in the [spec](https://tools.ietf.org/html/rfc2397), but we will focus on the image "data URLs" we mentioned at the outset. Here are a couple examples of the big three binary image formats used in a few different contexts:

### Source Maps

Another common but less visible usage of Base64 encoding is in source maps. Below is a source map generated by Google's Closure compiler:

Here Base64 encoding is used for the mappings field. The comma and semicolon delimited snippets are the Base64 encoded binary data of integers encoded as [variable-length quantities](https://en.wikipedia.org/wiki/Variable-length_quantity) (VLQ).

Images and source maps are just a couple places Base64 encoding is used. If you know of others or any novel uses of Base64 encoding, please mention them in the comments below. It also might be worth "inspecting" page sources to find others. For example, in Chrome, if you go to `chrome://dino` you can find that the offline dinosaur game's image assets (and it appears sound assets) are Base64 encoded (examining these assets--which are also embedded on YouTube's homepage--is how I discovered the dinosaur can duck under the low-flying pterodactyls).
