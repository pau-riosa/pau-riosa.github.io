---
layout: post
author: Pau Riosa
title: "JS101: Unit Testing using Jest"
---

### Install Jest

```
$ yarn add --dev jest
```

or 

```
$ npm install --save-dev jest
```

### Setup

In this example, let us say we are going to solve a problem regarding `Sum of Multiples`.
This is problem that can be found on [Project Euler](http://projecteuler.net/problem=1)

For us to begin, we need to create a folder in our directory, and create a three different files namely
`hello_world.js`, `hello_world.test.js` and `jest.config.js`

```
$ mkdir hello_world 
```
```
$ touch hello_world/hello_world.js
```
```
$ touch hello_world/hello_world.test.js
```
```
$ touch hello_world/jest.config.js
```

You should have something like this, then you are good to go.

![figure 1 file structure](/assets/images/files.png)

### Grind time

Now that we have setup our test environment we are going to start our unit testing using jest!

On `hello_world.js`, we are going to put...

```javascript
function hello_world() {
  return "Hello world!"
}

module.exports = hello_world
```

in `hello_world.test.js`
```javascript
const hello_world = require('./hello_world')
test("function hello_world", () => {

  expect(hello_world()).toBe("Hello world!")
})
```

in your terminal

```
$ jest
```

![figure 2 result](/assets/images/result.png)


### Conclusion

Just another day of learning, I am proud that I am able to manage to come up with a unit test using jest for javascript.
I am amazed for what it can do and a little bit what it can't.

Unit testing is essentially if you want to test the every functions or methods that you have in your code. This will help you simulate different scenarios, and to minimize bugs eventually.
