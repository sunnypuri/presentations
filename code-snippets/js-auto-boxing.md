## Auto boxing

When you try to call a property or method on certain primitive types,
JavaScript will first convert it into a temporary wrapper object, and access the property / method on it,
without affecting the original.

Auto boxing is a process where compiler convert primitive data types to their corresponding Object wrapper class

```
var name = 'Sunny';
console.log(`Hey ${name}`);
```

```
var name = 'Sunny';
var score = 100;

// Without autoboxing
console.log(`Hey ${name}, your score is ${score}`);

// With autoboxing
console.log(`Hey ${name}, your score is ${String(score)}`);
```

```
// Without autoboxing
console.log("Helloo".toUpperCase());

// With autoboxing
console.log(new String("Helloo").valueOf().toUpperCase());
```

---

```
// Without autoboxing
var name = "Sunny";
console.log(name.length);

// With autoboxing
var name = "Sunny";
console.log(new String(name).length);
```

---

```
(function(){
    var name = "Sunny";
    name.toString = function(){return `Hey`};
    console.log(name.toString());
    console.log(typeof name);
})();
```

```
(function(){
    var name = new String("Sunny");
    name.toString = function(){return `Hey`};
    console.log(name.toString());
    console.log(typeof name);
})();
```

---
