# js-tips

A repository of coding tips, tricks, and patterns from the fifth cohort of Founders and Coders students.  

## Table of contents

* [On Click and On Enter events for text inputs](#on-Click-and-On-Enter-events-for-text-inputs)
* [Add event listeners to DOM elements that don't exist on page load](#add-event-listeners-to-DOM-elements-that-do-not-exist-on-page-load)
* [Test your endpoints with curl](#test-your-endpoints-with-curl)

## On Click and On Enter events for text inputs

### Description  
Often, you add a click event to a submit button then realise that it doesn't work on pressing enter. So you add a keypress event to key 13 and the whole thing is a bit messy. This tip suggests wrapping the text/button inputs in a form and adding a submit event to the form, rather than click/enter events to the button. Remember to prevent default to stop unwanted behaviour from the form actually being submitted.

### Use cases
This is of general use whenever you have text inputs - e.g. searching, or tweeting.

### Demo
Cycle through from base to /3 of [this fiddle](http://jsfiddle.net/rubie/ej86gtc8) to see it in action.

## Add event listeners to DOM elements that do not exist on page load

### Description  
You want to add event listeners to DOM elements that are created after the page loads. If you, say, add a click event to the element, targetting it by class, it won't work because the event is bound to something that doesn't yet exist. This solution suggests binding the event to an element that does exist on page load, and targetting the new element as a child of this element. In jQuery, it would take the form: ``` $("existing element").on("click", **("child element")**, function)```  

Or you could target using .next(), .closest(), and so on.

### Use cases
This does seem to pop up all the time - in our twitter application, for example, you add a tweet with a delete button and you want to add a click event to the delete button.

### Demo

Cycle through /4 to /7 of [this fiddle](http://jsfiddle.net/rubie/ej86gtc8/4/) and have a play to see how it works.

## Test your endpoints with curl

### Description

You can use the command line **curl** instead of the browser to send GET or POST request to your server to test your endpoints.

### Use cases

It can be useful to test the behavior of your endpoints by sending some random data with your requests. It's a good way to know if your endpoints can deal with all kind of information without crashing. It can also be useful when you want to know what your endpoints return.

### Demo

GET request:
```shell
curl mywebsite.com/myendpoint
```

Simple POST request
```shell
curl -d "some data sent to the server" mysebsite.com/myendpoint
```
POST request with json
```shell
curl -H "Content-Type: application/json" -d '{"property":"myvalue"}' mysebsite.com/myendpoint
```

curl contains a lot of options and can even do your coffee. To read the documentation type **man curl** in your terminal
