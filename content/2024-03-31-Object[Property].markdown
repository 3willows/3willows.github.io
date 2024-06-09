---
categories: ['Javascript']
date: "2024-03-31T00:00:00Z"
title: object.property v. object[property]
---

I recently came across a situation where I was fetching information from a RESTful API.  After some intermediate steps, I ended up with an array of objects, all of which have the same set of attribtues (e.g. including an id).

I wanted to have a way of printing a list of ids of the objects, e.g.

```jsx
let attribute = id

array.map(object => <li> object.attribute </li>)
```

But this didn't work.

It took me a while before I realised what I needed is instead:

```jsx
array.map(object => <li> object[attribute] </li>)
```

Without the square brackets, I was probably just trying to read a non-existent "attribute" property in the object.