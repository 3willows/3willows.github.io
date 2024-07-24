---
categories: ["meta"]
date: "2024-07-20"
title: "Quick start v. quick deploy: Express + MongoDB Atlas"
---

I had planned to follow these steps one after another to create a simple CRUD website with Express and MongoDB Atlas:

1. run a "hello world" example on my local machine.
2. deploying it to a common platform, e.g. Vercel.
3. wiring up the deployed Express App to the Mongo Atlas database

Steps 1 and 2 were fine.  This [official guide](https://vercel.com/guides/using-express-with-vercel) was helpful, even though I still don't understand exactly why I need to remove the following line before deploying:-

```js
app.listen(port, () => console.log(`Server ready on port ${port}.`))
```

(I assume it is because the app needs to listen to a different port on the Vercel server.)

Step 3 was however very convoluted, given I had chosen Vercel at Steps 1 and 2.  There are online guides (including [official guidance](https://www.mongodb.com/docs/atlas/reference/partner-integrations/vercel/)), but there are a lot of nitty gritty set up I would rather avoid.

In the end I decided to change track and deploy on Render instead following this [tutorial](https://www.youtube.com/watch?v=i1wAQCg2iWU) and [repo](https://github.com/john-guerra/nodeExpressMongoES6_promptStorer).

The finished product is [here](https://nodeexpressmongoes6-promptstorer-main.onrender.com/): it takes a while to load because the server needs to "wake up" every time someone visits.

Going forward, it seems a better idea to start with Step 3 in mind.  Integrating a deployed database with the deployed website is straightforward, and I want all the help I can get.