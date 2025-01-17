---
sidebar_position: 9
sidebar_label: web3.eth.subscribe
---

# web3.eth.subscribe Migration Guide

## Breaking Changes

### New Block Headers event

In 1.x, `web3.eth.subscribe('newBlockHeaders')` was used to subscribe to new block headers.

In 4.x, either `web3.eth.subscribe('newHeads')` or `web3.eth.subscribe('newBlockHeaders')` can be used to subscribe to new block headers.

### web3.eth.clearSubscriptions

In 1.x, `web3.eth.clearSubscriptions` returns `true` on success.

In 4.x, `web3.eth.clearSubscriptions` returns an `Array of subscription ids`.

```typescript
// in 1.x
var subscription = web3.eth.subscribe('newBlockHeaders', function (error, result) {
	if (!error) console.log(result);
});
web3.eth.clearSubscriptions(function (error, success) {
	console.log(success); // true
});

// in 4.x
const subscription = await web3.eth.subscribe('newHeads');
subscription.unsubscribe().then(
	console.log(), // [...] Array of subsription ids
);
```
