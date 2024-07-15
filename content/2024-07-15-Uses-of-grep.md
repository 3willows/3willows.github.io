---
categories: ['meta']
date: "2024-07-15"
title: "Uses of grep: changing font size for a Hugo static website"
---

Recently I wanted to adjust the font size of this blog.

I already have a theme installed, so the choices are either changing something somewhere within the ```theme```, or somehow overriding the ```theme```.

A simple Google query didn't produce any straightforward results.  StackOverflow answers seem limited to specific situations. 

Perplexity AI gave a solution along the lines of overriding the default theme with some additional files.  An intriguing solution, but one that neither worked nor have any obvious support from Hugo DOcs.

It turned out a much easier way to solve the issue was to simply run ```grep -r "font"``` then ```grep -r "font-size" ```.  

It was quite clear from the results what I needed to change where.   It was then the work of the moment to see the changes reflected in the local environment.

```grep``` clearly still has a place even in the age of ChatGPT.