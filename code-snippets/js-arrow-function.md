## Arrow function

* Arrow functions – also called “fat arrow” functions (=>).
* Arrow functions make our code more concise, and simplify function scoping and the this keyword.
* Arrow functions are very similar to regular functions in behavior, but are quite different syntactically.

```
var foo = function(){
    return `Hey`;
}
```

```
var foo = () => {
    return `Hey`;
}
```

```
var foo = _ => {
    return `Hey`;
}
console.log(foo());
```

```
var greet = function(name){
    return `Hey ${name}`;
}

console.log(greet('Tom'));
```

```
var greet = name => `Hey ${name}`;

console.log(greet('Tom'));
```

```
var foo = function(name){
    return function(age){
        return function(city){
            return `${name} ${age} ${city}`;
        }
    }
}

console.log(foo('Sunny')(27)('Bangalore'));
```

```
var foo = (name) => (age) => (city) => `${name} ${age} ${city}`;

console.log(foo('Sunny')(27)('Bangalore'));
```
> Arrow function is not having it's own this, it will follow lexical approach (it will go till window)

```
"use strict";
var foo = () => {
    console.log(this);
}
foo();
```

```
var foo = function(name){
    this.name = name
    this.age = 26;
}

var user = new foo('Sunny', 27);
console.log(user.name);
console.log(user.age);
```

> You cannot use new keyword with arrow function

```
var foo = (name) => {
    this.name = name
    this.age = 26;
}

var user = new foo('Sunny', 27);
console.log(user.name);
console.log(user.age);
```
> Call, bind and apply will not work with arrow function

```
var name = 'Ross';
var tom = {
    name: 'Tom'
}

var foo = function foo(){
    console.log(this.name);
}

foo();
foo.call(tom);
```

```
var name = 'Ross';
var tom = {
    name: 'Tom'
}

var foo = () => {
    console.log(this.name);
}

foo();
foo.call(tom);
```

```
var name = 'Mike';
var obj = {
    name: 'Tom',
    foo: function() {
        console.log(this);

        var bar = function bar(){
            console.log(this.name);
        };
        bar();
    }
};

obj.foo();
```

```
var name = 'Mike';
var obj = {
    name: 'Tom',
    foo: function() {
        console.log(this);

        var bar = () => {
            console.log(this.name);
        };
        bar();
    }
};

obj.foo();
```

```
var name = "Mike";
(function(){

    let obj = {
        name: 'Tom',
        greet: function(){
            setTimeout(function(){
                console.log(this.name);  
            }, 1000);
        }
    };

    console.log(obj.greet());    
})();
```

```
var name = "Mike";
(function(){

    let obj = {
        name: 'Tom',
        greet: function(){
            setTimeout(() => {
                console.log(this.name);  
            }, 1000);
        }
    };

    console.log(obj.greet());    
})();
```


