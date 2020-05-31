## Hoisting

> Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.
> JavaScript hoists function declarations and variable declarations to the top of the current scope.

> Variable hoisting

> Function hoisting

```
var foo = "foo";
console.log(foo);
```

```
console.log(foo);
var foo = "foo";
```

```
console.log(foo);   // ReferenceError: foo is not defined
```

```
console.log(foo);   // ReferenceError: foo is not defined
foo = "foo";
```

```
console.log(typeof foo);   // Output: undefined
```

```
console.log(foo);
var foo = "foo";

var foo;
console.log(foo);
foo = "foo";
```

```
function foo(){
    console.log(foo);
    var foo = "foo";
}

foo();
```

```
var foo = "bar";
function greet(){
    console.log(foo);
    var foo = "foo";
}

greet();
```
 
> Explanation

```
var foo = "bar";
function greet(){
    var foo;
    console.log(foo);
    foo = "bar";
}

greet();
```

> Function hoisting

```
foo();
function foo(){
    console.log('Hello');
}
```

```
foo();
var foo = function foo(){
    console.log('Hello');
}
```

> Quizzes

```
console.log(foo); // Output: ??
var foo = "foo";
```

```
function foo() {
    a = 100;
    var b = 200;
}

foo();
console.log(a);     // Output: ??
console.log(b);     // Output: ??
```

```
function foo() {
    console.log(a); // Output: ??
    a = 100;
}

foo();
```

```
var a = 100;
function foo() {
    console.log(a); // Output: ??
    a = 200;
}

foo();
```

```
var a = 100;
function foo() {
    console.log(a); // Output: ??
    var a = 200;
}

foo();
```

```
function foo(){
    console.log("Hey");
}

foo();

function foo(){
    console.log("Hello");
}
```

```
console.log(typeof foo);
function foo(){
    return "bar";
}
var foo = "bar";
```

```
function foo(){
    return "bar";
}
var foo;
console.log(typeof foo);
```

```
if(true){
    function foo(){
        console.log(1);
    }
}else{
    function foo(){
        console.log(2);
    }
}

foo();
```

```
function foo(){
    bar();

    return;

    function bar(){
        console.log("bar");
    }
}

foo();
```

```
var x = 7,x = 8, x;
console.log(x);
```

```
// Callback demo
function foo(x){
    x();
}
foo(function(){console.log("bar")});


function foo(x){
    x();
    function x(){
        console.log("foo");
    }
}

foo(function(){console.log("bar")});
```

```
foo();

function foo() {
  console.log(1);
}

var foo = function() {
  console.log(2);
};

function foo() {
  console.log(3);
}

foo();
```
