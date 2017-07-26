# Is Protobuf 5x Faster Than JSON? (Part 1)

_Captured: 2017-04-23 at 18:50 from [dzone.com](https://dzone.com/articles/is-protobuf-5x-faster-than-json?oid=twitter&utm_content=buffer4f475&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

It is very common to see articles comparing Protobuf with JSON and claiming that Protobuf is the better choice for performance reasons. If you are switching from JSON to Protobuf just for the speed, the performance should be at least 2x times better -- otherwise, it is not worth the effort. However, the guys from DSL Platform proved that [in the Java world, it is not the case](https://blog.dsl-platform.com/improving-java-json-speed/). Protobuf Java implementation is _not_ significantly faster! The reason to use Protobuf should be the awesome cross-language schema definition for data exchange -- not a 5x performance boost.

But why? What's the catch? The DSL Platform blog does not dig into the details. There are a number of reasons that I can think of to support Protobuf being a better encoding format:

  * **Easier to bind to objects**. JSON field has strings, and comparing strings are slow.
  * **JSON is textual**; integers and floats are slow to encode and decode.
  * **There is no element size or count for the header of the body**. Parsing JSON strings, arrays, and objects will always require a sequential scan.

But drawing a conclusion from those intuitions is premature. There are also counter arguments:

  * **If most fields are strings, the performance is likely to be dominated by the string copying**, not the parsing. [In some benchmarks](https://github.com/fabienrenaud/java-json-benchmark), we can see that libraries are performing about the same. This is because the test data is set up mostly by string fields.
  * **Parsing is still sequential in the Protobuf library**. The control byte is not `[]` or `{}`, but similar branching code is still required. Parsing is essentially a slower version of memory copy, constructing an object in memory from bytes transferred from somewhere (i.e. network or disk). Removing the branching is the ultimate way to get closer to memory. Innovation like Parabix is the actual game-changer in this business. With Protobuf and JSON both being sequential, it is very hard to achieve a 5x performance boost running in the same CPU and the same core.
  * **Protobuf might be a faster format, but the library implementation might not be actually faster**. If the parser is not well optimized, so extra memory allocation or copy will slow it down.

There are a number of benchmarks listed on DSL-JSON. Some are even faster than other binary encodings. It is really counter-intuitive. There must be something missing here; it might be fast, but not _that_ fast. It turns out most benchmarks are testing object binding against the same data schema. For example, [here](https://github.com/eishay/jvm-serializers/wiki), the payload chosen is:
    
    
      required Size size = 5;       // of the image (in relative terms, provided by cnbc for example)
    
    
      required string format = 5;   //avi, jpg, youtube, cnbc, audio/mpeg formats ...

No matter how we set up a small, medium, or large payload, the benchmark is always biased. What does "medium payload" actually mean? It can mean different things for different people. So, I am playing the game differently here. There will be multiple benchmarks, each benchmark will be _extremely_ biased towards one input type so that we can know the best and worst case scenario. Then, we can know under what circumstances JSON will be significantly slower and to what extent.

Enough theories. Let's start JMH benchmarking. The candidates are:

  * **Jackson**: the de-facto Java JSON parser. Used as a baseline, the others will be compared against this.
  * **DSL-JSON**, the fastest JSON Java implementation.
  * **Jsoniter**, [my humble copy of DSL-JSON](http://jsoniter.com/). (Disclaimer: I am the author of Jsoniter library. Any number mentioned here about Jsoniter should not be trusted. Most performance optimization is copied from DSL-JSON.)
  * **Protobuf**, a very popular binary encoding format used in RPC (remote procedural call).
  * **Thrift**, another popular binary encoding format used in RPC. The protocol benchmarked is TCompactProtocol.

## Decode Integer

[The integer](https://github.com/json-iterator/java-benchmark/tree/master/src/main/java/com/jsoniter/benchmark/with_int) should be very fast in Protobuf.

library compared with Jackson ns/op

Protobuf
8.20
22124.431

Thrift
6.6
27232.761

Jsoniter
6.45
28131.009

DSL-Json
4.48
40472.032

Jackson
1
181357.349

This benchmark is not all about integers. It only has one field, so the cost of integer parsing might not be the dominating factor. So, [we expand the test to 10 integer fields](https://github.com/json-iterator/java-benchmark/tree/master/src/main/java/com/jsoniter/benchmark/with_10_int_fields) and try again:

library compared with Jackson ns/op

Protobuf
8.51
71067.990

Thrift
2.98
202921.616

Jsoniter
3.22
187654.012

DSL-Json
1.43
422839.151

Jackson
1
604894.752

Protobuf is more than 8x faster than Jackson and more than 2.6x faster than Jsoniter for integer decoding. Yes, Protobuf is faster.

[The optimization used by DSL-JSON is here](https://github.com/ngs-doo/dsl-json/blob/master/library/src/main/java/com/dslplatform/json/NumberConverter.java).
    
    
    private static int parsePositiveInt(final byte[] buf, final JsonReader reader, final int start, final int end, int i) throws IOException {
    
    
        for (; i < end; i++) {
    
    
            final int ind = buf[i] - 48;
    
    
            value = (value << 3) + (value << 1) + ind;
    
    
                throw new IOException("Integer overflow detected at position: " + reader.positionInStream(end - start));

Scan the integer directly from bytes `value = (value << 3) + (value << 1) + ind;`. Compared to `Integer.valueOf` , this only scans the bytes once, and avoids memory allocation.

Jsoniter unrolled the loop:
    
    
    int ind2 = intDigits[iter.buf[i]];
    
    
    int ind3 = intDigits[iter.buf[++i]];
    
    
    int ind4 = intDigits[iter.buf[++i]];
    
    
        return ind * 100 + ind2 * 10 + ind3;

## Encode Integer

What about encoding? For the same 10 integer fields object, the results are:

library compared with Jackson ns/op

Protobuf
2.9
121027.285

Thrift
0.17
2128221.323

Jsoniter
2.02
173912.732

DSL-Json
2.18
161038.645

Jackson
1
351430.048

Thrift serialization is particular slow, which is confirmed in multiple independent benchmarks. I guess it is more about the implementation than the format. Protobuf is about 3x faster than Jackson and 1.33x faster than DSL-JSON for integer encoding. Protobuf is not significantly faster here.

[The optimization used by DSL-JSON is here](https://github.com/ngs-doo/dsl-json/blob/master/library/src/main/java/com/dslplatform/json/NumberConverter.java).
    
    
    private static int serialize(final byte[] buf, int pos, final int value) {
    
    
                for (int x = 0; x < MIN_INT.length; x++) {
    
    
                    buf[pos + x] = MIN_INT[x];
    
    
            pos += writeFirstBuf(buf, DIGITS[i], pos);
    
    
            int off = writeFirstBuf(buf, v2, pos);
    
    
            writeBuf(buf, v1, pos + off);
    
    
            pos += writeFirstBuf(buf, DIGITS[q2], pos);
    
    
            final int r3 = (int) (q2 - q3 * 1000);
    
    
            buf[pos++] = (byte) (q3 + '0');

The idea is to write out integers every 1,000. For example, 19,823 will be 19 and 823. The look-up table `DIGITS` will map 19 to "19" and 823 to "823". The ascii string "823" is bit packed into an integer and is then unpacked in `writeBuf`.
    
    
    private static void writeBuf(final byte[] buf, final int v, int pos) {
    
    
    buf[pos] = (byte) (v >> 16);
    
    
    buf[pos + 1] = (byte) (v >> 8);

This implementation is faster than JDK `Integer.toString`. It is faster because the lookup table is generated statically and the runtime calculation work is less.

## Decode Double

library compared with Jackson ns/op

Protobuf
13.75
92447.958

Thrift
7.30
174052.307

Jsoniter
3.13
406471.628

DSL-Json
2.53
502287.602

Jackson
1
1271311.735

Protobuf is more than 13x faster than Jackson and more than 4x faster than Jsoniter for double decoding. There is no doubt. JSON is unfit for float numbers.

[The optimization used by DSL-JSON is here](https://github.com/ngs-doo/dsl-json/blob/master/library/src/main/java/com/dslplatform/json/NumberConverter.java).
    
    
    private static double parsePositiveDouble(final byte[] buf, final JsonReader reader, final int start, final int end, int i) throws IOException {
    
    
            final int ind = buf[i] - 48;
    
    
            value = (value << 3) + (value << 1) + ind;
    
    
                return parseDoubleGeneric(reader.prepareBuffer(start), end - start, reader);
    
    
                final int ind = buf[i] - 48;
    
    
                div = (div << 3) + (div << 1);
    
    
                value = (value << 3) + (value << 1) + ind;
    
    
                    return parseDoubleGeneric(reader.prepareBuffer(start), end - start, reader);

The number is read into `long`, then divided by a power of 10. If the input is 3.1415, it will be 31,415/10,000.

Double is even harder encode into a textual format.

library compared with Jackson ns/op

Protobuf
12.71
143346.157

Thrift
0.87
2093533.015

Jsoniter (only 6 digit precision)
6.5
280252.226

DSL-Json
1.23
1483965.621

Jackson
1
1822478.053

Protobuf is about 13x faster than Jackson for double encoding. If you are willing to sacrifice the precision, Jsoniter has the option to only keep 6 digits. In this case, Protobuf is 2x faster than Jsoniter.

The implementation to keep 6 digits turns double encoding to long value encoding:
    
    
    long lval = (long)(val * exp + 0.5);
    
    
    if (stream.buf.length - stream.count < 10) {
    
    
    for (int p = precision - 1; p > 0 && fval < POW10[p]; p--) {
    
    
        stream.buf[stream.count++] = '0';
    
    
    while(stream.buf[stream.count-1] == '0') {

This concludes the numeric part. We can see JSON is not designed for numbers. If you are using Jackson, switching to Protobuf can give you a 10x performance boost for numbers -- both encoding and decoding. However, DSL-JSONson is able to cut the performance difference down to 3x~4x for decoding, and 1.3x~2x for encoding (with an imprecise double).

Stay tuned for next time, when we'll dive deeper into concepts like decoding objects, encoding integer lists, and more.

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).
