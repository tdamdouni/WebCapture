# Hello, Hexagonal Architecture

_Captured: 2017-03-10 at 19:22 from [dzone.com](https://dzone.com/articles/hello-hexagonal-architecture-1?edition=278882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-10)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

When developing software we're always craving for architecture, because we want our software be easily changed in the future.

So, architecture stepped in for maintainability. Here maintainability means how easily we can incorporate changes without disturbing the old code.

Every added feature in software comes with a risk: risk of breaking the program, maintainability, rigidity, dependencies, etc, There are many shades of risks we call **technical debt**.

**Technical debt** has an inverse relationship with **maintainability**, using architectural styles we want to decrease the risk, or I should say make it consistent when adding new features.

We experienced that when we started writing code it was easy to add features, and gradually it becomes harder to do so unless we use the proper architecture for that project.

## **Hexagonal Architecture**

In one sentence, Hexagonal Architecture says: _**The core business logic talks to other parts of the application through a contract.**_

Your software development logic should talk to other pieces, meaning the database, any JMS Queues, any Flat files, HTTP requests, FTP, etc through a contract or an interface in Java.

The benefits of this type of design is whatever the input or output, every channel has to implement the same contract/interface to talk with our software. So from our perspective all chanells are the same, as all implement the same contract so our software can deal with any types of inputs and outputs.

### **Benefits**

  1. Easily incorporates any channels like Flat file, RDBMS, NoSQL, Http, Ftp, JMS, etc.

  2. Our software can be easily tested because it is easy to create a mock when there is a need to implement the contracts.

  3. Adding new requirements means adding plugins or implementing the contracts.

  4. Proper separation of concern.

  5. Maintains IOC as higher level and lower level talking through contract.

Sometimes we called Hexagonal architecture **Port and Adapter** or **Onion **architecture. With these styles we have a port for each channel, such as a database.

The tasks we have to perform are:

  1. To implement the contract to talk with our software. As database APIs say JDBC is itself a contract, or Hibernate is itself a framework, we need to create a GOF adapter pattern where we can implement a strategy which converts JDBC-related operations to our contract-related operations.

  2. Plug this adapter into our port to talk with this channel.

## **Outline of the Design**

### **Software Contract**

This is the general contract for talking with our software. Any output channel should implement that contract.

Here I take an example of how it can talk to a JPA entity which saves that data in the database.

### **DataBaseChannelAdapter.java**

As JPA Entity uses some JPA related annotation, I did not include this JPA entity as part of our Domain. I used JPA framework as an Outside Channel of our software domain, and DataBaseChannelAdapter takes our core domain Employee Object and takes a Command Object, which tells the adapter which JPA entity to call.

### **EmployeeDomainObject**
    
    
          return "EmployeeDomainObject [name=" + name + ", address=" + address

Our core Domain Employee Object does not depend on any framework, so I can plug any framework into it through an adapter. For example, I can easily change DatabaseAdapter to FileAdepter to save our core domain object in File.

### **EmployeeCommand.java**

This Command object helps an adapter to convert a Core Domain Object to an Underlying Output channel (database or file).

### **EmployeeDomainDao.java**
    
    
    package com.example.architecture.hexagonal;
    
    
       public void save(T t,TCommand commandObject)   {
    
    
       public void delete(T t,TCommand commandObject)   {
    
    
       public IPersists<T, TCommand> getAdapter() {
    
    
       public void setAdapter(IPersists<T, TCommand> adapter) {

This is our Core Domain Persist layer. Based on the adapter, it will call the exact output channel and persist our Domain Object.

## **Time to Test Our Software Design**

### **Main.java**
    
    
    package com.example.architecture.hexagonal;
    
    
       public static void main(String[] args) {

### **Output**

#### **Hexagonal Layers **

![](https://lh5.googleusercontent.com/7kTf1V74nvHNgUnk6IeXhrgOJgd9K9cdysLhMU4XTLJpy0Kfyp7EPhAKnmKz1bwXpD1xIjyaWHM7FNvK_adxZIv5TKldV8fZm29Br86mt3QJvyLhfc9YAdTo76_N3_LFevHdih98)

_Picture courtesy Google_

**Application Domain**: As I said earlier it is the software where all software related business logic and validation goes on. This is the module that every outside module talks with through a contract.

**Application/Mediation Layer**: Kind of like a services layer, it adopts the framework layer or an outside layer and makes necessary changes according to the domain layer contract to talk with the domain layer, or in the same way return back the result from the domain to the framework layer. It sits between the domain and framework layer.

**Framework Layer:** This layer as for input/output channels, a.k.a. the outside world, and uses an adapter to adapt the data and transform it according to our software contract.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
