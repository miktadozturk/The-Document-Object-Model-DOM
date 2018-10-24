# DOM Events

Things happen on webpages. Images load and videos end. Users do things on webpages as well. They move their mouse over things, they click on things, they resize their windows, they change their device orientation, etc. Very often when these things happen we want to respond in some way. Fortunately, we can by listening for the events that they generate.

```
document.addEventListener('click', function() {
    console.log('There was a click somewhere on the page!');
});
```

If you paste the code above into your console and hit enter, you will see that every time you click on the page 'There was a click somewhere on the page!' is logged.

The ```addEventListener``` method does not just exist on the document ```object```. Every element has it. Without reloading the page, let's add the following code:

```
document.body.addEventListener('click', function() {
    console.log('There was a click on the body element!');
});

document.documentElement.addEventListener('click', function() {
    console.log('There was a click on the html element!');
});
```

Now when you click on the page you can see the event is handled first by the listener attached to the body element, then by the one attached to the ```html``` element, and finally by the ```document``` object. This is called event bubbling. Events bubble up the DOM tree from the element they first happen on all the way to the document object.

The first argument passed to ```addEventListener``` is obviously the name of the event to listen for. The second argument is a function to serve as the listener or event handler. ```addEventListener``` also accepts a third parameter, a boolean indicating whether or not to use event capturing. Event capturing is like event bubbling but in reverse.

```
document.body.addEventListener('click', function() {
    console.log('A click was captured on the body element!');
}, true);

document.documentElement.addEventListener('click', function() {
    console.log('A click was captured on the html element!');
}, true);

document.addEventListener('click', function() {
    console.log('A click was captured on the document!');
}, true);
```

If you paste the above code into your console you will see that the events that use capturing happen in reverse order and that they all occur before any of the events that bubble.

