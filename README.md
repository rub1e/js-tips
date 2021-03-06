# js-tips

A repository of coding tips, tricks, and patterns from the fifth cohort of Founders and Coders students.  

## Table of contents

* [On Click and On Enter events for text inputs](#on-click-and-on-enter-events-for-text-inputs)
* [Add event listeners to DOM elements that don't exist on page load](#add-event-listeners-to-dom-elements-that-do-not-exist-on-page-load)
* [Test your endpoints with curl](#test-your-endpoints-with-curl)
* [A more useful **typeof**](#a-more-useful-typeof)  

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

NOTE: if you are using os x yosemite you might encounter the following issue: http://superuser.com/questions/830920/curl-local-host-names-on-mac-os-x-yosemite

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

## A more useful typeof  

### Description

Use typeof to determine the type of a data. If you want to get more information about the type you might need to use the method toString.

### Use case

One way to debug your code is to know the type of the data you work with. For that javascript has the specific method **typeof**. But this function when applied to different type of object will always return object. To determine the specific type of an object we can use the method **toString** from Object.prototype.


### Demo
```javascript
var string = "Hello World";
var number = 1;
var object = {"Hello":"World"};
var array = ["Hello", "World"];
var regex = /Hello World/;
var nullNull = null;
var undef = undefined;
var boolean = false;
var func = function(){};
var date = new Date();
var math = Math;
var error = new Error();
var nan = NaN;
var doc = document;

var arr = [string,number,object,array,regex,nullNull,undef,boolean,func,date,math,error,nan,doc];

console.log(arr.map(function(elt){
  return typeof elt;
}));

//Better with Object.prototype.toString

console.log(arr.map(function(elt){
  return Object.prototype.toString.call(elt);
}))

```

We need to use Object.prototype.toString.call because every object can specified their own implementation of the toString method (and we don't want this).
