---
categories: Javascript
date: "2024-03-25T00:00:00Z"
title: Anonymous functions have no reference in memory
---

I ran into a small bug today.

Following a tutorial, I added an anonymous function as the second argument to my ```window.addEventListener```, i.e.

```js
window.addEventListener("popstate", () => console.log("hello world"))
```

I then struggled to remove it with

```js
window.removeEventListener("popstate", () => console.log("hello world"))
```

At first I tried to solve it with studying in detail the documentation for ```window.removeEventListener```.

But soon I changed track: how can I find out what Event Listeners there are in my DOM (or in my window object)? A quick Google led to:

```js
getEventListeners(window).popstate
```

Using this I checked and confirmed that removeEventListener wasn’t removing anything.

I then experimented with using a named function instead of an anonymous function. This turned out to be the correct hunch.

The reason seems to be that anonymous functions have no reference and therefore nowhere to live in memory.  

That also means they cannot be removed easily: ```()⇒ console.log(”hello world”)``` in the ```removeEventListener``` is a different function to that in the ```addEvenListener```.

Sources: 
- [Event Listeners Anonymous Functions.](https://gomakethings.com/named-vs-anonymous-event-listener-functions/) 
- [Named vs. anonymous event listener functions](https://gomakethings.com/named-vs-anonymous-event-listener-functions/)
