# SOLID principles by example: Interface segregation

_Captured: 2017-09-22 at 13:56 from [ilclubdellesei.wordpress.com](https://ilclubdellesei.wordpress.com/2017/09/02/solid-principles-by-example-interface-segregation/)_

This post continues the analisys of the [SOLID principles ](https://ilclubdellesei.wordpress.com/2017/07/03/solid-principles-by-examples-introduction/)and it's about the Interface Segregration Principle (ISP).

## ![Screenshot_1.png](https://ilclubdellesei.files.wordpress.com/2017/09/screenshot_11.png)

## Definition

> The interface-segregation principle (ISP) states that no client should be forced to depend on methods it does not use.

## The bad example

Here we examine an interface that violates ISP:

12345678
`interface` `ISmartDevice``{``void` `Print();``void` `Fax();``void` `Scan();``}`

This interface states that a smart device is able to print, fax and scan. An implementation of this interface could be an **AllInPrinter** class:

1234567891011121314151617
`class` `AllInOnePrinter : ISmartDevice``{``public` `void` `Print()``{``// Printing code.``}``public` `void` `Fax()``{``// Beep booop biiiiip.``}``public` `void` `Scan()``{``// Scanning code.``}``}`

Simple, isn't it? Right. Now suppose we need to handle a dumb device (**EconomicPrinter** class) that can only print. We're forced to implement the Whole interface, for example:

1234567891011121314151617
`class` `EconomicPrinter : ISmartDevice``{``public` `void` `Print()``{``//Yes I can print.``}``public` `void` `Fax()``{``throw` `new` `NotSupportedException();``}``public` `void` `Scan()``{``throw` `new` `NotSupportedException();``}``}`

This is not very good.

## The good example

Here we apply the ISP and we separate the single ISmartDevice interface into 3 smaller interfaces: **IPrinter**, **IFax**, and **IScanner**.

1234567891011
`interface` `IPrinter{``void` `Print();``}``interface` `IFax{``void` `Fax();``}``interface` `IScanner{``void` `Scan();``}`

This way it's easier to implement classes that do not need to handle all the original functionalities of the ISmartDevice interface like our EconomicPrinter. Our code is more decoupled and easier to mantain. Let's re-implement our EconomicPrinter with this architecture:

12345678
`class` `EconomicPrinter : IPrinter``{``public` `void` `Print()``{``// Printing code.``}``}`

The original AllInOnePrinter now looks like this:

123456789101112131415161718
`class` `AllInOnePrinter : IPrinter, IFax, IScanner``{``public` `void` `Print()``{``// Printing code.``}``public` `void` `Fax()``{``// Beep booop biiiiip.``}``public` `void` `Scan()``{``// Scanning code.``}``}`

## TL;DR

The ISP guides us to create many _small _interfaces with coherent functionalities instead of a few _big_ interfaces with lots of different methods. When we apply the ISP, class and their dependencies communicate using focussed interfaces, minimising dependencies. Smaller interfaces are easier to implement, improving flexibility and the possibility of reuse.
