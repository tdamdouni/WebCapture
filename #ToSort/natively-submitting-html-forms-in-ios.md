# Natively Submitting HTML Forms in iOS

_Captured: 2017-05-23 at 03:51 from [dzone.com](https://dzone.com/articles/natively-submitting-html-forms-in-ios?edition=299094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-22)_

HTML forms are a common means of uploading information to a web server. For example, the HTML 5 specification includes a [sample form](http://www.w3.org/TR/html5/forms.html#writing-a-form's-user-interface) that simulates a pizza delivery request. The form allows the user to provide contact information, pizza size and topping details, and delivery instructions.

A working implementation of this form can be found on [httpbin.org](https://httpbin.org/forms/post). Submitting the form produces a JSON response that simply echoes the information sent with the request. However, in most "real world" applications, a form submission typically triggers some meaningful action on the server, such as posting a message, responding to a survey, or making a purchase.

Mobile applications often need to perform similar tasks. While it is possible to embed an HTML form in a native application using a web view, this is not always ideal. For example, the form may not be optimized for a mobile device, resulting in controls that are too small and difficult to interact with. Further, embedded forms don't generally provide the seamless experience users expect from a native application. They often look out of place, making it obvious that the app is not truly native:

![](https://gkbrown.files.wordpress.com/2017/05/html_form.png?w=700)

A form constructed with native controls is usually more visually consistent with platform conventions and much easier to interact with. For example:

![](https://gkbrown.files.wordpress.com/2017/05/native_form.png?w=700)

However, many native forms are processed via some form of custom XML or JSON-based web service API. This represents a duplication of effort, since developers need to support both the form processing code as well as the code for implementing the web service. It would be ideal if the server-side logic could be shared by both clients, reducing overall development effort while preserving the enhanced user experience provided by the native UI.

## MarkupKit

[MarkupKit](https://github.com/gk-brown/MarkupKit) is an open-source framework for simplifying development of native iOS and tvOS applications. It allows developers to construct user interfaces declaratively using a human-readable, HTML-like markup language, rather than visually using Interface Builder or programmatically in code.

For example, the following markup creates an instance of `UILabel` and sets the value of its `text` property to "Hello, World!":

This markup is equivalent to the following Swift code:

The native form shown in the previous section was created using the following markup. It declares a static table view whose contents represent the elements of the delivery request form:
    
    
            <UITextField id="emailTextField" placeholder="Email Address" keyboardType="emailAddress"/>
    
    
        <UITableViewCell textLabel.text="Bacon" value="bacon"/>
    
    
            <UIDatePicker id="deliveryDatePicker" datePickerMode="time" height="140"/>
    
    
            <UITextView id="commentsTextView" height="140" textContainerInset="4" textContainer.lineFragmentPadding="0"/>

Of course, MarkupKit isn't the only way to create native forms in iOS; however, it can significantly simplify the task.

## HTTP-RPC

[HTTP-RPC](https://github.com/gk-brown/HTTP-RPC) is an open-source framework for simplifying development of REST applications. It allows developers to access REST-based web services using a convenient, RPC-like metaphor while preserving fundamental REST principles such as statelessness and uniform resource access.

The project currently includes support for consuming web services in Objective-C/Swift and Java (including Android). It provides a consistent, callback-based API that makes it easy to interact with services regardless of target device or operating system.

For example, the following code snippet shows how a Swift client might access a simple web service that returns a friendly greeting:

While HTTP-RPC is often used to access JSON-based REST APIs, it also supports posting data to the server using the `application/x-www-form-urlencoded` MIME type used by HTML forms.

For example, the following view controller uses the iOS HTTP-RPC client to submit the contents of the form from the previous section to the test service at [httpbin.org](https://gkbrown.org/2017/05/19/natively-submitting-html-forms-in-ios/httpbin.org). The actual form submission is performed in the `submit()` method using HTTP-RPC's `WSWebServiceProxy` class:

While the example controller simply displays a success or failure message in response to the form submission, an actual application might do something slightly more sophisticated, such as presenting a confirmation page returned by the server.

As with MarkupKit, HTTP-RPC isn't strictly required, but its built-in support for executing URL-encoded form posts makes it a good option.

## Summary

This article provided an overview of how MarkupKit and HTTP-RPC can be used to natively submit HTML forms in iOS, reducing development effort and improving user experience.

For more information, please see the following:
