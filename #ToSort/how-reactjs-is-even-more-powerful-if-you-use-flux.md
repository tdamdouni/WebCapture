# How ReactJS is Even More Powerful if You Use Flux

_Captured: 2017-04-28 at 21:48 from [dzone.com](https://dzone.com/articles/how-reactjs-is-even-more-powerful-if-you-use-flux-1?oid=twitter&utm_content=buffer6abc8&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

I recently started learning ReactJS. With a very good documentation available on [GitHub](https://facebook.github.io/react), I found it very easy to learn. I created a sample application in ReactJS and it was working fine!!

With some experience in the same I would like to begin by mentioning two of its salient points:

  1. HTML and Javascript in a single file which makes it easy to maintain
  2. Component-driven Development in which DOM is divided into components to make it reusable and easily testable

Then I heard about **React with Flux** and I was intrigued to know [why do we need Flux when React is fine on its own](http://blogs.quovantis.com/how-reactjs-is-even-more-powerful-if-you-use-flux/). I did not have much development experience in ReactJS which is why I didn't realize the power of Flux. Eager to learn, I told myself let's pull our socks a little, learn Flux and also help train others.

I created an application using _ReactJS but initially didn't use Flux_ in order to understand its additional benefits like:

  1. Maintainability
  2. Readability
  3. Unidirectional data flow

**To see the same in practice, Let's take a look at developing an application first without using Flux and then using Flux.**

Let's start by understanding basic definition/architecture of Flux.

## **Flux Architecture**

![Flux Architecture](https://dzone.com/storage/temp/3205528-flux-js-01-768x432.png)

> _Flux Architecture_

There are four key points to Flux

  1. **Action:** Actions are very simple because they only need to take request from View and pass it to the Dispatcher. It acts as a mediator between View and Dispatcher.
  2. **Dispatcher:** Dispatcher is responsible for passing information to store. It does that via <this.dispatch> method in dispatcher.
  3. **Store:** Stores plays with data. It communicates with backend server as per request from View.
  4. **View:** Views are for displaying information. If views need some information then they get it from Store and if it needs to perform some action or update/add any information then it informs Action.Action calls Dispatcher which in turn fetches data from Store.

Let's say we have to create a TODO application. It would be a single page application divided into following components:

  * Header 
    * Todo Count
  * Todo Form
  * Todo List 
    * Todo Item

On browser, components would be shown as in the below diagram:

![TODO application using flux showing flux components](https://dzone.com/storage/temp/3205532-flux-js-02-768x601.png)

> _TODO application using flux showing flux components_

## **Expected Behavior**

  * Todo Count will display the total count of Todo Items.
  * Todo Form will have an input field.
  * On submitting the form, new Todo Item should be appended to Todo List and count should be increased in Todo Count.

## **Application Without Using Flux**

Let's create a TodoItem Class which will render individual todo item. It will receive information of todo item from its parent component:
    
    
              <li> { this.props.user } - { this.props.task} </li>)

The below component is TodoList which is responsible for rendering all todo items. This component gets "data" from its parent class via props. "this.props.data" is a list of items which iterates and call TodoItem which we created above.
    
    
            var TodoTasks = this.props.data.map(function(todoItem) {
    
    
                  < TodoItem user = { todoItem.user } task = {todoItem.task} key = { todoItem.id } />

TodoCount component is responsible for displaying the count of items. It will get count from TodoHeader component.
    
    
              <div> { this.props.count } </div>)

TodoHeader component displays the header of an application and it calls the TodoCount component to display the count of total items.
    
    
                < TodoCount count = { this.props.count}

Below is the TodoForm component. Let's focus on the same because it creates the data in addition to rendering.

The handleSubmit method is called when Submit button is clicked and it calls TodoSubmit method which it got from the Application component.

When I was doing this I had questions:

  * Why are we doing it this way?
  * Why Application component submits the form and not TodoForm?

The reason is that Application Component is the parent/grandparent of all components. And data flows from parent to child and child can't change the state of Parent. Also, there can't be any communication flow between siblings.

Now if TodoForm will submit the form then how will this information be passed to TodoList or TodoHeader component?

That's why we made Application component to be responsible for submitting the form.
    
    
            this.setState({ user: e.target.value })
    
    
            this.setState({ task: e.target.value })
    
    
            this.props.onTodoSubmit({ user: this.state.user, task: this.state.task })
    
    
            this.setState({ user: '', task: '' })
    
    
              <form className = "todoform"  onSubmit = { this.handleSubmit } >
    
    
                      <input type = "text" placeholder = "your name" 
    
    
                value = { this.state.user } onChange = { this.handleUserChange } /> 
    
    
                      <input type = "text" placeholder = "your task" 
    
    
                      <input type = "submit" value = "submit" />

The application component is the parent of all. It has methods on which we need some discussion.

**loadDataFromServer** - It will load data from the server, but in our example, there isn't any server so we have hard-coded the data.

**handleTodoSubmit** - This method would be called by the TodoForm as explained in TodoForm component.

When this method would be called then it will change the state with new created Todo item which will trigger re-rendering of Application component and all child components will be updated with the new information.
    
    
                  { id: 1, user: "Adam", task: "This is task1"},
    
    
                  { id: 2, user: "Ricky",task: "This is task2"}
    
    
            var todos = this.state.data
    
    
            var newTodos = todos.concat([todo])
    
    
                <TodoHeader count = { this.state.data.length } /> 

As you can see that if sibling components want to communicate with each other then they need to pass data to their parent component.

Like in our example **Todo Form **wants to tell **Todo List **that new item has been added.

That's why **Application **component is passing callback **handleTodoSubmit. **So on submit of Todo Form it is calling **handleTodoSubmit **method of **Application **component via callback. And handleTodoSubmit is updating the state of Application which causes the re-rendering of Application component by updating Todo Item and Todo Header.

In our example, there is only 1 hierarchy but in real time scenarios, there could be multi-level hierarchy where the innermost child would want to update the other level of innermost child. Then you have to pass the callback method over all the hierarchies.

But that would make it less maintainable and it also impacts readability in negative ways which will result in losing the power of React.

## Now Let's Try This Same Application Using Flux

As we have seen there are 4 layers in Flux. Let's write a code according to its structure.

### **Action**

Actions are called by Views. If View wants to update data in Store then View tells about this changeto action. Here we have created AppAction. In this, there is only 1 action i.e addItem.

This would be called when we want to add a new todo Item. This action further calls handleViewAction of dispatcher(AppDispatcher).

### **Dispatcher**

In AppDispatcher, handleViewAction is defined which is called by AppAction. In handleViewAction action is passed which will tell what action is performed.

There is a **this.dispatch** inside handleViewAction which is a pre-defined method of Dispatcher. This method will internally call the Store.

### **Store**

Let's discuss methods of Store one by one.

**dispatcherIndex - **Execution starts from here because of the AppDispatcher.register. Whenever dispatch method of Dispatcher is called then it would pass the action information wherever AppDispatcher.register is defined.

In our example, we have only one action "ADD_ITEM" but in most of the cases, there would be multiple actions. So we have to first define the type of action and based on that we will perform actions and will call emit method.

Here, we are calling addTodoItem method from dispatcherIndex method and after that emitChange.

**addTodoItem - **In this method we are not doing anything except pushing new todo item to the todoItems array.

**emitChange - **In emitChange, we are using this.emit(CHANGE_EVENT) method, this will let listeners of CHANGE_EVENT know that something is changed.

**addListener - **This method is used by Views to listen to the CHANGE_EVENT.

**removeListener - **This method is used by Views to remove listener.

**getTodoItems - **This method will return all the todos. This would be called by TodoList component.

**getTodoCount - **This method will return the count of all todos. This would be called by TodoCount component.
    
    
    var AppDispatcher = require('../dispatchers/app-dispatcher');

### **View/Components**

In TodoTask we did not change anything, it is the same as in above example.

In TodoList component, we are fetching todo items from Store directly by calling AppStore.getTodoItems in getInitialState.

Now the question is, "how will this component get to know when new todo item has been added?"

The _answer_ is in componentWillMount. In this method, we are calling **AppStore.addChangeListener** which will listen to the event which is defined in addChangeListener of Store. If there would be any change then it will call the _onChange which will reset the state.
    
    
            var TodoTasks = this.state.todoItems.map(function(todoTask) {

Similar to TodoList, TodoCount will also get data from Store and there is a listener defined in componentWillMount.
    
    
            return ( < div > { this.state.count } < /div>)

TodoHeader component is similar to above example.

In TodoForm, on submit of form AppAction.addItem would be called which will let Store know via Dispatcher as discussed above.
    
    
            this.setState({ user: e.target.value })
    
    
            this.setState({ task: e.target.value })
    
    
            AppAction.addItem({ user: this.state.user, task: this.state.task })
    
    
            this.setState({ user: '', task: ''})
    
    
              <form className = "todoform" onSubmit = { this.handleSubmit} >
    
    
              value = {this.state.user} onChange = { this.handleUserChange } /> 
    
    
              < input type = "text" placeholder = "your task"
    
    
              value = {this.state.task} onChange = {this.handleTaskChange} /> 
    
    
              < input type = "submit" value = "submit" / >

Now the job left for Application component is just to render 3 components TodoHeader, TodoForm, TodoList.
    
    
    ReactDOM.render( < Application / > , document.getElementById("example"))

## **Conclusion**

On comparing both the codes you will find that creating applications without using Flux is still easy. _But_ if you understand the flow of Flux then your choice would _always_ be Flux because the flow of Flux would be the same even when your application is getting complex. It provides us with additional benefits of _maintainability, readability, unidirectional data flow_.

To summarize, let's try again to understand the flow.

In TODO component, we are rendering 3 components <TodoHeader>, <TodoForm>, <TodoList>. There is no need to pass any callback, no need to define any state because <TODO> component is not doing anything except calling other components.

TodoHeader component is also not doing anything except rendering or calling other component.

In TodoCount component, we need to display the count of total items. We will get count from AppStore on rendering of TodoCount. But count may get an update after rendering of TodoCount component. That's why we have added listener in componentWillMount and removed in componentWillUnmount method. So if there would be any update in Store related to count then it would call _onChange method and will change the state of count accordingly.

TodoList component is displaying the list of Todo Items and for that it needs TodoItems. The behavior is similar to TodoCount in terms of communicating with AppStore.

In TodoForm, we want to submit the form and want to tell other components that new item has been added. So on submit, instead of telling other components it is just passing information to AppAction which will dispatch it to store with the help of AppDispatcher. And AppStore will update/add the data.

In AppStore, there is emit method called in emitChange which will allow listeners to know that information has been updated/added.

As you can see, components are not dependent on each other. If they need any information they will get it from **Store** and if they want to update anything then they will create an **Action** and it would be **Dispatch**ed to Store.

**Clearly, the data flow is unidirectional so it would be easy to understand and maintain.**

Hope you gained something from this article. Suggestions/corrections are welcome.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
