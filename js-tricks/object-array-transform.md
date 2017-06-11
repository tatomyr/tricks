# Useful tip on transfomation an `key:value`-pair array to appropriate object and vice-versa 

```javascript
const arr = [
  { key: 'a', val: 1 },
  { key: 'b', val: 2 },
];

const obj = arr.reduce((prev, { key, val }) => ({ ...prev, [key]: val }), {}); // { "a": 1, "b": 2 }

const arr2 = Object.keys(obj).map(key => ({ key, val: obj[key] })); // [{ "key": "a", "val": 1 }, { "key": "b", "val": 2 }]
```
