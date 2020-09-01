## Method chaining

Chaining Methods, also known as Cascading, means repeatedly calling one method after another on an object, in one continuous line of code. 


#### Auto boxing
When you try to call a property or method on certain primitive types, JavaScript will first convert it into a temporary wrapper object, and access the property / method on it, without affecting the original.

```
"    Hello   ".trim().toUpperCase().split("").reverse().join("-");
```

```
"  Hello  ".trim();
new String("   Hello  ").valueOf().trim();
```

```
function Calculate(value) {
    this.num = value;
}

Calculate.prototype.add = function (value){
    this.num += value;
    return this;
}

Calculate.prototype.subtract = function (value){
    this.num -= value;
    return this;
}

Calculate.prototype.multiply = function (value){
    this.num *= value;
    return this;
}

Calculate.prototype.divide = function (value){
    this.num /= value;
    return this;
}

Calculate.prototype.display = function (){
    console.log(this.num);
    return this;
}
```

```
var obj = new Calculate(5);

obj.add(1).subtract(2).multiply(2).divide(2).display().add(1).display();
```

```
obj.add(1)
    .subtract(2)
    .multiply(2)
    .divide(2)
    .display()
    .add(1)
    .display();
```