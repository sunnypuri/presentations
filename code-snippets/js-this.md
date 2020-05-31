## This

```
console.log(window);
```

```
console.log(this);
```

```
console.log(this === window) // Prints true on console.
```

```
var name = 'Sunny';
console.log(name);
console.log(window.name);
console.log(this.name);
```

```
function greet() {
    console.log('Hey..');
}

greet();
window.greet();
this.greet();
```

```
function foo(){
    console.log(this);
}
foo();

function foo(){
    console.log(this);
}
new foo();
```

```
function foo(){
    console.log(this);
    debugger;
}
foo();
```

```
var obj = {
    log: function() {
        console.log(this);
    }
};
obj.log();
console.log(obj);
```

```
var obj = {
    log: function() {
        console.log(this);
    }
};
var callingLog = obj.log;
console.log(callingLog());
```

> this can be determined by the calling context

```
var obj = {
    foo: function() {
        console.log(this);

        function bar(){
            console.log(this);
        }

        bar();
    }
};

console.log(obj.foo());
```

```
var obj = {
    foo: function() {
        console.log(this);

        function bar(){
            this.x = 10;
            console.log(this);
        }

        bar();
        console.log(window.x);
    }
};

console.log(obj.foo());
```

```
var obj = {
    foo: function() {
        console.log(this);
        var self = this;
        function bar(){
            self.x = 10;
            console.log(self);
        }

        bar();
        console.log(self.x);
    }
};

console.log(obj.foo());
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
            setTimeout(function(){
                console.log(this.name);  
            }.bind(this), 1000);
        }
    };

    console.log(obj.greet());    
})();
```

```
"use strict";
var foo = () => {
    console.log(this);
}
foo();
```

```
"use strict";
var foo = {
    bar: function(){
        console.log(this);
    },
    baz: () => {
        console.log(this);
    }
}

foo.bar();              // Output: foo object
foo.baz();              // Output: window (even with "use strict");

var bar = foo.bar;
var baz = foo.baz;

bar();                  // Output: window or (undefined in case of "use strict")
baz();                  // Output: window
```
