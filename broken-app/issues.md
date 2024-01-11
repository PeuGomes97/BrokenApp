# Broken App Issues

- No Error Handle set

- No 404 handler

- Function for listen on port not properly set. Written with no call back function on info being passed on console or server.

- Axios and app variables not properly declared using const for the module requirement.

- Using "app.use(express.json()); to recognize every output in JSON format, instead of using old way "JSON.Stringify"

- Implementing async keyword to the post route so it makes the function run asynchronously. 