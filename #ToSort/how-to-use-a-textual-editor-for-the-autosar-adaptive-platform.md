# How to use a textual editor for the Autosar Adaptive Platform

_Captured: 2017-04-13 at 22:33 from [blogs.itemis.com](https://blogs.itemis.com/en/how-to-use-a-textual-editor-for-the-autosar-adaptive-platform?utm_source=hs_email&utm_medium=email&utm_content=50499857&_hsenc=p2ANqtz--Rbk6hx59H4VWOXc3LPCgHHb8Sp7Hj3O6GhZmKrv-1akrG23417rPZ_XwdbXbqkpWZWv2iL9dj3yi0KXWrLc-NihfiQC51Yh9Qhwh_h5d5CINkykg&_hsmi=50498919)_

AUTOSAR is about to release its new specification for the [Autosar Adaptive Platform](https://www.autosar.org/standards/adaptive-platform/). According to AUTOSAR, the difference to classic AUTOSAR is:

_"In comparison to the AUTOSAR Classic Platform the AUTOSAR Runtime Environment for the Adaptive Platform dynamically links services and clients during runtime."_

To support the specification of adaptive applications, AUTOSAR's meta-model is currently being extended by AUTOSAR working groups. Finally, this will result in an updated version of the Autosar Tool Platform (Artop), that supports these meta-model elements. Several companies have already built in-house-versions of Artop that support the current work-in-progress versions of the adaptive AUTOSAR meta-model.

![textual-editor-autosar-adaptive-platform.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Automotive/textual-editor-autosar-adaptive-platform.jpg?t=1492099761217&width=362&height=208&name=textual-editor-autosar-adaptive-platform.jpg)

## New editors are necessary

To work with the new meta-model, projects need new editors - because editing AUTOSAR XML-files is cumbersome. We are using a textual, generic [Xtext](https://www.itemis.com/en/xtext/) based editor, that we developed for project Sphinx and extended considerably within the scope of customer projects.

It is a generic Xtext-based editor, that can work with any EMF model. It has a common core and can be extended through Eclipse plugin.xmls to support content assist, highlighting etc. for different meta-models. It also supports nice syntax for any named elements and typed elements. (NOTE: If you are familiar with the standard ecore->Xtext transformation, provided by Xtext, this is a different approach. Our approach provides a much neater syntax and supports many meta-models with a single grammar and only one Xtext project/plugin).

Since we are not allowed to show any adaptive AUTOSAR models before the specification is officially released, here is a simple example of this notation based on classic AUTOSAR:

![2017-03-16_09h58_12.png](https://blogs.itemis.com/hs-fs/hubfs/2017-03-16_09h58_12.png?t=1492099761217&width=362&height=151&name=2017-03-16_09h58_12.png)

In line 1, we specifiy the meta-model that we want to use (AUTOSAR). If you would have any other meta-model, based on Eclipse EMF, you could just specify that here and get an editor for that language.

Note in line 5, we just specify the name directly after the "application-sw-component-type". With the classic ecore->Xtext import, this would be an attribute of its own and thus clutter the syntax. Same with the type in line 6.

Of course you will get all the benefits of Xtext, such as content assist, highlighting, hyperlinks, type checks. etc.

Upon saving, the file is automatically converted and saved as .arxml, so that it can be used for tools that work with AUTOSAR xml.

## Generic approach for any EMF-metamodel

If you have been following Artop for a while, you might also have come across the ARText project, which seems to be in hibernation right now. Our approach differs from ARText, since ARText is specifically for AUTOSAR and introduces a custom version of the concepts in AUTOSAR and maps AUTOSAR elements to ARText elements in a complex way. Our approach is generic and directly uses any EMF-metamodel (in our case AUTOSAR), but additionaly introduces grammatical short-cuts for often used meta-model concepts, such as named or typed elements.

We plan to publish the framework as part of Eclipse Sphinx, providing a common textual editor support for all meta-models. For legal reasons, our internal extensions, that make the experience even nicer with AUTOSAR models, could only be released as part of the Artop project.

If you're interested in more information about Xtext don't hesitate to contact our team.
