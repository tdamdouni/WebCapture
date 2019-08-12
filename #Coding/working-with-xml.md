# Working With XML

_Captured: 2018-09-16 at 14:20 from [dzone.com](https://dzone.com/articles/working-with-xml?edition=397196&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-15)_

[Jumpstart your Angular applications with Indigo.Design,](https://dzone.com/go?i=306554&u=https%3A%2F%2Fwww.infragistics.com%2Fproducts%2Findigo-design%3Futm_source%3Ddzone%26utm_medium%3Dcpc%26utm_term%3Dtext1%26utm_campaign%3Dindigo) a unified platform for visual design, UX prototyping, code generation, and app development.

Hi all. In this post, I will share some basic information that will help you work with an XML file. The first thing to know about XML in Scala is that Scala can process XML literals, so you don't need to have any specific dependencies for working with XML. You can directly put the whole XML file into the Scala REPL and Scala will automatically interpret it as XML.

So let's do some basic examples to get an understanding of how to play with XML.
    
    
    scala> val foo = <foo><bar type="greet">hi</bar><bar type="count">1</bar><bar type="color">yellow</bar></foo>
    
    
    foo: scala.xml.Elem = <foo><bar type="greet">hi</bar><bar type="count">1</bar><bar type="color">yellow</bar></foo>

So if you want to retrieve the values of each tag then you can use:

So here you can see I just applied `.text` on `foo` and it gave me the text values of each XML tag without any spaces.

If you want to retrieve the value of the `bar` tag, then, in that case, you can use the `\` selector and tag name like this:
    
    
    res1: scala.xml.NodeSeq = NodeSeq(<bar type="greet">hi</bar>, <bar type="count">1</bar>, <bar type="color">yellow</bar>)

So here you can see the output is a `NodeSeq`, which is the sequence of the XML tags that has the name bar.

And if you want to access the value of each XML tag that is `res1`, then you can apply a map over it and can take the text value of every tag like so:
    
    
    scala> (foo \ "bar").map(_.text)
    
    
    res2: scala.collection.immutable.Seq[String] = List(hi, 1, yellow)

Some of you have queries about how to find out the value of tag that has the property type or how to retrieve the XML tag on the basis of property. So, in this example, you can see that the `bar` tag has the property "`type`" so you can do the following:
    
    
    scala> (foo \ "bar").map(_ \ "@type")
    
    
    res3: scala.collection.immutable.Seq[scala.xml.NodeSeq] = List(greet, count, color)

Note that the `\` selector can only retrieve children of the node. If you want to deep search for the specific node or want to select all nodes, you have to use the `\\\` selector.
    
    
     <title>Yahoo! Weather - Boulder, CO</title>
    
    
     <title>Conditions for Boulder, CO at 2:54 pm MST</title>
    
    
     <forecast day="Thu" date="10 Nov 2011" low="37" high="58" text="Partly Cloudy" 

Suppose that you want to retrieve the `title` XML tag and you tried this:

So here the result is a blank `NodeSeq()` because, in this operation, it found its child XML tag which is "`channel`" not a "`title`" and did not check further child of "`channel`" that's why it's giving us a black `NodeSeq()`.

But if you use `\\\` selector so it will be like this:
    
    
    res5: scala.xml.NodeSeq = NodeSeq(<title>Yahoo! Weather - Boulder, CO</title>, <title>Conditions for Boulder, CO at 2:54 pm MST</title>)

Here you can see it's giving you all the results that have the XML tag "`title`." Basically, the `\\\` selector is used for deep searches.

I hope this post will make it easy to work with XML files.

[Take a look at the Indigo.Design sample applications](https://dzone.com/go?i=306555&u=https%3A%2F%2Fwww.infragistics.com%2Fproducts%2Findigo-design%3Futm_source%3Ddzone%26utm_medium%3Dcpc%26utm_term%3Dtext1%26utm_campaign%3Dindigo) to learn more about how apps are created with design to code software.
