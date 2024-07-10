---
categories: ['meta']
date: "2024-07-10"
title: "Notes on my first Clojure Dojo"
---

Doing [4clojure](https://4clojure.oxal.org/) for 2 hours, from problem 1 to problem 21 ([nth element](https://4clojure.oxal.org/#/problem/21)).

1

Everything is an expression in clojure.  So are there any statements?

2

On the command line, ``` `(6 7 8)``` is not the same as ```(6 7 8)``` because it is not evaluated.  Similiar for ```:a ``` versus ```a```.


3

Searching and parsing the following expressions:

```clojure
 (for [i (range 1 5)] i)

 (for [i (range 1 5)](* 2 i))

 (do (for [i (range 1 5)](* 2 i)))

 (doall (for [i (range 1 5)](* 2 i)))
 
 (print (for [i (range 1 10)](* 2 i)))
 ```

4

Reading and deciphering the following answer for [nth element](https://4clojure.oxal.org/#/problem/21):

```clojure
(def index-of
  (fn [a b] ((vec a) b)))
```

Basically, forcing everything in a vector so that you can use get.