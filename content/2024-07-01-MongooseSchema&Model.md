---
categories: ['db']
date: "2024-07-01"
title: "Schema and Model in Mongoose"
---

Initially I was surprised that the code below logs anything out at all.

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

const Kitten = mongoose.model("Kitten", kittySchema)

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

If the code still works when the Schema is empty, what is the point of it in the first place?

Part of the answer is that you cannot read the properties in the BSON documents unless you specify it in the Schema.

Try

```js
  const oneCat = await Kitten.findOne()
  console.log(oneCat.name)
```

This will log "undefined".  Add the "name" property in the Schema and the problem is fixed.