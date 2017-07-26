# 3 Steps to Writing and Reading XML Files

_Captured: 2017-04-24 at 23:29 from [dzone.com](https://dzone.com/articles/writing-and-reading-xml-file?edition=292911&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-24)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

To read or write XML files, you should consider JAXB (Java Architecture for XML Binding). JAXB will convert and reconvert XML objects using marshalling (writing to XML) and unmarshalling processes.

## When and Where Do I Need to Write XML Files?

### Creating a Custom Configuration or UI File

Suppose, in a project, you need to customize the User Data for each field or configure the system's database to your standard.

### Building a Generic XML File for Documentation and Installation

Alternatively, suppose you want to a make a configuration file for all users in order to access and process their data fields.

## Your Task

Develop an XML configuration for all web users using their name, IP address, and location as their identifier.

## Solution

Step one: Create the specified POJO with an annotation for the task:
    
    
         Map<String,Long> uNameAndHashCode = new TreeMap<>();
    
    
        public void setuNameAndHashCode ( Map<String,Long> newUNameAndHcode) {

**Note**: We use the JAXB annotation for jaxbMarshaller.marshal jaxbMarshaller.unmarshal().

Now we write the created User POJO content to an XML file:
    
    
            user.uNameAndHashCode.put("Vipin Jaiswal", (long) 323783292.32323);

![JAXB \( Marshalling , Un Mashalling \)](https://amudabadmus.files.wordpress.com/2017/02/2017-02-21-at-08-42-36.png?w=736)

> _And lastly, step three: Read the created UserXML File for the task:_
    
    
                User myUser = (User) jaxbUnmarshaller.unmarshal(file);

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).
