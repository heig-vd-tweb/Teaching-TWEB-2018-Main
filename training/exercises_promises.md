# Promises: exercises
1\)
```js
const p1 = new Promise(function(resolve, reject) {
  console.log('2');
  resolve();
});
p1.then(function() { console.log('1'); });
// Answer: 2 1
```

2\)
```js
function f1() { console.log('U'); }
const f2 = () => new Promise((success) => success('A'));
f1();
f2().then((value) => { console.log(value); f1(); });
// Answer: U A U
```

3\)
```js
const f1 = () => new Promise((s) => s('S'));
const f2 = (d) => new Promise((s) => s(d + 'F'));
const f3 = () => console.log('A');
const f4 = () => console.log('H🐰');

f1().then(f2).then((v) => { f3(); console.log(v); f4(); });
// Answer: A SF H🐰
```

4\)
```js
const p1 = (data1) => new Promise((resolve) => resolve(data1));
const p2 = (d) => new Promise((resolve) => resolve(d + 'R'));
const p3 = (data2) => new Promise((resolve) => resolve('H'));
const p4 = (data2) => new Promise((resolve) => resolve(data2 + '♥'));

p1('R').then(p2).then(p3).then(p4).then(console.log);
// Answer: H♥
```

5\)
```js
let promise = new Promise((resolve) => resolve());
promise.then(value => console.log(1));
console.log(2);
console.log(3);
// Answer: 2 3 1
```

6\)
```js

console.log(1);
let promise = new Promise((resolve) => {
  console.log(2);
  resolve();
})

7\)
promise.then(() => console.log(3));
console.log(4);
// Answer: 1243
```

8\)
```js
function test() {
  new Promise(resolve => resolve('ok'))
    .then(data => {
      return data;
    });
}
// What does `test();` return? => undefined
```

9\)
```js
function test() {
 return new Promise(resolve => resolve('ok'))
    .then(data => {
      return data;
    });
}
// What does `test();` return? => a promise
```

10\)
```js
Promise.resolve()
.then(
  () => { throw new Error('Woups!'); },
  () => { console.log('catch 1'); },
)
.catch(() => { console.log('catch 2')});
// Answer: catch 2
```

11\)
```js
const p1 = (data) => new Promise((resolve, reject) => data > 2 ? resolve('A') : reject('Z'));
p1(1).then(z => console.log('O'), a => console.log('U'));
p1(5).then(z => console.log('O'), a => console.log('U'));
// Answer: U O
```

12\)
```js
new Promise((resolve) => { throw new Error('Woups'); })
  .catch(error => console.log(error.message))
  .then(() => console.log('done'));
// Answer: Woups done
```

13\)
```js
function getValue() {
  if (true) return 1;
  return new Promise((resolve) => resolve(2))
}
getValue().then(v => console.log('the value is ' + v));
// TypeError!
// How to fix it ? Promise.resolve(1), Promise.resolve(getValue())
```

14\)
```js
for (var i = 0; i < 3; ++i) {
  setTimeout(() => { console.log(i) }, 100);
}
// Answer: 333 => the synchronous loop is totally executed before the asynchronous code.
```

15\)
```js
let a = 0;

for (let i = 0; i < 3; ++i) {
  new Promise((resolve) => setTimeout(resolve(), 100))
    .then(() => ++a);
}

console.log(a);
// Answer: 0 => use Promise.all
```

16\)
```js
function sendLoggingData(req) {
  return new Promise((resolve, reject) => {
    setTimeout(() => { throw new Error('Woups!'); }, 1000);
  });
}

app.get('/', (req, res) => {
  sendLoggingData(req).then(() => console.log('data sent!'));
  res.send('ok');
});
// What is happening here? 'ok' is sent, then the server CRASHES.
```
