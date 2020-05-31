## Javascript Basics

> Data types 

```
number
string
boolean
null
undefined

bigint
object
symbol
```

```
console.log(typeof 10);
console.log(typeof "Hey");
console.log(typeof true);
console.log(typeof null);
console.log(typeof undefined);

var log = console.log;

log(typeof 10n);
log(typeof window);
log(typeof Symbol("name"));
```

```
var name = "Sunny";
```

```
function foo(){
    return `Hello`;
}
```

> Higher order function

```
var foo = function(){
    return `Hello`;
}
foo();
```

> Arrow function

```
var foo = () => {
    return `Hello`;
}
foo();
```

> Inner function

```
var foo = function(){
    function bar(){
        return `Hello`;
    }
    return bar;
}

foo()();
```

> Above example is also an example of currying and closure

> Callback

```
var foo = function(){
    return `Hello`;
}

var bar = function(cb){
    return cb();
}

bar(foo);
```
