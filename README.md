### pify
---
https://github.com/sindresorhus/pify

```js
const fs = require('fs');
const pify = require('pify');
pify(fs.readFile)('package.json', 'utf8').then(data => {
  console.log(JSON.parse(data).name);
});
pify(fs).readFile('package.json', 'utf8').then(data => {
  console.log(JSON.parse(data).name);
});

const request = require('request');
const pify = require('pify');
pify(request, {multiArgs: true})('https://sindresorhus.com').then(result => {
  const [httpResponse, body] = result;
});

const pify = require('pify');
function fn(){
  return true;
}
fn.method = (data, callback) => {
  setImmediate(() => {
    callback(null, data);
  });
};
const promiseFn = pify(fn, {excludeMain: true});
if(promiseFn()){
  promiseFn.method('hi').then(data => {
    console.log(data);
  });
}

```

```
npm install pify
```

```
```


