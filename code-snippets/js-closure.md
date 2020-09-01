## Closure

Closure means that an inner function always has access to the variables of its outer function, even after the outer function has returned.

> Scope: Local and global scope(window), also we have closures

> Common example of closure add(1)(2)(3)

```
function add(a) {
    return function (b) {
        return a+b;
    }
}

add(1)(2);
console.dir(add(1));
```

```
function add(a) {
    var c = 3;
    return function (b) {
        return a+b+c;
    }
}

add(1)(2);
```

```
var c = 3;
function add(a) {
    return function (b) {
        return a+b+c;
    }
}

add(1)(2);
```

```
function add(a) {
    var c = 3;
    var d = 4;
    return function (b) {
        return a+b+c;
    }
}

add(1)(2);
```

```
function add(a) {
    c = 3;
    return function (b) {
        return a+b+c;
    }
}

add(1)(2);
console.dir(add(1));
```

```
function add(a) {
    return function (b) {
        return function (c) {
            return a+b+c;   
        }
    }
}

add(1)(2)(3);
console.dir(add(1)(2));
```

> Example: Counter

```
var counter = function (){
    var _count = 0;
    return function(){
        return ++_count;
    }
}

var count = counter();
console.log(count());
console.log(count());
console.log(count());

console.dir(count);
```