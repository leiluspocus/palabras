---
title: 'Passing arguments in an event handler Javascript'
date: "2013-02-26T23:19:15+00:00"
template: post
draft: false
slug: /en/passing-arguments-in-an-event-handler-javascript/
category: Javascript
tags:
  - bug
  - javascript
  - leaflet
---
I had this problem while working on Leaflet but I think it can be generalized to the issue of passing parameters to an event handler in Javascript. With the « bind » method of jQuery, you can pass parameters by using the data property of event (the object sent when an event is triggered) :
```javascript
$(marker).bind("click", { parameter : its_value, parameter2: its_value }, function(event) {
console.log("Your parameter is :" + event.data.parameter);
console.log("Your parameter2 is :" + event.data.parameter2);
// your code goes here
});
```
  
As « <em>marker</em> » was a L.Marker object, I had to convert it into a jQuery object before applying the bind method. <a href="http://stackoverflow.com/questions/3994527/passing-parameters-to-click-bind-event-in-jquery" target="_blank">Thank you Anurag on StackOverflow !!</a> 