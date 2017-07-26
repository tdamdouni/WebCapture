# Architecture Erosion in Agile Development

_Captured: 2017-04-08 at 15:32 from [lattix.com](http://lattix.com/blog/2017/03/31/architecture-erosion-agile-development?ref=quuu&utm_content=bufferf4518&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Software architecture erosion refers to the gap between the planned and actual architecture of a software system as observed in its implementation.1

Architecture erosion is a common and recurring problem faced by agile development teams. Unfortunately, the process of solving this problem is usually ad hoc or very manual, without adequate visibility at the architecture level. One effective solution is the reflexion model technique. The technique is a lightweight way of comparing high-level architecture models with the actual source code implementation while also specifying and checking architectural constraints.

The diagram below is an example of the reflexion model technique.

![Agile Architectural Analysis](http://lattix.com/files/images/products/ArchitecturalAnalysisPic.jpg)

Architecture erosion can result in lower quality, increased complexity, and harder-to-maintain software. As these changes happen, it becomes more and more difficult to understand the originally planned software architecture. This is particularly important in an agile environment where, according to the [Agile Manifesto](http://agilemanifesto.org/), working software is valued over comprehensive documentation and responding to change is valued over following a plan. In reality, this means that the architecture is evolving as the software is evolving. Therefore, software changes need special attention (architectural assessment) from software architects. If this does not happen, the architecture could erode or become overly complex. Uncontrolled growth of a software system can lead to architectural issues that are difficult and expensive to fix.

#### How to avoid architecture erosion

Architecture erosion can be avoided or corrected by continuously monitoring and improving the software. Continuous checking of the implemented architecture against the intended architecture is a good strategy for detecting software erosion. Once architectural issues have been found, refactoring should be used to fix them. In an agile environment, you should combine development activities with lightweight [continuous architectural improvement](https://www.amazon.com/Agile-Software-Architecture-Refactoring-Architectures-ebook/dp/B019ZU07WQ) to avoid or reverse architecture erosion. The process of continuous architectural improvement can be broken down into four steps:

  1. Architecture assessment
    1. Identify architectural smells and design problems
    2. Create a list of identified architectural issues
  2. Prioritization
    1. Decide the order in which the architectural issues will be tackled starting with strategic design issues or high-importance requirements first
  3. Selection
    1. Choose the appropriate [refactoring pattern](https://sourcemaking.com/) to fix the issue. If none exist create your own. 
  4. Test
    1. Make sure the behaviors of the system did not change
    2. Update the architecture assessment to make sure you fixed the design problems and did not introduce new issues. Watch the [Lattix Update Feature](https://www.youtube.com/watch?v=iHU_W4wJY5w&t=340s) video for more information on this step. 

This is particularly useful in agile development. In a scrum environment, architecture refactoring should be integrated into sprints by adding time for refactoring both code and architecture. During the sprint, architects need to check their architecture, while testers and product owners should validate the system still meets requirements. Architecture refactoring should be done once during a sprint as opposed to code refactoring, which should be done daily. If it is done less often, fixing architectural issues involves more time and complexity as more code changes are added on top of design issues. If done more often, the architecture could change needlessly and add to software complexity. Architectural problems not solved in a current sprint should be saved and maintained in a backlog.

#### Summary

Architecture erosion can happen in any software project where the architectural assessments are not part of the development process. Architectural refactoring makes sure wrong or inappropriate decisions can be detected and eliminated early. One of the principles of agile development is "[maintain simplicity."](http://csis.pace.edu/~marchese/CS389/L3/Ch3_summary.pdf) Focus on simplicity in both the software being developed and in the development process. Whenever possible, actively work to eliminate complexity from the system. A clean architecture eliminates complexity from the software while a lightweight, reflexion technique compliant tool like [Lattix Architect](http://lattix.com/lattix-architect) makes the process of continuous architecture improvement simple.

1\. [Terra, R., M.T. Valente, K. Czarnecki, and R.S. Bigonha, "Recommending Refactorings to Reverse Software Architecture Erosion", 16th European Conference on Software Maintenance and Reengineering, 2012](http://gsd.uwaterloo.ca/sites/default/files/Full%20Text.pdf)
