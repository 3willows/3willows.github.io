---
categories: ['meta']
date: "2024-07-08"
title: "Random HTML Attribute"
---

I spent last evening and this morning playing around with Andrew's [Random MDN page](https://random-mdn-page-deploy.vercel.app/).  The result is a remix, [Random HTML Attribute](https://random-html-attribute.vercel.app/).

Looking through my old commits, here are main hurdels along the way:-

- The MDN webpage used in the original project is no longer actively maintained: see web archive version [here](https://web.archive.org/web/20200615000000*/https://developer.mozilla.org/en-US/docs/Web/JavaScript/Index).

- I therefore needed to look for an alternative page with a similiar structure.  There were a few candidates but in the end I settled on [this page](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes).


- I then applied the procedure described in [his write up](https://healeycodes.com/tiny-project-to-completion), i.e. use developer tools (more specifically ```Copy -> Copy JS Path```), with appropriate modifications.

- To give me a better feel for what data I was getting from ```getNewPages.js```, I renamed the keys for the JSON object to make sure I could see at a glace what data was being scraped: see [this commit](https://github.com/3willows/random-html-attribute/commit/a591a577c49e0e1412ef452e8208adc81633e3e1).  

- It was also important to use the [optional chaining (?.)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) operator, to make sure that my code still ran even if there was nothing to the property I was looking for.

- From then on the journey went more or less smoothly.  When deploying I kept getting an ```Internal server error``` at the final hurdle (i.e. after running ```vercel``` for deployment), even though the ```localhost:3000```(after running ```vercel dev```) was working fine.

- But looking under the ```build logs``` of my project in my Vercel account, it was quickly apparent that the server did not understand ```views/index meant``` ```view/index.*ejs*```.  That was the glitch at the final hurdle.

One question that lingers in my mind is why exactly do I need to comment out the listener, i.e. 

```js
const listener = app.listen(process.env.PORT, function () {
  console.log("Your app is listening on port " + listener.address().port)
})
```

And also add an export i.e. 

```js 
module.exports = app
```

For the deployment to work.  The export is easier to understand, but why exactly does the listener throw a spanner in the works?  

Perplexity.ai says it is something to do with serverless environments: in which case it is something too far away from my experience to have a feel for yet.

A pleasant surpise is the simple URL provided by Vercel at a click: https://random-html-attribute.vercel.app/.  This somehow looks more pleasing then github pages which always begins with a github handle.