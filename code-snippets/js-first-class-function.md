## First class function

JavaScript has first-class functions. This means functions can be treated like other values.

- Functions can be assigned to a variables
- Functions can be returned from other functions
- Functions can be passed as arguments to other function (aka callback)


```
function foo(){
    console.log('Hello');
}

foo();
```


> Functions can be assigned to a variables

```
var foo = function foo(){
    console.log('Hello');
}

foo();
```


> Functions can be returned from other functions

```
function foo(){
    function greet(){
        console.log('Hello');
    }

    return greet;
}

foo()();
```


>Functions can be passed as arguments to other function

```
function greet(){
    console.log('Hello')
}

function foo(fn) {
    fn();
}

foo(greet);
```


> Arrow function

```
var foo = ()=>{
    console.log('Hello');
}

foo();
```


> IIFE (Anonymous function)

```
(function (){
    console.log('Hello');
})();
```

```
(function foo(){
    console.log('Hello');
})();
```

> Other ways to write IIFE

```
(function(){ console.log('Hey')})();
(function(){ console.log('Hey')}());
!function(){ console.log('Hey')}();
~function(){ console.log('Hey')}();
+function(){ console.log('Hey')}();
-function(){ console.log('Hey')}();
(()=> `Hey`)();
```


> Is function object?

```
function greet() {
    console.log(this.x);
}

greet.x = 10;
greet.y = false;

console.dir(greet);
```

