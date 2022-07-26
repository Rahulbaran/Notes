# [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

- Provides an interface for fetching resources asynchronously.
- Based on `Promise`.
- `fetch()` is used to make a request & fetch resources. It takes one mandatory argument **path to resource** & returns a `Promise` which resolves with `Response`. (`Promise` only rejects when a network error is encountered).
- We can also pass 2nd argument `init` in `fetch()`.

## Fetch Interfaces

### fetch()

- **Syntax:-**

```js
fetch(resource);
fetch(resource, init);
```

### Headers

- `Headers` object has an associated header list which represents response/request headers.
- `Headers()` constructor is used to create the object.
- `append()` method is used to add headers in the object.
- There are also other methods like `delete()`, `entries()`, `get()`, `set()`, `has()`, `keys()` & `values()`.

```js
const header = new Headers({
  "Content-Type": "application/json"
});

header.append("Accept-Encoding", "gzip");
header.set("Content-Type", "image/jpeg");
```

### Request

- Represents a resource request.
- `Request()` constructor is used to create `Request` object.
- Properties related with the object are `body`, `credentials`, `headers`, `method`, `mode`(no-cors, same-origin, navigate), `url` etc.
- `arrayBuffer()`, `blob()`, `clone()`, `formData()`, `text()` & `json()` are methods associated with `Request` object.

```js
const request = new Request("https://dogpics.com", {
  method: "GET",
  headers: {
    "Content-Type": "application/json"
  }
});

const [url, method] = [request.url, request.method];
```

### Response

- Represents the response to a request.
- `Response()` constructor is used to create `Response` object.
- Properties associated with the object are `body`, `headers`, `ok`, `status`, `statusText`, `type`(basic & cors), `url` etc.
- `arrayBuffer()`, `blob()`, `clone()`, `error()`, `formData()`, `json()`, `text()` & `redirect()` are associated methods.

```js
const response = new Response();
```

## Using the Fetch API

- Other than `XMLHttpRequest` API, `Fetch` API can easliy be used by other technologies such as `Service Workers`.
- `Fetch` also provides a single logical place to define other HTTP-related concepts such as `CORS` & extensions to HTTP.

- **Example**

```js
const resource = "https://dogpics.com";
fetch(resource)
  .then(res => res.json())
  .then(data => console.log(data));
  .catch(error => console.error(error))
```

- `Response` object returned by `fetch()` contains the entire HTTP response that's why we use `json()` to extract the actual JSON response which returns another promise & it resolves with the result of parsing the response body text as JSON.

## Supplying request options

- Along with `resource`, `fetch()` method optionally accepts 2nd parameter `init` object.
- **Example**

```js
const postData = async url => {
  const data = { names: ["Rahul", "Rohit", "Upendra", "Mamta"] };

  const init = {
    method: "POST", // GET, POST, PUT, DELETE etc.
    mode: "cors", // no-cors, cors, same-origin
    cache: "no-cache", // default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, same-origin, omit
    headers: {
      "Content-Type": "application/json", // application/json, application/x-www-form-urlencoded, text/plain
      redirect: "follow" // manual, follow, error
    },
    referrerPolicy: "no-referrer", //
    body: JSON.stringify(data)
  };
  const response = await fetch(url, init);

  return response.json();
};

postData("https://dog.ceo/api/breeds/list/all").then(data => console.log(data));
```

## Uploading a file

- `<input type='file' />`, `FormData()` & `fetch()` are used to upload a file.

```js
const $fileField = document.querySelector("input[type='file']");

const makeRequest = async function () {
  const formData = new FormData();
  formData.append("avatar", $fileField.files[0]);

  const response = await fetch("https://example.com/profile/avatar", {
    method: "POST",
    body: formData
  });

  return response.json();
};

makeRequest()
  .then(data => console.info(data))
  .catch(err => console.error(err));
```

## Uploading multiple files

- To upload multiple files `<input type="file" multiple />`, `FormData()` & `fetch()` are used.

```js
const $fileField = document.querySelector("input[type='file']");

const makeRequest = async function () {
  const formData = new FormData();
  for (let i = 0; i < formData.files.length; i++) {
    formData.append(`avatar-${i + 1}`, $fileField.files[i]);
  }

  const response = await fetch("https://example.com/posts", {
    method: "POST",
    body: formData
  });

  return response.json();
};

makeRequest()
  .then(data => console.info(data))
  .catch(err => console.error(err));
```

## Response Objects

- `Response` instance returned by `fetch()` after resolving promises has following common properties:-
  - `Response.status`
  - `Response.statusText`
  - `Response.ok`

## Body

- Both request & response may contain body data.
- A body is an instance of any of the following types:-
  - `ArrayBuffer`
  - `TypedArray`
  - `DataView`
  - `Blob`
  - `File`
  - `String`,
  - `URLSearchParams`
  - `FormData`
