## use strict

> It makes debugging easier

```
flag = true;
console.log(flag);  // Output: true
```

> By enabling strict mode, we enter into a restricted variant of JavaScript that will not tolerate the usage of variables before they are declared.

```
'use strict';
flag = true;
console.log(flag);	// Output: Uncaught ReferenceError: flag is not defined
```

> Please make sure that "use strict" is at the top of your scripts, otherwise strict mode may not be enabled.

```
flag = true;
'use strict';
console.log(flag);  // Output: true
```

> If we want to invoke strict mode only in functions instead of whole script file, just use 'use script' in top of that function.

```
flag = true;
console.log(flag);  // Output: true
function foo() {
    'use strict';
    a = 10;
    console.log(a); // Output: Uncaught ReferenceError: a is not defined
}
foo();
```

> Cannot use reserved keyword for example: let, private, protected, public, static

```
"use strict";
var let = 1;
console.log(let);   // Unexpected strict mode reserved word
```

```
"use strict"
var foo = 1;
delete foo;
console.log(foo);
```

```
"use strict"
var foo2 = () => {};
delete foo2;
console.log(foo2);
```

```
"use strict";
var a = 2;
eval("var a = 10");
console.log(a);
```

```
"use strict";
function foo(){
    console.log(this);
}
foo();
```

```
var obj = {
    foo: function() {
        "use strict";
        console.log(this);

        function bar(){
            console.log(this);
        }
        bar();
    }
};
console.log(obj.foo());
```
