---
categories: ['db']
date: "2024-07-01"
title: "Schema and Model in Mongoose (2 of 2)"
---

So the point of Schema is to define what properties can be read.

The point of model is instead to define what collection is read.

Try

```js
const uri = process.env.DB_URL;
const port = process.env.PORT || 3000;
const localTest = "mongodb://127.0.0.1:27017/test"

const express = require("express")
const mongoose = require("mongoose")
const app = express()

app.use(express.static("public"))

main().catch((err) => console.log(err))

async function main() {
  await mongoose.connect(localTest)
}

// There is no "goingCrazy" property in Kitten
// There is instead a "name" property of the type String.
const kittySchema = new mongoose.Schema({
  goingCrazy: Number
})

const Kitten = mongoose.model("Mitten", kittySchema)

async function doSomething() {
  const cats = await Kitten.countDocuments()
  const names = await Kitten.find()
  console.log(cats)
  console.log(names)
}
doSomething()

app.listen(port, () => console.log(`Server ready on port ${port}.`))

module.exports = app
```

This will read the empty "Mitten" collection, as opposed to the "Kitten" collection.