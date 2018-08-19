# ezlite.js

A lightweight JavaScript library for ezlite

### Install
```
npm install ezlite.js --save
```

### Usage
```js
var ezlite = require('ezlite.js');

// Init WebSocket client
var client = new ezlite.Client('wss://peer.ezira.io:8090');

// Get accounts
client.call('get_accounts', ['fabien'], function(err, result) {
  console.log(err, result);
});
```

### Promises

You can also use ezlite.js with promises by promisifying ezlite with
[bluebird](https://github.com/petkaantonov/bluebird) as in:

```js
var ezlite = require('ezlite.js');
bluebird.promisifyAll(ezlite.Client.prototype);
```

It'll add a *Async* to all ezlite functions (e.g. return client.callAsync().then())

```js
// So instead of writing client.request('get_accounts', ['fabien'], cb); you have to write:
return client.callAsync('get_accounts', ['fabien']).then(function(result) {
  console.log(result); // => [{ id: 26921, name: 'fabien' ...]
});
```

## License

[MIT](LICENSE).
