# URL Encoding and Decoding Using Java

_Captured: 2017-03-26 at 19:33 from [dzone.com](https://dzone.com/articles/url-encoding-and-decoding-using-java?edition=286925&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-26)_

### If you find yourself encoding and decoding URLs often, take a look at how to do it in Java while staying on alert in case you need multiple iterations.

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

It is a common requirement to implement URL encoding and decoding in Java while creating crawlers or downloaders. This post focuses on creating modules for encoding and decoding of a passed URL. You can take a look at the [source code on GitHub](https://github.com/csanuragjain/extra/tree/master/EncodeDecodeURL).

## Main Method

###   
How It Works

  1. `url` is the variable containing the encoded URL that we want to decode.

  2. `url2` is the variable containing the URL we want to encode.

  3. We call the decode method, which decodes and prints the URL.

  4. We call the encode method, which encodes and prints url2.

## Encode Method

###   
How It Works

  1. We use the encode method of a predefined Java class named URLEncoder.

  2. The encode method of URLEncoder takes two arguments:

    1. The first argument defines the URL to be encoded.

    2. The second argument defines the encoding scheme to be used.

  3. After encoding, the resulting encoded URL is returned.

## Decode Method

###   
How It Works

  1. Because the same URL can be encoded multiple times, we need to decode it until the URL cannnot be decoded further. For example, "video%252Fmp4" is the result of two encodings. Upon decoding it once, we get "video%2Fmp4". Now the URL needs to be further decoded so that we get "video/mp4", which is the result.

  2. We use the decode method of a predefined Java class named URLDecoder.

  3. The decode method of URLDecoder takes two arguments:

    1. The first argument defines the URL to be decoded.

    2. The second argument defines the decoding scheme to be used.

  4. After decoding, the resulting decoded URL is returned.

  


  5. We create an iteration that runs until prevURL!=decodeURL

  


  


  


  6. Now, prevURL=decodeURL, so the decoded URL is returned.

## **Output**
    
    
     Decoded URL: https://r1---sn-ci5gup-cags.googlevideo.com/videoplayback?pcm2cms=yes&mime=video/mp4&pl=21&itag=22&&itag=43&type=video/webm; codecs="vp8.0, vorbis"&quality=medium  
    
    
     Encoded URL2: https%3A%2F%2Fr1---sn-ci5gup-cags.googlevideo.com%2Fvideoplayback%3Fpcm2cms%3Dyes%26mime%3Dvideo%2Fmp4%26pl%3D21%26itag%3D22%26%26itag%3D43%26type%3Dvideo%2Fwebm%3B+codecs%3D%22vp8.0%2C+vorbis%22%26quality%3Dmedium

##   
**Full Program**
    
    
          public static void main(String[] args) {  
    
    
               String url2="https://r1---sn-ci5gup-cags.googlevideo.com/videoplayback?pcm2cms=yes&mime=video/mp4&pl=21&itag=22&&itag=43&type=video/webm; codecs=\"vp8.0, vorbis\"&quality=medium";  
    
    
               System.out.println("Decoded URL: "+decodeURL);  
    
    
               System.out.println("Encoded URL2: "+encodeURL);  
    
    
                         while(!prevURL.equals(decodeURL))  
    
    
                         String encodeURL=URLEncoder.encode( url, "UTF-8" );  

I hope this helps!

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
