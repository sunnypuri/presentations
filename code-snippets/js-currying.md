## Currying

Translating a function of N arguments to a 'tree' of N nested functions

```
function add(a, b, c){
    return a+b+c;
}
```

```
function add(a){
    return function(b) {
        return function (c) {
            return a+b+c;   
        }
    }
}

add(1)(2)(3);
console.dir(add(1)(2));
````

```
function add(x, y){
    return x+y;
}


add(1, 2);
```

```
function add(x) {
    return function(y){
        return x+y;
    }
}

var increment = add(1);
increment(5);


var incrementBy2 = add(2);
incrementBy2(5);
```

```
function multiply(x) {
    return function (y){
        return x*y;
    }
}

multiply(2)(5);


var double = multiply(2);
double(5);

var triple = multiply(3);
triple(5);
```


```
function isEven(num) {
    return num%2 == 0;
}

isEven(4);
```


```
function mod(modulo) {
    return function(value){
        return value % modulo;
    }
}

function equal(equalTo){
    return function(value){
        return value == equalTo;
    }
}

var modBy2 = mod(2);
var equalToZero = equal(0);


function isEven(num) {
    return equalToZero(modBy2(num));
}

isEven(4);
```

```
function not(fn){
    return function(value){
        return !fn(value);
    }
}


var isOdd = not(isEven);
isOdd(5);
```



```
function add(x, y, z) {
    return x + y + z;
}

add(1, 2, 3);
```

```
function curry(f, n = f.length, bound = []) {
    return function curried(...args) {
        if (args.length + bound.length >= n) {
            return f(...bound, ...args);
        } else {
            return curry(f, n, bound.concat(args));
        }
    }
}
```

```
var _add = curry(add);

console.log(_add(1)(2)(3));
console.log(_add(1, 2)(3));
console.log(_add(1, 2, 3));
console.log(_add(1)(2, 3));
```