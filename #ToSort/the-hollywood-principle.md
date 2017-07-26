# The Hollywood Principle

_Captured: 2017-05-25 at 10:21 from [dzone.com](https://dzone.com/articles/the-hollywood-principle?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

The Hollywood Principle says:

![Hollywood.jpg](https://lh3.googleusercontent.com/60NpYzzxYr4v60JZTR9c__o-7bABBoYI1ff9ancTw42FYlS6MKsWjjyXpMPlQ8g1LzTJ0uVKQMcKvRioCuswfkKMKFoWUKQg23zCQTZJ0-ruGQ1uMJNKDPv-gxV-W5ufHNTIG4ii)

This little sentence opens up a new viewpoint in software. This is one of the important principles every developer should know. In this article, we will try to discuss it.

## "Don't Call Us, We'll Call You": What Does it Mean?

In layman terms, you don't have to bother about when your turns come. When your turns come, they will call you.

But what do "you" and "they" denote here?

To explain "you" and "they" in technical terms, first we need to understand how software design works. When we design a software, we try to implement two things.

  * API

  * Framework

### API

An API is used to publish some methods/functions, so the caller/user of the API calls this method to get some useful information. So, the caller does not have any action points to take -- only call methods and outputs.

### Framework

The framework is a little bit more critical than the API. The framework is maintaining an algorithm, but it expects the value to be produced by the caller of the framework. To put it simply, the framework takes the strategy or business implementation from the caller and calls it when required.

With the Hollywood Principle, we can feed our strategy or business implementation, denoting the framework engine/implementation, which calls the fed strategy when required.

## Real-Life Example

**Spring DI:** Think about Spring, where we declare beans in XML, and Spring containers call these beans to create Spring beans. We inject other beans into it, returning a fully configured bean. So with the help of XML, we feed the strategy, and the Spring container calls them when required. We often call it Dependency Injection. In fact, you might also know the Hollywood Principle by another name: IoC (Inversion of Control).

**Struts 1.x:** Pay attention to the Struts 1.x implementation, where the caller of Struts extends ActionClass and provides business implementations in the Action class. The Struts framework calls those Action classes based on the URL mentioned in Struts config file. So here, the Action class is the strategy, and the Struts framework invokes it.

**Observer pattern/Listener in Swing:** Think about Swing's actionListener. We subscribe to an event, like button click on Blur, and when this event occurs, Swing calls our code written in the actionPerformed method.

Apart from this, a **servlet/EJB** maintains lifecycles, so the underlying server calls the appropriate lifecycle method when the servlet or EJB state is changed.

We call those methods **Callback** methods because the framework calls this method. We don't have to call them, but we may provide the implementations of those methods if we want to push some strategies in the framework.

## Use Case

Say Cognizant has a resume upload portal where job seekers upload their resumes. When the company does some on-campus recruiting, Cognizant will call them by sending an email to their inbox.

We can implement the same thing via the Hollywood principle. Job seekers upload their resumes in the job portal, and Cognizant sends mail to them when an on-campus event occurs.

**Cognizant says: Don't call me, I will call you.**

![Hollywood \(2\).jpg](https://lh3.googleusercontent.com/TXSKYeY-9YSsetnQlIMvOcsSmIZUPUJFjmfchTkVn6fEqAPXs7Po7CxJihtR9ZxSVkkYzPzvW1ijEX_NVaSCS1pwLGaQkN9hDqH2w80XMRZsJ0UtEsUdjl5B93hCRIWPMEeMB9Vd)

> _Let see the implementation._

### Assumption

Here, I have not introduced any interface for the sake of simplicity, and I've not added any complex scenario like a priority, reset, GroupWise mail sending, etc., as I just wanted to show how the Hollywood Principle works.
    
    
            return "Resume [email=" + email + ", name=" + name + ", content=" + content + "]";
    
    
        private List<Resume> resumeList = new ArrayList<Resume>();
    
    
        public void uploadContent(String mail ,String name,String content)
    
    
                System.out.println("Sending mail to " + resume.getName() + " at " + resume.getEmail());

### Output

Please note that in the CognizantJobPortal class, I maintain a list where uploaded resumes are added. When Cognizant triggers a campusing, the job portal/framework sends the mail to all job seekers who uploaded a CV to Cognizant.
