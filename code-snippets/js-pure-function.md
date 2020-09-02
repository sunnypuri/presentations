## Pure Function

Always receive the same output for a given input with no side effects.


```
function toLowerCase(str) {
    return str.toLowerCase();
}

toLowerCase('Hello');
```

```
function toUpperCase(str) {
    return str.toUpperCase();
}

toUpperCase('Hello');
```

```
function trim(str) {
    return str.trim();
}

trim('   Hello    ');
```


```
function isEven(num) {
    return num % 2 === 0;
}

isEven(4);
```

```
function isOdd(num) {
    return !isEven(num);
}

isOdd(6);
```

```
function add(x, y) {
    return x + y;
}

add(1, 3);
```


> Avoid side effects

```
var one = 1;
function increment(num) {
    return num + one;
}

console.log(increment(5));
```

```
function increment(num) {
    return num + 1;
}

increment(5);
```

```
function increment(num) {
    return add(num, 1);
}

increment(5);
```


```
function random(range){
    return Math.floor(Math.random() * range);
}

random(5);
```

```
Math.max(1, 2, 3, 4, 5);
```

> Avoid side effect means It should not modify anything outside of their scope.


> Pure functions must not mutate external state.

```
var maxValue = 0;
function max(arr) {
    maxValue = Math.max(...arr);
}

max([1, 2, 3, 4, 5]);
console.log(maxValue);
```

```
var list = [1, 2, 3, 4, 5];
Math.max(...list);
Math.max.apply(this, list);
```


> Impure

```
var list = [1, 2, 3, 4, 5];
console.log('Splice', list.splice(1));
console.log('Splice', list.splice(1));
console.log('Splice', list.splice(1));
```

> Pure

```
var list = [1, 2, 3, 4, 5];
console.log('Slice', list.slice(1));
console.log('Slice', list.slice(1));
console.log('Slice', list.slice(1));
```
