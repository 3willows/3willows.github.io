---
categories: ['meta']
date: "2024-07-06"
title: "From Passport.js to Project Mood: diary of a day's reading"
---

## 1 Passport.js

I started the day with the excellent ["Concept" section](https://www.passportjs.org/concepts/authentication/) of the documenation for Passport.js, a tool for adding user authenticiation with Express.js.

I have been reading into the documentation for MongDB and Mongoose recently.  The trouble with them (as of 2024) was that there was a very steep jump between the very simple quick start example and the full documenation.  

This made getting to grips with the materials very difficult: especially because Mongoose is a kind of "wrapper" around MongoDB native driver, and when I search for how things are done, search results often use two different sets of terms.

By contrast, the Passport.js "Concepts" section is an ideal bridge between simple instructions to get things done and a more conceptual explanation focusing on the "whys".

Of course, even after reading it, there are some questions that are still unclear:

(1) What exactly is "salt" when we use the LocalStrategy?  Or in storing users' passwords in general?

(2) Why does (say) LocalStrategy return a "verify function" that is a callback?  

But at least now I am able to understand where "salt" and "verify function" fit in the overall scheme of things.  Very roughly, 

(1) You only need to go down to the reeds with "salt" if you are taking care of storing user data on a grandular level with the LocalStorage strategy.

(2) By contrast, all strategies (including authentication using 3rd parties tools) involve the use of callbacks (sometimes called "cb", sometimes "done": always the 2nd/3rd paramter).  In fact, heavy use of callbacks is a feature of Express and even Node more generally.

(cf. [This answer](https://stackoverflow.com/questions/32153865/what-is-done-callback-function-in-passport-strategy-configure-use-function)  and [this answer](https://stackoverflow.com/questions/65342761/passportjs-configuration-done-callback) from StackOverflow)

## 2 Sessions and the 5-6 different ways of storing things on the browser

When following through the Passport.js quickstart tutorial, I had run into an issue with not enabling express-session.   

This meant I could not make use of session storage in the browser, which is necessary for the quick-start example to work.

This led me to find out more about different ways in which a browser stores data, which are explained by a number of good tutorials with easy follow-along:

- Local storage: cf. this [article](https://medium.com/@joeylee08/localstorage-101-persisting-browser-data-on-the-client-694cea0981b3) with examples that can be tested on the browser right away.

- Going deeper into the broader background: e.g. this [series of articles](https://javascript.info/cookie) on Javascript.info.

- Which led to an exploration of the "Application" tab on Chrome Developer Tools, which listed 6 different kinds of storage I could explore directly in the browser, including the intriguing IndexDB.

I then tried to find a way of mainpulating IndexDB on the browser alone (with the console and the Application tab) without success.  No follow-along was readily available: possibly something too advanced at this stage.

I am intensely curious about the history behind how all these different ways came about.  As with everything on the web, I strongly suspect it is an organic development with a lot of commercial and hardware issues underlying it.  

In some ways I find trying to learn about the web similiar to doing archival history (as I imagine it): one has to hunt through many different sources, and understand their background and motivations, in order to get into the minds of the people who created the tools on the webs.

## 3 Project Mood

I had discovered RSS earlier from my Hugo template.  

Initially I wanted to get rid of it as I did not want it to clutter up my blog: but later rememebred watching a documentary about how a young [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz) contributed to the development of RSS, and deciding to spend some more time on it.

This turned out to be a very good investment.  In short, [RSS](https://www.youtube.com/watch?v=0klgLsSxGsU) is tool to subscribe to any blog I like, without the search engine serving as intermediary.  This gives a fantastic browsing experience, as I could immediately flip between the 20-30 blogs that I like without going through any distracting Googling/clicking through messy bookmarks.

One of the blogs I started reading more of after using RSS is [Andrew Healey's](https://healeycodes.com/).  His posts are written in a way that is pleasant to read, even if one doesn't understand all the technical details (e.g. [this recent offering](https://healeycodes.com/2d-multiplayer-from-scratch)).  Which makes them ideal for idle browsing.

Digging through his older posts, I found [a 2019 post on "Project Mood"](https://healeycodes.com/project-mood), which seems to use many of the technologies i am learning no (e.g. Express).

Unfortunately, when I downloaded and tried to run the code, I kept running into an error with my "USERAGENT" (according to the error message).

This forced me to dig deeper into (1) (generally) what the "User-Agent" Header is all about, and (2) exactly what kind of "User-Agent" is expected when I use the Github API.

Fortunately, there is a very [good video (with Github repo)](https://github.com/3willows?tab=repositories) explaining this.

It seems the original code had a minor error, in that "process.env.USERAGENT" was used directly as a property in a JSON object, i.e. 

```js
{ headers: {'User-Agent': process.env.USERAGENT}}
```

Whereas it probably needs to be placed in a template literal like so:

```js
{ headers: {'User-Agent':`${process.env.USERAGENT}`}}
```

In any case, I was very pleased to end the day by making Project Mood work on my local machine!  At this point, I enjoy reading and tinkering with other people's code to creating my own by far.  

Often I don't feel I really understand the technology well enough to really plan anything meaningfully yet.  But I can read and tinker with what other people have done and in the process gain more fluency.