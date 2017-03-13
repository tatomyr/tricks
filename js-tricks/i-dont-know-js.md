# I Don't Know JS

### 1

Use this snippet to pick the right case from an object (parentheses depend on context):
``` javascript
({ foo: 'Hello', bar: 'World' })['foo']
```
It could be even function:
``` javascript
({ foo: () => console.log('Hello'), bar: () => alert('World') })['bar']()
```

### 2

When we need to try whether some object is defined to properly get to its property, we often use such construction:
``` javascript
let foo;
foo && foo.bar || 'Default value'
```
While it's a quite straightforward approach, it has a redundant duplication, which could be crucial, especially when 'foo' is a complicated function, or when it's situated inconveniently to be calculated twice. So, in that case, we can use a trick to evade a 'Cannot read property 'bar' of undefined' error:
``` javascript
(foo || {}).bar
```
or even more expressively:
``` javascript
(foo || { bar: 'Default value' }).bar
```

### 3

Try
``` javascript
for (var i = 1; i <= 5; i++) {
  setTimeout(() => {
    console.info(i);
  }, i*1000);
}
```
vs
``` javascript
for (let i = 1; i <= 5; i++) {
  setTimeout(() => {
    console.info(i);
  }, i*1000);
}
```
See the difference between this two snippets?
