# Funny Function

### Functions as objects

Repeat the last part of the code for a few times:
``` javascript
const f = (prop) => {
  f.once = true;
  f.toggle = !f.toggle;
  return prop;
}

f([
  f.once === true,
  f.toggle === true
]);
```
Another sample of a 'once' function:
``` javascript
const once = () => once.flag ? false : once.flag = true;

once();
```
Or more universally:
``` javascript
const once = (tag) => once[tag] ? false : once[tag] = true;

once('foo'); // true
once('foo'); // false
once('foo'); // false
once(); // true
once(); // false
```
And a 'toggle' function again:
``` javascript
const toggle = (tag) => toggle[tag] = !toggle[tag];

toggle();
toggle();
toggle();
```

You can consider a function as an object which has a default method (let's call it 'main'):
``` javascript
f = {
  main: (<arguments>) => {
    <function body>
  },
  <...other properties>
}
```
So, when you call the `f(<arguments>)`, you actually refer to `f.main(<arguments>)`. It's something like a short-hand of the second option.
But be aware that the 'main' method is represented by anonymous function and not an object itself.
This is the crucial distinguish between named and anonymous functions: first are objects whereas second aren't.

---

### More functional `if-else` operators

If you inted to apply full `if-else` operator, you can use this snippet:
``` javascript
(condition ? () => {
  console.info('True');
} : () => {
  console.warn('False');
})();
```
If you want to organize the operator partially, you can use the next chain construction:
```
IF(<condition>, callbackIfTrue)[.ELSE(callbackIfFalse)]
```
where you should previously define the `IF` function:
``` javascript
const IF = (condition, callback) =>
  condition && (callback() || { ELSE: () => {} }) || { ELSE: (callback) => callback() };
```
Now you can write down something like:
``` javascript
IF(condition, () => {
  console.info('True');
}).ELSE(() => {
  console.warn('False');
});
```
or just the `if` part:
``` javascript
IF(condition, () => {
  console.info('True');
});
```
