# Why low code can only be the beginning

_Captured: 2018-01-03 at 16:19 from [blogs.itemis.com](https://blogs.itemis.com/en/why-low-code-can-only-be-the-beginning?utm_source=hs_email&utm_medium=email&utm_content=59754756&_hsenc=p2ANqtz--tYRmRnArsY2sr83H6rWwTIdudlvNeW1vdPh14W_1fgcEsIz2oEzdGULrPecfdvcLY8Id84VGqlFAzteTK4K4onICZzw&_hsmi=59754756)_

Digital transformation and business agility are the buzzwords of the day, stirring up the business world. It's true, in order to survive in a rapidly changing market that can bring up different market needs and customer expectations and even new competitors on a daily basis, agility is to the rescue.

![Rakete-Hand.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Rakete-Hand.jpg?t=1514992779618&width=2172&height=1035&name=Rakete-Hand.jpg)

If [Gartner](https://www.gartner.com/doc/reprints?id=1-3W4WJDK&ct=170322) and [Forrester](https://reprints.forrester.com/#/assets/2/160/RES117623/report) are to be believed, "low code development" is the new silver bullet to make business agility happen. Indeed the market seems to grow continuously, and major players like Mendix, Outsystems, or Appian provide impressive growth rates.

## Low code development: configuration rather than coding

The idea behind it is simple: create business apps through configuration rather than coding. Configuration means that an application is specified by creating models of the data it processes, the process steps (business logic and workflows), as well as the user interface. Importantly, all of those are specified visually: entity relationship diagrams are used for data modeling, and notations based on activity-diagrams are used for the business logic and workflows. The user interface is constructed by arranging predefined widgets in a WYSIWYG-style editor.

The advantages of such an approach are obvious: the technical barrier is significantly lowered so that people without a professional software engineering background, so called "citizen developers", are now enabled to create applications without direct involvement of the IT department. While this can directly leverage the development of departmental applications, improving "internal" efficiency and reducing the need for shadow IT, it can also fuel the development of sustainable business applications, as it enables rapid prototyping through short iterations and direct feedback, instead of requiring complete, tardy production cycles.

However, even while low code development platforms do support the specification of automated workflows and usually offer various kinds of service integrations, e.g. with ERP systems or active directories, the business logic that can be captured in such applications is quite limited. Which is where the problems actually start: consider insurances. The data model, workflows, and user interface of an application that lets consumers procure and taylor insurance products are relatively straightforward. But the business logic that defines the product itself is really complicated. The price calculation alone usually is a quite complex rule-based system.

## The boundaries of low code

The answer generally given by all major low code platform vendors is to fall back to "regular" coding to capture such complex business logic, and to tie it into the system via external APIs. This is very unsatisfactory, because this forms the core of a business, and it basically stays inaccessible for users without a professional software engineering background.

If we borrow from the insurance domain once more and look at how insurance products are developed today, it gets clear that this is a serious drawback. The "modeling" of an insurance product is traditionally performed by business specialists. Tools like Microsoft Excel and Access are often used by these product modelers, augmented by more formal languages like SAS and R for data analysis. At some point, the product specification, usually a Word document, is handed over to the IT department (or even an external IT service provider), which pours it into code.

Once the product is implemented it must be validated with regards to the specification. If undesired behavior is discovered, the product modelers must understand the reasons, often requiring them to dig into code they have never seen and will likely will not understand. The whole process is time-consuming and error-prone. Each product iteration requires a complete development cycle, involving both, business experts and IT.

## Take the idea further

This is far from "agile". And it is right here at the core of the domain where the innovation is most critical and agility would be most useful: insurance products have to be continuously adapted, driven e.g. by legal changes or updated risk assessments. To be competitive, speed is a requirement. Taking the idea behind low code development further, business specialists indeed should be able to capture and validate their potentially complex business logic. Of course the required formalisms cannot be as easy as those to specify a simple workflow. [We need to extend their toolkit with something suitable](https://www.itemis.com/en/convecton), not with a toy.

Alexander works for itemis AG in Lunen, where he's responsible for leading a team of software engineers and - deputy - for the management of the head office. As a consultant and coach he advises and educates customers with respect to the application of modeling languages and the technical realization of software tools. As a project manager and software architect, he's mostly involved in the development of integrated tool-chains for the company's automotive customers. Alexander has a special interest in graphical user interface technologies and hence lead the Eclipse Graphical Editing Framework (GEF) project. He further represents itemis AG in the Eclipse Architecture Council as well as the Eclipse Planning Council.
