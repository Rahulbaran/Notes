# [XMLHttpRequest API](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)

-   This API is used to interact with servers.

-   Data can be retrieved from a URL without full page referesh.

-   Used Heavily in **AJAX(Asynchronous JavaScript XML)**

-   Can be used to retrieve any type of data.

## Constructor

#### XMLHttpRequest()

-   Creates an `XMLHttpRequest` object.

```bash
const xhr = new XMLHttpRequest();
```

## Properties

#### XMLHttpRequest.onreadystatechange

-   An event handler which is called whenever the `readyState` attribute changes.

#### XMLHttpRequest.readyState (Read only)

-   Returns state of request in as an `unsigned short` (0 to 4)

| Value | State            | Description                                                           |
| ----- | ---------------- | --------------------------------------------------------------------- |
| 0     | UNSENT           | XMLHttpRequest object has been created but open() has not been called |
| 1     | OPENED           | open() has been called                                                |
| 2     | HEADERS_RECEIVED | send() has been called & headers and status are available             |
| 3     | LOADING          | Downloading: responseText holds partial data                          |
| 4     | DONE             | The operation is complete                                             |

#### XMLHttpRequest.response (Read only)

-   Returns any of **ArrayBuffer**, **Blob**, **Document**, **JS objects**, **DOMString** depending on **XMLHttpRequest.responseType**.

#### XMLHttpRequest.responseText (Read only)

-   Returns a **DOMString** that contains the response to the request as text, or `null` if the request was unsuccessful or has not yet been sent.

#### XMLHttpRequest.responseType

-   Used to set type of data in the response.
-   Possible values

    -   **""** - Empty String similar to **text**
    -   **arraybuffer** - JS **ArrayBuffer** containing binary data.
    -   **blob** - a **Blob** object containing binary data
    -   **document** - an HTML Document or XML Document
    -   **json** - response is a JS object created upon parsing received JSON data
    -   **text** - a text in a **DOMString** object.
    -   **ms-stream**

-   Default value is **text**.

#### XMLHttpRequest.responseURL (Read only)

-   Returns URL of the response or empty string if URL is null.

#### XMLHttpRequest.responseXML (Read only)

#### XMLHttpRequest.status (Read only)

-   Returns an `unsigned short`(status-code) with the status of response of the request.

#### XMLHttpRequest.statusText (Read only)

-   Returns a text containing information about response status (status code with a string).

#### XMLHttpRequest.timeout

-   Used to set a time for a request before it is automatically terminated.

-   Time is set in **milliseconds**.

#### XMLHttpReuqest.withCredentials

-   A boolean value which indicates whether or not cross-site `Access-Control` requests should be made using credentials such as cookies or authorization headers.

## Event Handlers

-   Various **on\*** evnet handler are supported which are `onload, onreadystatechange, onerror, onprogress, onloadstart, onloadend`.

-   **XMLHttpRequest** events via standard `addEventListener()` APIs are also supported.

Note:- **DOMString** behaves similar to JavaScript **String**.

## Methods

#### XMLHttpRequest.abort()

-   To abort the request if it has already been sent.

-   It cancels the request

#### XMLHttpRequest.getAllResponseHeaders()

-   Returns all the response headers, separated by CRLF, as a string, or null if no response has been received.

#### XMLHttpRequest.getResponseHeader()

-   Returns the value of specified header or null if either response has not yet been received/header doesn't exist in response.

#### XMLHttpRequest.open()

-   Used to initialize a request.

-   It takes 3 arguments.
    -   request method (GET,POST,PUT,DELETE,PATCH etc.)
    -   request URL
    -   request type in boolean(async - true)

#### XMLHttpRequest.overriedMimeType()

-   Overrides the MIME type returned by the server

#### XMLHttpRequest.send()

-   To send a request after initializing it using **open()**.

-   If the request is asynchronous (which is the default), this method returns as soon as the request is sent.

#### XMLHttpRequest.setRequestHeader()

-   To set the header of HTTP request.

-   It should be used after **open()** but before **send()**.

-   It allows setting one header (key-value) at one call which means to set multiple headers we will have to call it multiple times.

## Events

#### abort

-   Fired when a request has been _aborted_ using **XMLHttpRequest.abort()** method.
-   We can also use **onabort** property.

#### error

-   Fired when request faces an _error_.
-   **onload** property can also be used.

#### load

-   Fired when request has been made successfully.
-   **onload** property can also be used.

#### loadstart

-   Fired when a request has started to load data.
-   **onloadstart** can also be used.

#### loadend

-   Fired when a request has completed.
-   **onloadend** property can also be used.

#### progress

-   Fired periodically when a request receives more data.
-   Also available via **onprogress** property.

#### timeout

-   Fired when progress (request) is terminated due to preset time expiring (timeout property is used).
-   Also available via **ontimeout** property.

---

-   Form data can be sent in formats like `multipart/form-data`, JSON, XML etc.

-   In the event of a communication error (such as the server going down), an exception will be thrown in the **onreadystatechange** method when accessing the response status. To mitigate this, we can wrap it inside `try...catch`.

-   When using **FormData** to submit POST requests using **XMLHttpRequest** or the **Fetch_API** with the `multipart/form-data` Content-Type (e.g. when uploading Files and Blobs to the server), _do not explicitly set the Content-Type header on the request_. Doing so will prevent the browser from being able to set the Content-Type header with the boundary expression it will use to delimit form fields in the request body.
