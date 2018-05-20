# Mapping through an object like an array

```javascript
// mapObject :: (a -> b) -> {a} -> {b}
const mapObject = f => obj => 
  Object.entries(obj).reduce(($, [key, value]) => ({ ...$, [key]: f(value) }), {})
```

# Example

```javascript
const letters = {
  a: { capital: 'A', minuscule: 'a', position: '1' },
  b: { capital: 'B', minuscule: 'b', position: '2' },
  c: { capital: 'C', minuscule: 'c', position: '3' },
  ...
}

const extractCapitals = ({ capital }) => capital

mapObject(extractCapitals)(letters) // { a: 'A', b: 'B', c: 'C', ... }
```
