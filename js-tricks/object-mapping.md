# Mapping through an object like an array

```javascript
// mapObject :: (a -> b) -> {a} -> {b}
const mapObject = f => obj => 
  Object.entries(obj).reduce(($, [key, value]) => ({ ...$, [key]: f(value) }), {})
```
