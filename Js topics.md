# Must learn topics in JAVA SCRIPT

## NOTE: ES6 (most important in JavaScript)

### JAVA SCRIPT:
> JavaScript is a programming language that powers the dynamic behavior on most websites. Alongside HTML and CSS, it is a core technology that makes the web run.
<ol>
    <li>Var, let, const</li>	
    <li>Interactions: Alert, Prompt, Confirm</li>
    <li>Functions
    <ul>
        <li>Arrow function</li>
        <li>IIFE function</li>
    </ul>
    </li>
    <li>Object method , this</li>
    <li>New operator</li>
    <li>JSON methods
    <ul>
    <li>JSON.parse</li>
    <li>JSON.stringify</li>
    </ul>
    </li>
    <li>Prototype
    <ul>
        <li>Prototypal Inheritance</li>
        <li>F.Prototype</li>
        <li>Native prototypes</li>
        <li>Prototype methods, objects without __proto__</li>
    </ul>
    </li>
    <li>Callbacks
    <ul>
    <li>Callback hell</li>
    </ul>
    </li>
    <li>Promise
    <ul>
    <li>Promise Chaining</li>
    <li>Promise.all</li>
    <li>Promise.allSettled</li>
    <li>Promise.race</li>
    <li>Promise.resolve/reject</li>
    </ul></li>
    <li>Implicit Try....Catch</li>
    <li>Regular Expressions</li>
    <li>Closures</li>
    <li>Arrays</li>
    <li>Fake namespaces</li>
    <li>DOM manipulation</li>
    <li>Event Handlers</li>
    <li>Fetch Api</li>
    <li>Get</li> 
    <li>Post (error is coming in it)</li>
    <li>JQuery 
    <ul>
    <li>Events</li>
    <li>Effects</li>
    <li>Selectors</li>
    <li>HTML</li>
    <li>CSS</li>
    <li>DOM</li>
    </ul></li>
    <li>AJAX
    <ul>
    <li>XML Http</li>
    <li>Request</li>
    <li>Response</li>
    </ul></li>
</ol>

## Keywords

### let Keyword
> let creates a local variable in JavaScript & can be re-assigned. Initialization during the declaration of a let variable 
> is optional. A let variable will contain undefined if nothing is assigned to it
> - eg. let count;

### const Keyword
> A constant variable can be declared using the keyword const. It must have an assignment. Any attempt of re-assigning a const variable will result in JavaScript runtime error. 
> - eg. const numberOfColumns = 4;

## Promises

#### States of a JavaScript Promise
```
const promise = new Promise((resolve, reject) => {
  const res = true;
  // An asynchronous operation.
  if (res) {
    resolve('Resolved!');
  }
  else {
    reject(Error('Error'));
  }
});

promise.then((res) => console.log(res), (err) => alert(err));
```
>A JavaScript Promise object can be in one of three states: pending, resolved, or rejected.
 
> While the value is not yet available, the Promise stays in the pending state. Afterwards, it transitions to one of the two states: resolved or rejected.
 
 >A resolved promise stands for a successful completion. Due to errors, the promise may go in the rejected state.
 
 >In the given code block, if the Promise is on resolved state, the first parameter holding a callback function of the then() method will print the resolved value. Otherwise, an alert will be shown.

### Avoiding nested Promise and .then()
```
const promise = new Promise((resolve, reject) => {  
  setTimeout(() => {
    resolve('*');
  }, 1000);
});

const twoStars = (star) => {  
  return (star + star);
};

const oneDot = (star) => {  
  return (star + '.');
};

const print = (val) => {
  console.log(val);
};

// Chaining them all together
promise.then(twoStars).then(oneDot).then(print);
```
> In JavaScript, when performing multiple asynchronous operations in a sequence, promises should be composed by chaining multiple .then() methods. This is better practice than nesting.
 
> Chaining helps streamline the development process because it makes the code more readable and easier to debug.
### Chaining multiple .then() methods
```
const promise = new Promise(resolve => setTimeout(() => resolve('dAlan'), 100));

promise.then(res => {
  return res === 'Alan' ? Promise.resolve('Hey Alan!') : Promise.reject('Who are you?')
}).then((res) => {
  console.log(res)
}, (err) => {
  alert(err)
});
```
> The .then() method returns a Promise, even if one or both of the handler functions are absent. Because of this, multiple .then() methods can be chained together. This is known as composition.
 
 > In the code block, a couple of .then() methods are chained together. Each method deals with the resolved value of their respective promises.
## Async-await
### Resolving JavaScript Promises
```
let promise1 = Promise.resolve(5);
let promise2 = 44;
let promise3 = new Promise(function(resolve, reject) {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then(function(values) {
  console.log(values);
});
// expected output: Array [5, 44, "foo"]
```
> When using JavaScript async...await, multiple asynchronous operations can run concurrently. If the resolved value is required for each promise initiated, Promise.all() can be used to retrieve the resolved value, avoiding unnecessary blocking.

### Async Await Promises
```
function helloWorld() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('Hello World!');
    }, 2000);
  });
}

async function msg() {
  const msg = await helloWorld();
  console.log('Message:', msg);
}

msg(); // Message: Hello World! <-- after 2 seconds
```
> The async...await syntax in ES6 offers a new way write more readable and scalable code to handle promises. It uses the same features that were already built into JavaScript.

### JavaScript async…await advantage
> The JavaScript async...await syntax allows multiple promises to be initiated and then resolved for values when required during execution of the program. As an alternate to chaining .then() functions, it offers better maintainablity of the code and a close resemblance synchronous code.

### Async Function Error Handling
```
let json = '{ "age": 30 }'; // incomplete data

try {
  let user = JSON.parse(json); // <-- no errors
  alert( user.name ); // no name!
} catch (e) {
  alert( "Invalid JSON data!" );
}
```
> JavaScript async functions uses try...catch statements for error handling. This method allows shared error handling for synchronous and asynchronous code.

## Requests

### HTTP GET request

> HTTP GET requests are made with the intention of retrieving information or data from a source (server) over the web.

 > GET requests have no body, so the information that the source requires, in order to return the proper response, must be included in the request URL path or query string.

### Asynchronous calls with XMLHttpRequest
```
const xhr = new XMLHttpRequest();
xhr.open('GET', 'mysite.com/api/getjson');
```
> AJAX enables HTTP requests to be made not only during the load time of a web page but also anytime after a page initially loads. This allows adding dynamic behavior to a webpage. This is essential for giving a good user experience without reloading the webpage for transferring data to and from the web server.
 
> The XMLHttpRequest (XHR) web API provides the ability to make the actual asynchronous request and uses AJAX to handle the data from the request.
 
> The given code block is a basic example of how an HTTP GET request is made to the specified URL.

### The query string in a URL
```
const requestUrl = 'http://mysite.com/api/vendor?name=kavin&id=35412';
```
> Query strings are used to send additional information to the server during an HTTP GET request.
 
> The query string is separated from the original URL using the question mark character ?.
 
 > In a query string, there can be one or more key-value pairs joined by the equal character =.
 
> For separating multiple key-value pairs, an ampersand character & is used.
 
 > Query strings should be url-encoded in case of the presence of URL unsafe characters.

### XMLHttpRequest GET Request Requirements
```
const req = new XMLHttpRequest();
req.responseType = 'json';
req.open('GET', '/myendpoint/getdata?id=65');
req.onload = () => {
  console.log(xhr.response);
};

req.send();
```
> The request type, response type, request URL, and handler for the response data must be provided in order to make an HTTP GET request with the JavaScript XMLHttpRequest API.
 
> The URL may contain additional data in the query string. For an HTTP GET request, the request type must be GET.

### HTTP POST request
> HTTP POST requests are made with the intention of sending new information to the source (server) that will receive it.
 
> For a POST request, the new information is stored in the body of the request.

### HTTP POST request with the XMLHttpRequest API
```
const data = {
  fish: 'Salmon',
  weight: '1.5 KG',
  units: 5
};
const xhr = new XMLHttpRequest();
xhr.open('POST', '/inventory/add');
xhr.responseType = 'json';
xhr.send(JSON.stringify(data));

xhr.onload = () => {
  console.log(xhr.response);
};
```
> To make an HTTP POST request with the JavaScript XMLHttpRequest API, a request type, response type, request URL, request body, and handler for the response data must be provided. The request body is essential because the information sent via the POST method is not visible in the URL. The request type must be POST for this case. The response type can be a variety of types including array buffer, json, etc.

### JSON Formatted response body
```
fetch('url')
.then(
  response  => {
    console.log(response);
  },
 rejection => {
    console.error(rejection.message);
);
```
> The .json() method will resolve a returned promise to a JSON object, parsing the body text as JSON.
 
### promise url parameter fetch api
```

fetch('url')
.then(
  response  => {
    console.log(response);
  },
 rejection => {
    console.error(rejection.message);
);
```
> A JavaScript Fetch API is used to access and manipulate requests and responses within the HTTP pipeline, fetching resources asynchronously across a network.
 
 > A basic fetch() request will accept a URL parameter, send a request and contain a success and failure promise handler function.
 
 > In the example, the block of code begins by calling the fetch() function. Then a then() method is chained to the end of the fetch(). It ends with the response callback to handle success and the rejection callback to handle failure. 
 The example block of code shows .json() method that returns a promise that resolves to a JSON-formatted response body as a JavaScript object.

### async await syntax
```
const getSuggestions = async () => {
  const wordQuery = inputField.value;
  const endpoint = `${url}${queryParams}${wordQuery}`;
  try{
const response = __~await~__ __~fetch(endpoint, {cache: 'no-cache'});
    if(response.ok){
      const jsonResponse = await response.json()
    }
  }
  catch(error){
    console.log(error)
  }
}
```
> The async…await syntax is used with the JS Fetch API fetch() to work with promises. In the code block example we see the keyword async placed the function. This means that the function will return a promise. The keyword await makes the JavaScript wait until the problem is resolved.


### Good Resources to learn JavaScript:

1. https://javascript.info/
2. https://www.w3schools.com/js/DEFAULT.asp
3. https://www.codecademy.com/learn/introduction-to-javascript


		




