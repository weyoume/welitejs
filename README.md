# welightjs

A lightweight JavaScript library for welightjs

### Install
```
npm install welightjs --save
```

### Usage
```js
var welightjs = require('welightjs');

// Init WebSocket client
var client = new welightjs.Client('wss://peer.ezira.io:8090');

// Get accounts
client.call('get_accounts', ['fabien'], function(err, result) {
  console.log(err, result);
});
```

### Promises

You can also use welightjs with promises by promisifying welightjs with
[bluebird](https://github.com/petkaantonov/bluebird) as in:

```js
var welightjs = require('welightjs');
bluebird.promisifyAll(welightjs.Client.prototype);
```

It'll add a *Async* to all welightjs functions (e.g. return client.callAsync().then())

```js
// So instead of writing client.request('get_accounts', ['fabien'], cb); you have to write:
return client.callAsync('get_accounts', ['fabien']).then(function(result) {
  console.log(result); // => [{ id: 26921, name: 'fabien' ...]
});
```

## License

[MIT](LICENSE).
