# What is continuous integration (CI)?

_Captured: 2015-10-05 at 21:34 from [mariolucero.cl](http://mariolucero.cl/extreme-programming/what-is-continuous-integration-ci/)_

**Continuous integration (CI)** is a software engineering practice in which isolated changes  
are immediately tested and reported on when they are added to a larger code base. The goal  
of CI is to provide rapid feedback so that if a defect is introduced into the code base, it can be  
identified and corrected as soon as possible. Continuous integration software [tools](http://mariolucero.cl/tools/) can be used  
to automate the testing and build a document trail.

![jenkins-plugin-diagram-saci](http://mariolucero.cl/wp-content/uploads/2014/03/jenkins-plugin-diagram-saci-300x162.png)

Continuous integration has evolved since its conception. Originally, a daily build was the standard.  
Now, the usual rule is for each team member to submit work on a daily (or more frequent) basis and  
for a build to be conducted with each significant change. When used properly, continuous integration  
provides various benefits, such as constant feedback on the status of the software. Because CI detects  
deficiencies early on in development, defects are typically smaller, less complex and easier to resolve.

![Continuous Integration: Improving Software Quality and Reducing Risk](http://ecx.images-amazon.com/images/I/51EiswnBCBL.jpg)

> _[Continuous Integration: Improving Software Quality and Reducing Risk](http://www.amazon.com/gp/product/0321336380?ie=UTF8&linkCode=as2&camp=1634&creative=6738&tag=-&creativeASIN=0321336380)_

According to Paul Duvall, co-author of _Continuous Integration: Improving Software Quality and _  
_Reducing Risk_, best practices of CI include:

  * Committing code frequently.
  * Categorizing developer tests.
  * Using a dedicated integration build machine.
  * Using continuous feedback mechanisms.
  * Staging builds.

CI originated from within the [extreme programming](http://mariolucero.cl/agile-points/extreme-programming/) paradigm, but the principles can be applied to any iterative programming model, such as agile programming. Traditional development approaches, such as the waterfall model can benefit from using CI methods for the construction stage.

To conclude, you should not say that you are doing CI only because you are using Jenkins (to mention one of the most well know Software)!!!
