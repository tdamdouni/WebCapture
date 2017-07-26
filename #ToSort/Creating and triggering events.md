# Creating and triggering events

_Captured: 2016-03-08 at 10:31 from [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating_and_triggering_events)_

This article demonstrates how to create and dispatch events.

## Creating custom events

Events can be created with the `[Event`](https://developer.mozilla.org/en-US/docs/Web/API/Event) constructor as follows:
    
    
    var event = new Event('build');
    
    // Listen for the event.
    elem.addEventListener('build', function (e) { ... }, false);
    
    // Dispatch the event.
    elem.dispatchEvent(event);

This constructor is supported in most modern browsers (with Internet Explorer being the exception). For a more verbose approach (which works with Internet Explorer), see [the old-fashioned way](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating_and_triggering_events) below.

### Adding custom data - CustomEvent()

To add more data to the event object, the [CustomEvent](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent) interface exists and the _**detail**_ property can be used to pass custom data.  
For example, the event could be created as follows:
    
    
    var event = new CustomEvent('build', { 'detail': elem.dataset.time });

This will then allow you to access the additional data in the event listener:
    
    
    function eventHandler(e) {
      console.log('The time is: ' + e.detail);
    }

### The old-fashioned way

The older approach to creating events uses APIs inspired by Java. The following shows an example:
    
    
    // Create the event.
    var event = document.createEvent('Event');
    
    // Define that the event name is 'build'.
    event.initEvent('build', true, true);
    
    // Listen for the event.
    elem.addEventListener('build', function (e) {
      // e.target matches elem
    }, false);
    
    // target can be any Element or other EventTarget.
    elem.dispatchEvent(event);

## Triggering built-in events

This example demonstrates simulating a click (that is programmatically generating a click event) on a checkbox using DOM methods. [View the example in action.](http://developer.mozilla.org/samples/domref/dispatchEvent.html)
    
    
    function simulateClick() {
      var event = new MouseEvent('click', {
        'view': window,
        'bubbles': true,
        'cancelable': true
      });
      var cb = document.getElementById('checkbox'); 
      var canceled = !cb.dispatchEvent(event);
      if (canceled) {
        // A handler called preventDefault.
        alert("canceled");
      } else {
        // None of the handlers called preventDefault.
        alert("not canceled");
      }
    }

## Browser compatibility

  * Desktop
  * Mobile
