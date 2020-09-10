## Pipe/Composition

Function composition is the process of combining two or more functions to produce a new function.

#### Pipe
```
function _pipe(...fns){
    return function(value){
        for(fn of fns){
            value = fn(value);
        }
        return value;
    }
}
```

#### Compose
```
function _compose(...fns){
    return _pipe(...fns.reverse());
}
```

> Example 1:
```
function pipe(fn1, fn2) {
    return function(value){
        return fn2(fn1(value));
    }
}

function compose(fn2, fn1) {
    return function(value){
        return fn2(fn1(value));
    }
}

function _toUpperCase(str) {
    return str.toUpperCase();
}


function _toLowerCase(str) {
    return str.toLowerCase();
}



var pipeOutput = pipe(
    _toUpperCase,
    _toLowerCase
)('Hello');


console.log(pipeOutput);

var composeOutput = compose(
    _toUpperCase,
    _toLowerCase
)('Hello');

console.log(composeOutput);
```


> Example 2:
```
function _reverse(arr) {
    return arr.reverse();
}

function _split(delimiter) {
    return function(str){
        return str.split(delimiter);
    }
}

function _join(delimiter) {
    return function(arr){
        return arr.join(delimiter);
    }
}

function _log(label) {
    return function(value) {
        console.log(label, value);
        return value;
    }
}

function _toUpperCase(str) {
    return str.toUpperCase();
}


var reverseString = _pipe(
    _split(""),
    _log('After split:'),
    _reverse,
    _join(""),
    _toUpperCase
);


console.log(reverseString('Hello'));
```

> Example 3:
```
function _mod(modulo) {
    return function(value){
        return value % modulo;
    }
}

function _equal(equalTo) {
    return function(value) {
        return value === equalTo;
    }
}


var isEven = _pipe(
    _mod(2),
    _equal(0)
);

console.log(isEven(4));
```

#### Example using map, reduce, filter
```
var compose = (...fns) => x => fns.reduceRight((v, f) => f(v), x);
var pipe = (...fns) => x => fns.reduce((v, f) => f(v), x);


function _map(callback){
    return function(arr){
        const list = [];
        for(let i=0; i < arr.length; i++){
            list.push(callback(arr[i]));
        }
        return list;
    }
}

function _filter(callback) {
    return function(arr){
        const list = [];
        for(let i=0; i < arr.length; i++){
            if(callback(arr[i])){
                list.push(arr[i]);
            }
        }
        return list;
    }
}

function _reduce(callback, acc) {
    return function(arr) {
        for(let i=0; i < arr.length; i++){
            acc = callback(arr[i], acc);
        }
        return acc;
    }
}


function _log(label) {
    return function(value) {
        console.log(label, value);
        return value;
    }
}

function multiply(x) {
    return function (y){
        return x*y;
    }
}

var isOdd = v => v%2 == 1;

var data = [1, 2, 3, 4, 5];

var sum = function (x, y) {
    return x + y;
}

var output = pipe(
    _map(multiply(3)),
    _filter(isOdd),
    _log('After filter: '),
    _reduce(sum, 0)
)(data);

console.log(output);
```