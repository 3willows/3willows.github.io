---
categories: ["meta"]
date: "2024-07-29"
title: "Learn Next.js with the Leviathan"
---

[[demo]](https://leviathan-five.vercel.app/)
[[repo]](https://github.com/3willows/leviathan)

After finishing the official quick start, I wanted to try Next.js out with an actual project.

Soon after I started web programming, I used plain HTML and CSS (and a lot of ChatGPT) to put together a web version of [John Selden's Table Talk](https://3willows.github.io/johnSeldenTableTalk/).  The process took a day or two around new year's eve and new year's day.

8 months on and with Next, the process has got a lot smoother.

Unsurprisingly in hindsight, it was the text wrangling that took the most time.  I already had it easy: Project Gutenberg provides a single html file, which each chapter separated enclosed within a ```<div class="chapter">```.  This makes things a lot simpler than when I was using a plaintext file converted with pandoc.

Still, it took some time for me to get the bash script right, even with all the plethora of AI tools supplied by [PromptBros](https://promptbros.ai/).  My focus was on comparatively old tools such as ```sed``` and ```awk```: perhaps I would have been better off using some modern and more familiar tools.  

Still, if other Project Gutenberg books follow a similar format, I may be able to reuse the scripts I already have.

Once text-wrangling is done, the Next.js's out of the box features really shines:

- Routing can be automatically done with arranging a directory structure
- The css can be configured in one go.  
- Deployment with Vercel is seamless.

A minor snag towards the end was the fact tht Next.js routes are [absolute by default](https://stackoverflow.com/questions/69084689/relative-routing-in-next-js/78805112#78805112): which means if you nest the directories further in or further out, special steps have to be taken, e.g.

```jsx
 const pathname = usePathName()

<Link href={`${pathname}/chapter/1`}>Chapter 1</Link>
```

I wonder what the design philosophy behind this is.  Was it an accident of history, kept on because of the need to maintain backwards compatibility?