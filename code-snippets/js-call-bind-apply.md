## Call, bind and apply

> call (Function.prototype.call) and apply(Function.prototype.apply) is used to invoke the function immediately.

> bind (Function.prototype.bind) method creates a new function and sets the this keyword to the specified object, which can be called ater in certain events when it's useful.

> call, bind and apply methods are used to set `this` keyword independent of how the function is called.

```
function foo(param1, param2){
    console.log(this);
}

console.log(foo);

console.dir(foo);

console.log(foo.name);

console.log(foo.toString());

foo.age = 27;
console.log(foo.age);

foo.__proto__.age = 30;

console.log(foo.age);


foo();
foo.call();
foo.apply();
foo.bind()();
```

```
function foo(){
    console.log(this);
}

foo();
```

> In simple terms we use call, bind and apply to change the context (this)

```
function foo(){
    console.log(this);
}
foo.call('Tom');
foo.call(1);
foo.call(true);
```

```
"use strict";

function foo(){
    console.log(this);
}

foo();
foo.call({});
foo.call('Tom');
```

```
function foo(param1, param2, param3){
    console.log(this);
    console.log(param1);
    console.log(param2);
    console.log(param3);
}

foo(1,2,3);
foo.call(this,1,2,3);
foo.apply(this, [1,2,3]);
foo.bind(this, 1, 2, 3)();
```

```
function sum(){
    var total = 0;
    for(var value of arguments){
        total += value;
    }

    return total;
}

sum(1,2,3,4,5);
sum.call(null, 1,2,3,4,5);
sum.apply(null, [1,2,3,4,5]);
sum.bind(null, 1,2,3,4,5)();
```

```
Math.max(1,2,3,4,5,6);
```

```
var nums = [1,2,3,4,5,6];
Math.max.apply(null, nums);
```

```
var nums = [1,2,3,4,5,6];
Math.min.apply(null, nums);
```

> We can directly use bind with function expression

```
var foo = function(){
    console.log(this);
}.bind('Hey');

foo();
```


> Objects

```
var obj = {
    name: 'Tom',
    foo: function() {
        console.log(this);
        console.log(this.name);
    }
};

obj.foo();
```

```
var obj = {
    name: 'Tom',
};

var foo = function() {
    console.log(this);
    console.log(this.name);
}

foo();
foo.call(obj);
```

```
var name = 'Mike';
var obj = {
    name: 'Tom',
    foo: function() {
        console.log(this);

        function bar(){
            console.log(this.name);
        }
        bar();
        bar.call(this);
        bar.apply(this);
        bar.bind(this)();
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

        var bar = function bar(){
            console.log(this.name);
        }.bind(this);
    }
};

obj.foo();
```


> Quizzes

```
var foo = function() {
    console.log(this)
}.bind(1);

foo();
```

```
var obj = {
    foo: function(){
        console.log(this);
    }.bind('Hey')
}

obj.foo();
```

```
var mike = {
    name: 'Mike'
}

var obj = {
    name: 'Tom',
    log: function(){
        console.log(this.name);
    }
}

obj.log();
obj.log.call(mike);
```

```
var mike = {
    name: 'Mike'
}

var obj = {
    name: 'Tom',
    log: function(){
        console.log(this.name);
    }.bind(mike)
}

obj.log();
```

```
var foo = function() {
    console.log(this)
}.bind(1);
 
 var obj = {
    callFoo : foo
 }
obj.callFoo();
```

```
var name = 'Mike';
var foo = function() {
    console.log(this.name)
};
 
 var obj = {
     name: 'Tom',
     callFoo : foo
 }
obj.callFoo();
```

```
var name = 'Mike';
var foo = function() {
    console.log(this.name)
};
 
 var obj = {
     name: 'Tom',
     callFoo : foo
 }
var callFoo = obj.callFoo;
callFoo();
```

```
var obj = {
    name: 'Mike',
    foo: {
        name: 'Tom',
        log: function(){
            console.log(this.name);
        }
    }
};

obj.foo.log();
obj.foo.log.call(obj);
```

```
var name = 'Ross';
var obj = {
    name: 'Mike',
    foo: {
        name: 'Tom',
        log: function(){
             setTimeout(function(){
                console.log(this.name);  
            }, 1000);
        }
    }
};

obj.foo.log();
```

```
var name = 'Ross';
var obj = {
    name: 'Mike',
    foo: {
        name: 'Tom',
        log: function(){
             setTimeout(function(){
                console.log(this.name);  
            }.bind(this), 1000);
        }
    }
};

obj.foo.log();
```

```
var names = ['Mike', 'Tom'];
var friends = ['Ross', 'Jeff'];
names.push(friends);


names.push.apply(names, friends);
console.log(names);
```

```
const add = function(a,b){
  console.log(a+b)
};

setTimeout(add,1000,1,2);
```