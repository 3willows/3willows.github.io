---
categories: Javascript
date: "2024-03-24T00:00:00Z"
title: In Array.sort()’s compareFn, the order of a and b doesn't matter
---

MDN documentation on Array.prototype.sort() says of the the optional CompareFn,

>A function that determines the order of the elements. The function is called with the following arguments:
>
>- ```a``` The first element for comparison. Will never be `undefined`.
>
>- ```b``` The second element for comparison. Will never be `undefined`.
>
>It should return a number where:
>
>- A negative value indicates that `a` should come before `b`.
>- A positive value indicates that `a` should come after `b`.
>- Zero or `NaN` indicates that `a` and `b` are considered equal.
>
>To memorize this, remember that `(a, b) => a - b` sorts numbers in ascending order.

But Stephen Girder[^1] observes that, if we ```console.log``` within the comapreFn on Chrome, a actually comes after b  E.g.

```js
const compareFn = (a, b) => {
console.log("a:", a)
console.log("b:", b)
console.log('a - b', a - b )
return a-b
}

const data = [4, 3, 2, 1]

data.sort(compareFn)
```

Logs:

``` js
a: 3
b: 4
a - b: -1
a: 2
b: 3
a - b: -1
a: 1
b: 2
a - b: -1
```

After some googling (and finding this [article](https://stackoverflow.com/questions/24080785/sorting-in-javascript-shouldnt-returning-a-boolean-be-enough-for-a-comparison?noredirect=1&lq=1)), I realised that the order of a and b doesn’t matter.

If a is the first element and b the second element, everything just flips around.   The programme should instead log something like:

```js
a: 4
b: 3
a - b: 1
a: 4
b: 2
a - b: 2
a: 4
b: 1
a - b: 3
```

In any case, conceptually the comparator function has nothing to do with this kind of step-by-step comparison (which is part of the procedure for bubble sort).  The comparator function just needs to specify the direction of the sort: it doesn’t matter how the sorting is done.

[^1]: Modern React with Redux [2024 Update] (Ep.263)