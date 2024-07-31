---
categories: ["meta"]
date: "2024-07-30"
title: "More ClojureScript Koans"
---

I could only programme for a very short time today, so decided to have another crack at Clojure Koans.

[This puzzle](http://clojurescriptkoans.com/#functions/9) is a good brain teaser.  Dill in the ___ below.

```clj
(= 25 ( ___ (fn [n] (* n n))))
```

I was stuck and decided to make a [Clojure tutor](https://promptbros.ai/agent/clz9wopvz0001azkhmwwpin6w) bot on PromptBros to chat with.

Again, it didn't give the right answers: the ```apply``` function (if correctly explained) requires an input after the function, not before.

I struggled a short while, but eventual a light bulb went on when I realised everything in ____ needs to be enclosed in parentheses so that the expression is evaluated and a function is returned.

Looking forward to picking up at [Higher Order Functions](http://clojurescriptkoans.com/#higher-order-functions/2).