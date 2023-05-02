# Warmup

Here's an `app.js` file for an Express application that will run on port 5000. When we visit each of these routes, what will the output be?

1. `localhost:5000/`
1. `localhost:5000/granola`
1. `localhost:5000/poptarts`
1. `localhost:5000/banana`
1. `localhost:5000/fruits/cherry`
1. `localhost:5000/shoes?not=false`

```js
const express = require('express');
const app = express();

app.use((req, res, next) => {
  console.log('a request came in', req.path);
  next();
})

app.get("/", (req, res, next) => {
  res.send('This is the root route');
})

app.get("/granola", (req, res, next) => {
  res.send('granola is a great breakfast');
})

app.get("/:food", (req, res, next) => {
  res.send(`${req.params.food} is ${req.query.not ? 'not ' : ''}a food`)
})

app.get("/poptarts", (req, res, next) => {
  res.send("pop tarts are a part of this complete breakfast");
})

// error handling
app.use((error, req, res, next) => {
  console.log(error.message);
  res.send(error);
})

module.exports = app;
```
