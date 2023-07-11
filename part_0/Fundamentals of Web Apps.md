## Fundamentals of Web Apps

### Developer Console

`ctrl + shift + i` in chrome - windows/linux
`option-cmd-i` in chrome - MacOS

### HTTP GET

The server and the browser communicate with each other via HTTP (Hyper-text transfer protocol)

<img src="./network-img.png" width="500" height="350">

When the page is loaded, the browser fetches contents of the page: https://studies.cs.helsinki.fi/exampleapp/ from the server and has downloaded the image (kuva.png)

<img src="./network-headers.png" width="500" height="350"> <br>
The headers in the above image show the details of request and response exchange done by the browser (client) and server.

- General headers

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

- Response Headers <br>
  <img src="./network-response.png"> <br>

  - Connection → indicates whether the network connection stays open after the current transaction finishes
  - Content Length → size of the response (bytes)
  - Content Type → format the response file along with the format type
  - Date → time the message was created
  - Etag → known as the entity tag; refers to the specific version of the resource
  - Server → specifies the software used by the server at the time of response
  - X-Powered-By → refers to the technologies used by the web server. Note: the prefix `X-` in a header means that it is a non-standard header

  Ref.: https://dev.to/spukas/http-headers-explained-4kg1 <br>

- Sequence Diagram of request and response: <br>
  <img src="./req-res-seq-img.png" width="700" height="350"> <br>