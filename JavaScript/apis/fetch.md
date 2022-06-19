# [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

- Provides an interface for fetching resources.
- Based on `Promise`.
- `fetch()` is used to make a request & fetch resources. It takes one mandatory argument **path to resource** & returns a `Promise` which resolves with `Response`. (`Promise` only rejects when a network error is encountered).

- We can also pass 2nd argument `init` in `fetch()`.

## Fetch Interfaces

#### fetch()

- **Syntax:-**

```js
fetch(resource);
fetch(resource, init);
```

#### Headers

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

#### Request

- Represents a resource request.

- `Request()` constructor is used to create `Request` object.

- Properties related with the object are `body`, `credentials`, `headers`, `method`, `mode`(no-cors, same-origin, navigate), `url` etc.

- `arrayBuffer()`, `blob()`, `clone()`, `formData()`, `text()` & `json()` are methods associated with `Request` object.

```js
const request = new Request("https://dogpics.com");

const [url, method] = [request.url, request.method];
```

#### Response

- Represents the response to a request.

- `Response()` constructor is used to create `Response` object.

- Properties associated with the object are `body`, `headers`, `ok`, `status`, `statusText`, `type`(basic & cors), `url` etc.

- `arrayBuffer()`, `blob()`, `clone()`, `error()`, `formData()`, `json()`, `text()` & `redirect()` are associated methods.

```js
const response = new Response();
```
