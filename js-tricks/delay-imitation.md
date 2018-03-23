# Random Delay Imitation

```javascript
const f = () => new Promise(resolve => {
  // Delay generator (s): [0; 3)
	const delay = Math.round(1000 * (Math.random() + Math.random() + Math.random()))
	setTimeout(() => {
		resolve(delay)
  }, delay)
}) 

f().then(delay => { console.info(delay) })
```
