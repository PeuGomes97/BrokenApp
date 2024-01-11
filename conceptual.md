### Conceptual Exercise

Answer the following questions below:

- What are some ways of managing asynchronous code in JavaScript?

 One way is using promises. The best practice would be to avoid nested callbacks. When a promise is returned we can handle using .then and .catch, to manage what is done after the promise is resolved or rejected. .then can be chained to avoid too much nesting, and using only one .catch after chaining.
A better option is using async await with try and catch, in place of .then and .catch. The await keyword will stop the execution of the code until the promise gets a resolved value, and then move on to the next line of code to execute. We also use the catch keyword to handle rejected promise.

- What is a Promise?

A promise is a pending value, a guarantee that something will be rejected or resolved in the future.

- What are the differences between an async function and a regular function?

Async functions always return a promise, and also supports the use of await keyword, which a regulor function does not. Async functions runs asynchronously when a regular function run syncronously.

- What is the difference between Node.js and Express.js?

Node.js is allows us to use Javascript to run in a server-side environment. That means we can use Javascript for back-end porposes.
Express.js is a framework to make easier for building applications using Node.js

- What is the error-first callback pattern?

Node.js always have the error as the first parameter. 

- What is middleware?

Middleware run  in the middle of request-response cycle. Middleware functions intercept requests, before being passed to the execution of the route and it can use the updated response. For ex: User authentication before accessing a route.

- What does the `next` function do?

Allows the next piece of middleware in sequence to run

- What are some issues with the following code? (consider all aspects: performance, structure, naming, etc)

```js
async function getUsers() {
  const elie = await $.getJSON('https://api.github.com/users/elie');
  const joel = await $.getJSON('https://api.github.com/users/joelburton');
  const matt = await $.getJSON('https://api.github.com/users/mmmaaatttttt');

  return [elie, matt, joel];
}


We can be more descriptive about the variable names. Since the functions is returning information about those users and not the user itself. Also about execution, the await keyword in every axios.get it stops the code to run the next user until the previous one being resolved. A better approach would be = 

async function getUserInfo() {
  const elieInfoPromise = $.getJSON('https://api.github.com/users/elie');
  const joelInfoPromise = $.getJSON('https://api.github.com/users/joelburton');
  const mattInfoPromise = $.getJSON('https://api.github.com/users/mmmaaatttttt');

  const [elieInfo, joelInfo, mattInfo] = await Promise.all([elieInfoPromise, joelInfoPromise, mattInfoPromise]);

  return { elieInfo, mattInfo, joelInfo };
}
