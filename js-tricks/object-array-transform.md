#  Tips on transfomation an `key:value`-pair array to appropriate object and vice-versa 

```javascript
const arr = [
  { key: 'a', val: 1 },
  { key: 'b', val: 2 }
];

const obj = arr.reduce((prev, { key, val }) => ({ ...prev, [key]: val }), {}); // { "a": 1, "b": 2 }

const arr2 = Object.keys(obj).map(key => ({ key, val: obj[key] })); // [{ "key": "a", "val": 1 }, { "key": "b", "val": 2 }]
```

### Useful functions
```javascript
const arrToObj = (arr, customKey = 'key', customVal = 'val') => arr.reduce((prev, { [customKey]: key, [customVal]: val }) => ({ ...prev, [key]: val }), {});

const objToArr = (obj, customKey = 'key', customVal = 'val') => Object.keys(obj).map(key => ({ [customKey]: key, [customVal]: obj[key] }));

arrToObj([
  { key: 'a', val: 1 },
  { key: 'b', val: 2 }
]) // { "a": 1, "b": 2 }

objToArr({ a: 1, b: 2 }) // [{ "key": "a", "val": 1 }, { "key": "b", "val": 2 }]

objToArr([3, -7], 'name', 'value') // [{ name": "0", "value": 3 }, { "name": "1", "value": -7 }]
```
