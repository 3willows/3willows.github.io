---
categories: ["meta"]
date: "2024-07-31"
title: "Clojure conj: lists v vectors"
---

At [this juncture](http://clojurescriptkoans.com/#destructuring/3), I noticed an interesting pattern with the behaviour of  `conj` in Clojure.

As per ClojureDocs:

```clj
;; notice that conjoining to a vector is done at the end
(conj [1 2 3] 4)
;;=> [1 2 3 4]

;; notice conjoining to a list is done at the beginning
(conj '(1 2 3) 4)
;;=> (4 1 2 3)
```

Why?  According to a Perplexity AI answer and my PromptBros agent, it is because:

- Vectors are arrays, and the convenient place is for items to be added at the end.

- Lists are linked lists, and the the convenient place is for items to be added is at the beginning.

Not sure if this is accurate, but if so, it is a really cool way of signalling the difference! 