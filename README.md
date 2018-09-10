# welitejs

A lightweight JavaScript library for WeYouMe

### Install
```
npm install welitejs --save
```

### Usage
```js
var welitejs = require('welitejs');

// Init WebSocket client
var client = new welitejs.Client('wss://peer.WeYouMe.io:8090');

// Get accounts
client.call('get_accounts', ['fabien'], function(err, result) {
  console.log(err, result);
});
```

### Promises

You can also use welitejs with promises by promisifying welitejs with
[bluebird](https://github.com/petkaantonov/bluebird) as in:

```js
var welitejs = require('welitejs');
bluebird.promisifyAll(welitejs.Client.prototype);
```

It'll add a *Async* to all welitejs functions (e.g. return client.callAsync().then())

```js
// So instead of writing client.request('get_accounts', ['fabien'], cb); you have to write:
return client.callAsync('get_accounts', ['fabien']).then(function(result) {
  console.log(result); // => [{ id: 26921, name: 'fabien' ...]
});
```

## License

[MIT](LICENSE).
