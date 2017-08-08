# IEC 61508: What does this standard mean for software development?

_Captured: 2017-08-04 at 22:20 from [blogs.itemis.com](https://blogs.itemis.com/en/iec-61508-what-does-this-standard-mean-for-software-development?utm_source=hs_email&utm_medium=email&utm_content=54879111&_hsenc=p2ANqtz--tINoFlL-CuruqJ_7L8hqZWb8NiOwJAuuq7qWdffcBmISI7CVRpuNXmVD-W59RHDDs9Da7MmoGj_MpVFwqbfHsKXCuxg&_hsmi=54879210)_

For more and more systems, functional safety requirements must be met. For software development, the fulfillment of IEC 61508 "Functional safety of safety-related electronic / electronic / programmable electronic systems" is to be demonstrated - especially in the automotive sector.

On the other hand, there are commercial requirements for the product which often severely limit the development budget.

The solution lies in an efficient development process, which fulfills the safety-relevant requirements and can be demonstrated by a seamless traceability. A prerequisite for the successful implementation of such a process is a thorough understanding of this standard and a clear definition and delineation of the specific terms. Let's look at the three terms "specification", "architecture" and "requirements".

## **Specification**

[Wikipedia](https://en.wikipedia.org/wiki/Specification_\(technical_standard\)) defines them as follows:

> The word _specification_ is defined as "to state explicitly or in detail" or "to be specific". A specification may refer to a type of [technical standard](https://en.wikipedia.org/wiki/Technical_standard). [...] A requirement specification is a set of documented [requirements](https://en.wikipedia.org/wiki/Requirement) to be satisfied by a material, design, product, or service."

A specification is therefore the collection of all measurable requirements (or requirements) to a product or service.

## **Requirement**

Chris Rupp and Klaus Pohl define requirements in their book "Requirements Engineering Fundamentals" as a condition or ability with different focus:

As a condition required by a user to solve a problem or achieve a goal - that is, as the WHAT of a product that can be easily documented in textual form.

As a condition that must be met by a system, for example, to meet a standard, specification, or other document. This also covers legal aspects.

As a documented condition according to item 1 or 2.

In contrast to point 1, the definitions in points 2 and 3 contain references to documents - the content of the requirements depends directly on the content of these documents. If a standard or a specification describes the architecture of a product or system, architecture itself becomes a requirement.

## **Architecture**

[Wikipedia](https://en.wikipedia.org/wiki/Software_architecture) defines software architecture as follows:

> Software architecture refers to the high level structures of a [software system](https://en.wikipedia.org/wiki/Software_system), the discipline of creating such structures, and the documentation of these structures. These structures are needed to reason about the software system. Each structure comprises software elements, relations among them, and properties of both elements and relations. The _architecture_ of a software system is a metaphor, analogous to the [architecture](https://en.wikipedia.org/wiki/Architecture) of a building. Software architecture is about making fundamental structural choices which are costly to change once implemented."

In contrast to the definition of requirements, the architecture clearly describes the HOW of a system. As a rule, they can easily be represented graphically.

## **Specification, Requirements, Architecture: These are the differences and connections**

In simplest terms, a specification defines a document that can contain both requirements and architecture. There are also cases where it is useful to describe architectural elements in requirements. Sometimes requirements are also contained in the architecture. However, these should remain special cases, since it is useful for an efficient development to consciously differentiate between requirements and architecture.

Such a deliberate distinction, of course, presents a tool-based traceability. As a rule, architectures are represented by graphical tools, while textual requirements are best managed in a database. To enable seamless traceability, the tool used must be able to work across the entire tool. One possible solution is, for example, [YAKINDU Traceability](https://www.itemis.com/en/yakindu/traceability/).

## **More about "Functional Safety"**

In the Whitepaper "Integration of functional safety in the development process of embedded systems" by itemis employees Helko Glathe and Richard Pohl, you will learn more about this topic. Download it here for free.
