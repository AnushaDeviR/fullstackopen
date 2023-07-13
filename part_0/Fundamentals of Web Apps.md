# Fundamentals of Web Apps

## Developer Console

`ctrl + shift + i` in chrome - windows/linux
`option-cmd-i` in chrome - MacOS

## HTTP GET

The server and the browser communicate with each other via HTTP (Hyper-text transfer protocol)

<img src="./network-img.png" width="500" height="350">

When the page is loaded, the browser fetches contents of the page: https://studies.cs.helsinki.fi/exampleapp/ from the server and has downloaded the image (kuva.png)

<img src="./network-headers.png" width="500" height="350"> <br>
The headers in the above image show the details of request and response exchange done by the browser (client) and server.

<b>- General headers</b>

- Request URL → the URL we want access
- Request Method → the method used by HTTP/HTTPS to request the details
- Status Code → are issued by the server in response to the request, these specify the standard statuses of responses.

  ```
  Note:
  1xx informational response – the request was received, continuing process
  2xx successful – the request was successfully received, understood, and accepted
  3xx redirection – further action needs to be taken in order to complete the request
  4xx client error – the request contains bad syntax or cannot be fulfilled
  5xx server error – the server failed to fulfil an apparently valid request
  ```

  Ref.: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes

  - Remote Address → server's IP Address
  - Referrer Policy → the referrer in HTTP header contains the full or partial address from where the resource has been requested; the referrer policy controls how much information about the referrer is to be included with the requests.

  ```
  Referrer-Policy: no-referrer
  Referrer-Policy: no-referrer-when-downgrade
  Referrer-Policy: origin
  Referrer-Policy: origin-when-cross-origin
  Referrer-Policy: same-origin
  Referrer-Policy: strict-origin
  Referrer-Policy: strict-origin-when-cross-origin
  Referrer-Policy: unsafe-url
  ```

  Ref.: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy

<b>- Response Headers </b><br>
<img src="./network-response.png"> <br>

- Connection → indicates whether the network connection stays open after the current transaction finishes
- Content Length → size of the response (bytes)
- Content Type → format the response file along with the format type
- Date → time the message was created
- ETag → known as the entity tag; refers to the specific version of the resource
- Server → specifies the software used by the server at the time of response
- X-Powered-By → refers to the technologies used by the web server. Note: the prefix `X-` in a header means that it is a non-standard header

Ref.: https://dev.to/spukas/http-headers-explained-4kg1 <br>

- Sequence Diagram of request and response: <br>
  <img src="./req-res-seq-img.png" width="700" height="350"> <br>

## Traditional web applications

In a traditional web application, when an URL is accessed through the browser, it fetches the HTML document containing the structure and textual details of the accessing page from the server. The HTML document could either be static (file saved on the server) or dynamic (server forms the file with the application code, eg.: data from database).

## Running application logic in the browser

The browser fetches the HTML as the first document, from that page it fetches the JavaScript file from the script tag from the `head` element of the HTML code.

## Event handlers and Callback functions

Event handler are known as callback (a function passed into another function as input) functions. The browsers invoke the event handlers when the event on the webpage has occurred.

## Document Object Model (DOM)

HTML pages are implemented in a tree-like structure. Document Object Model (DOM) is an Application Programming Interface (API) that allows modifications of the elements to reflect on webpages. <br>

```
var ul = document.createElement('ul')

data.forEach(function(note) {
  var li = document.createElement('li')

  ul.appendChild(li)
  li.appendChild(document.createTextNode(note.content))
})

document.getElementsByClassName('notes').appendChild(ul)
```

From the above code, new child nodes are created (`ul`) which is referred by the class name `notes`. 

