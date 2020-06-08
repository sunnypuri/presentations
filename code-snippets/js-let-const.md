## Let and const

> Up until now, the only way to declare a variable in javaScript was to use the keyword var.
> In ES6, there are two new ways to declare variables in javascript: let and const.

```
var name = 'Mike';
console.log(window.name);
```

```
console.log(name);
var name = 'Mike';
```

```
let name = 'Mike';
console.log(window.name);
```

```
console.log(name);
let name = 'Mike';
```

```
let name = 'Mike';
name = 'Tom';
console.log(name);
```

```
let name = 'Mike';
let name = 'Tom';
console.log(name);
```

```
let x = 7, x = 8, x;
console.log(x);
```

```
x = 20;
let x = 10;
console.log(x);
```

```
const name = 'Mike';
console.log(name);
```

```
const name = 'Mike';
name = 'Tom';
console.log(name);
```

```
const obj = {
    name: 'Tom',
    greet: function(){
        console.log(`Hey ${this.name}`);
    }
}

obj.name = 'Mike';
obj.greet();
```

```
const friends = ['Mike', 'Tom'];
friends.push('Ross')
console.log(friends);
```

> Always use const for functions and objects

```
const foo = function(){
    console.log('Hey');
}
foo();
```

```
let name = 'Mike'
{
  let name = 'Tom'
  console.log(name);
}
console.log(name); 
```

```
let name = 'Mike'
{
    console.log(name);
    let name = 'Tom'
  
}
console.log(name);   
```

> so let's understand when to use let

```
for(var i=0 ; i<4; i++){
    console.log(i);
}

console.log(i);
```

```
for(let i=0 ; i<4; i++){
    console.log(i);
}

console.log(i);
```

```
var x = 10;
if(true){
    let x = 20;
}
console.log(x);
```

```
for (var i = 0; i < 5; i++) {
  setTimeout(function(){
    console.log(i);
  });
}
```

```
for (let i = 0; i < 5; i++) {
  setTimeout(function(){
    console.log(i);
  });
}
```

```
for (var i = 0; i < 5; i++) {
    (function(j){
        setTimeout(function(){
            console.log(j);
        });
    })(i);
}
```

```
for (var i = 0; i < 5; i++) {
  setTimeout(console.log, 0, i);
}
```

```
let a;
```

```
const a;     // Missing initializer in const declaration
```