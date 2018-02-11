Say, we want to store and represent some ORDERED key-value data. 
The most common way is to use an aray of objects:

``` javascript
const arr = [
  { name: 'a', value: 1 },
  { name: 'b', value: 2 },
  { name: 'c'. value: 3 },
];
```

Though it's very convenient to map through this array, it obviously isn't a pleasant to repeat yourself with all this `name`'s and `value`'s. 
Could we organize this structure with less writing efforts?

Consider this construction:

``` javascript
const obj = {
  a: 1,
  b: 2,
  c: 3,
};
```
Defenitely less typing.
To present the data it contains we can use something like that: 

``` javascript
const printObject = obj => Object.keys(obj).forEach(key => { console.log(key, '=', obj[key]) })
```

This produce such output:
```
a = 1
b = 2
c = 3
```

However, if order matters, we could encounter such situation: 

``` javascript
const objWithNumIndex = {
  a: 1,
  b: 2,
  3: 'c',
};
```

This time the output will be:
```
3 = c
a = 1
b = 2
```

Not so good, yeah?
Then I can suggest using this stucture: 

``` javascript
const list = [
  { a: 1 },
  { b: 2 },
  { 3: 'c' },
];
```

As we can see, there is a little bit more typing, but this time the list order will be kept.

To map through this list I suggest using something like that: 

``` javascript
const print = list => list.forEach(item => {
  const key = Object.keys(item)[0];
  console.log(key, '=', item[key]) 
});
// a = 1
// b = 2
// c = 3
```

