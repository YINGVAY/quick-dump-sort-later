This is forcing the variable "https" to use the 'http' module
```javascript
const https = require('http');
```


This line uses the `get()` method from the `https` module to send a request to the url, which is the endpoint that provides a random quote in JSON format.

The second parameter `(resp) => {...}` is a callback function that is called once the response is received from teh server. The `resp` parameter represents the servers response to the request.
```javascript
https.get('https://api.quotable.io/random', (resp) => {
```

We are creating a variable that will hold the response as the data arrives, the data comes in chunks and we will combine them as the arrive into one complete string.

```javasctipt
let data = '';
```

The part of the code is listening for data events. The `on('data')` function is triggered every time a chunk of data is received from the server.

Each time a chunk of data arrives, its added to the `data` variable. This happens because the response may arrive in chunks.

```javascript
  resp.on('data', (chunk) => {
    data += chunk;
  });
```

once all of the data has been received, the `end` event is fired, signaling that the response is complete, we are using `JSON.parse(data` to convert the string of data we've received into a javascript object. This is because the server response is in JSON format, a format for representing structured data

`quote.content` is the actual quote text, and `quote.author` is the author of the quote. At last we log the quote and author to the console using `console.log()`

```javascript
  resp.on('end', () => {
    const quote = JSON.parse(data);
    console.log(`"${quote.content}" - ${quote.author}`);
  });
```

This part is simply listening to errors during the HTTP request, if there is a issue it will trigger the error event and it will print it to the console

```javascript
}).on('error', (err) => {
  console.log('Error: ' + err.message);
});
```

**the final complete program that prints the quotes.

```javascript
const https = require('https');

// Fetch a random quote from the API
https.get('https://api.quotable.io/random', (resp) => {
  let data = '';

  // A chunk of data has been received.
  resp.on('data', (chunk) => {
    data += chunk;
  });

  // The whole response has been received.
  resp.on('end', () => {
    const quote = JSON.parse(data);
    console.log(`"${quote.content}" - ${quote.author}`);
  });

}).on('error', (err) => {
  console.log('Error: ' + err.message);
});
```

[[2025-01-14 (fourth day, feeling overwhelmed)]]





