# Software Design Principles

_Captured: 2018-02-07 at 19:32 from [dzone.com](https://dzone.com/articles/software-design-principles?edition=358124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-07)_

[Learn how](https://dzone.com/go?i=268439&u=http%3A%2F%2Falm.parasoft.com%2Flaser-focus-your-testing-with-change-based-testing%3Futm_campaign%3DImpact%252520of%252520Change%2525202018%26utm_source%3DDZone%26utm_medium%3DDZone%252520Java%252520Partner%252520Resources) to stop testing everything every sprint and only test the code you've changed. Brought to you by Parasoft.

Software design has always been the most important phase in the development cycle. The more time you put into designing a resilient and flexible architecture, the more time will save in the future when changes arise.

Requirements always change -- software will become legacy if no features are added or maintained on regular basis -- and the cost of these changes are determined based on the structure and architecture of the system. In this article, we'll discuss the key design principles that help in creating easily maintainable and extendable software.

## A Practical Scenario

Suppose that your boss asks you to create an application that converts Word documents to PDFs. The task looks simple -- all you have to do is to look up a reliable library that converts Word documents to PDFs and plug it in inside your application. After doing some research, say you ended up using the _Aspose.words_ framework and created the following class:
    
    
            com.aspose.words.Document wordDocument = new com.aspose.words.Document(input);

Life is easy and everything is going pretty well!

### Requirements Change, as Always

After a few months, some client asks you to support Excel documents as well. So you did some research and decided to use _Aspose.cells_. Then, you go back to your class, add a new field called _documentType,_ and modify your method like the following:
    
    
                com.aspose.words.Document wordDocument = new com.aspose.words.Document(input);

This code will work perfectly for the new client (and will still work as expected for the existing clients), but some bad design smells are starting to appear in the code. That means we're not doing this the perfect way, and we will not be able to modify our class easily when a new document type is requested.

  1. **Code repetition:** As you see, similar code is being repeated inside the if/else block, and if we managed, someday, to support different extensions, then we will have a lot of repetitions. Also, if we decided later on, for example, to return a file instead of byte[], then we have to make the same change in all the blocks.
  2. **Rigidity:** All the conversion algorithms are being coupled inside the same method, so there is a possibility that, if you change some algorithm, others will be affected.
  3. **Immobility:** The above method depends directly on the _documentType_ field. Some clients will forget to set the field before calling _convertToPDF()_, so they will not get the expected result. Also, we're not able to reuse the method in any other project because of its dependency on the field.
  4. **Coupling between the high-level module and the frameworks:** If we decide later on, for some purpose, to replace the Aspose framework with a more reliable one, we will end up modifying the whole _PDFConverter_ class -- and many clients will be affected.

### Doing It the Right Way

Normally, developers are not able to predict future changes, so most would implement the application exactly as we implemented it the first time. However, after the first change, the picture becomes clear that similar future changes will arise. So, instead of hacking it with an if/else block, good developers will do it the right way in order to minimize the cost of future changes. So, we create an abstract layer between our exposed tool _(PDFConverter)_ and the low-level conversion algorithms, and we move every algorithm into a separate class as follows:
    
    
            com.aspose.words.Document wordDocument = new com.aspose.words.Document(input);
    
    
        public byte[] convertToPDF(Converter converter, byte[] fileBytes) throws Exception {

We force the client to decide which conversion algorithm to use when calling _convertToPDF()_.

## What Are the Advantages of Doing It This way?

  1. **Separation of concerns (high cohesion/low coupling)**: The _PDFConverter_ class now knows nothing about the conversion algorithms used in the application. Its main concern is to serve the clients with the various conversion features regardless how the conversion is being done. Now that we're able to replace our low-level conversion framework, no one would even know as long as we're returning the expected result.
  2. **Single responsibility:** After creating an abstract layer and moving each dynamic behavior to a separate class, we actually removed the multiple responsibilities that the _convertToPDF()_ method previously had in the initial design. Now it just has a single responsibility, which is delegating client requests to the abstract conversion layer. Also, each concrete class of the _Converter_ interface has now a single responsibility related to converting some document type to a PDF. As a result, each component has one reason to be modified, hence no regressions.
  3. **Open/Closed application:** Our application is now opened for extension and closed for modification. Whenever we want to add support for some document type, we just create a new concrete class from the _Converter_ interface and the new type will become supported without the need to modify the _PDFConverter_ tool, since our tool now depends on abstraction.

## Design Principles Learned From This Article

The following are some best design practices to follow when building your application's architecture.

  1. Divide your application into several modules and add an abstract layer at the top of each module.
  2. Favor abstraction over implementation: Always make sure to depend on the abstraction layer. This will make your application open for future extensions. The abstraction should be applied on the dynamic parts of the application _(_which are most likely to be changed regularly_)_ and not necessarily on every part, since it complicates your code in case of overuse.
  3. Identify the aspects of your application that vary and separate them from what stays the same.
  4. Don't repeat yourself: Always put duplicate functionalities in some utility class and make it accessible through the whole application. This will make your modification a lot easier.
  5. Hide low-level implementation through the abstract layer: Low-level modules have a very high possibility to be changed regularly, so separate them from high-level modules.
  6. Each class/method/module should have one reason to be changed, so always give a single responsibility for each of them in order to minimize regressions.
  7. Separation of concerns: Each module knows what another module does, but it should never know how to does it.

[Get the top tips](https://dzone.com/go?i=268440&u=http%3A%2F%2Falm.parasoft.com%2Fget-unit-testing-done-right%3Futm_campaign%3DUTA%2525202018%26utm_source%3DDZone%26utm_medium%3DDZone%252520Java%252520Partner%252520Resources) for Java developers and best practices to overcome common challenges. Brought to you by Parasoft.

Topics:

design principles ,java ,single responsibility principle ,dry principle ,refactoring ,abstraction ,tutorial
