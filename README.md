# ifetch
> A tiny fetch lib to use ajax based on promise

Installation
---

```
  $ npm install ifetch
```

Usage
---

Add the paths to configuration:

```javascript
// Usage
function errHandler(err) {
  if (err.status === 401) {
    window.location = '/auth/logout';
  }
  return new Promise(function(resolve, reject) {
    reject(err);
  });
}

let fetch = {};

['get', 'post', 'put', 'delete'].forEach((m) => {
  fetch[m] = function(options) {
    var opt = Object.assign({
      dataType: 'json',
      contentType: 'application/json',
      headers: {
        'X-REGION': 'ext'
      }
    }, options);

    return request[m](opt).catch(errHandler);
  };
});

module.exports = fetch;
```

License
---

ifetch is available under the terms of [the MIT license](LICENSE).
