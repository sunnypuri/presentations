## Objects

### Data types

Primitive	       number, string, boolean, undefined, null, bigInt, symbol

Non-primitive	   object, arrray, function


> Primitive example (copy values)
```
var name = 'Tom';
var copyName = name;

copyName = 'Mike';
console.log(name);
console.log(copyName);
```

> Non primitive example (copy Reference)

```
var obj = {
    name: 'Tom',
    age: 27
}

var copyObj = obj;
copyObj.name = 'Mike';

console.log(obj);
console.log(copyObj);

console.log(obj === copyObj);    // Both are objects so it will perform reference comparision
```

> Array example

```
var list = [1,2,3];
var copyList = list;

copyList.push(4);
console.log(list);
console.log(copyList);
```

```
var list = [1,2,3];
var list2 = [1,2,3];
console.log(list == list2);  // It will match reference, and in this case reference are not same
```


### Objects 

- Object literals - {key: value}
- new Operator (Built in function like Array, String, Object, RegExp(), Boolean(), Date())
- Object.create()


#### Object literals

```
var obj = {
    name: 'Mike',
    getName: function(){
      return this.name;  
    },
    greet(){
        return `Hey ${this.name}`;
    }
}

console.log(obj.getName());
console.log(obj.greet());

console.log(new obj.getName());     // getName {}
console.log(new obj.greet());       // TypeError: obj.greet is not a constructor

console.dir(obj.getName);
console.dir(obj.greet);

console.log(obj.getName.hasOwnProperty('prototype'));
console.log(obj.greet.hasOwnProperty('prototype'));
```

---


#### Get and Set in Objects

```
var obj = {
    name: 'Mike',
    age: 27,
    city: 'Bangalore',

    get getCity(){
        return this.city;
    },
    set setCity(value){
        this.city = value;
    }
}

obj.setCity = 'Pune';
console.log(obj.getCity);
```

---

#### PropertyDescriptor

```
var obj = {
    name: 'Mike',
    age: 27,
}


console.log(Object.getOwnPropertyDescriptor(obj, 'name'));
console.log(Object.getOwnPropertyDescriptors(obj));

Object.defineProperty(obj, 'city', {});

console.log(obj);
console.log(Object.getOwnPropertyDescriptors(obj));


console.dir(obj);
console.log(obj.propertyIsEnumerable('city'));

Object.defineProperty(obj, 'city', {
    value: 'Pune'
});
obj.city = 'Bangalore';

Object.defineProperty(obj, 'city', {
    value: 'Pune',
    writable: true
});
obj.city = 'Bangalore';


Object.defineProperty(obj, 'city', {
    value: 'Pune',
    writable: true,
    configurable: true
});


obj.city = 'Bangalore';
delete obj.city;

Object.defineProperty(obj, 'city', {
    value: 'Pune',
    writable: true,
    configurable: true,
    enumerable: true
});


for(key in obj){
    console.log('Key', key);
}

console.log(obj);
```

> NIT
```
Object.defineProperty(obj, 'getCity', {
    get getCity(){
        return this.city;
    },
    set setCity(value){
        this.city = value;
    },
});
```

=========================================

#### new

Object are built by Constructor calls (via new)
Constructor calls links to its own prototype

```
var boolean = new Boolean(false);
console.log(boolean);
console.log(boolean instanceof Boolean);
console.log(boolean instanceof Object);     // It is true because of prototype chain
console.log(typeof boolean);
console.log(boolean.valueOf());

console.log(Object.getPrototypeOf(boolean));    // Boolean.prototype
console.log(Object.getPrototypeOf(boolean) == Boolean.prototype);   // true
```

```
var obj = new Object();
obj.name = 'Tom';
console.log(obj);
console.log(obj instanceof Object);
console.log(typeof obj);

console.log(Object.getPrototypeOf(obj));
console.log(Object.getPrototypeOf(obj) == Object.prototype);

console.log(obj.constructor == Object);
console.log(obj.__proto__ == Object.prototype);
```

================================================================

#### Object.create()

The Object.create() method creates a new object, 
using an existing object as the prototype of the newly created object.

Syntax: Object.create(proto, [propertiesObject])

```
var obj = Object.create(null);  // In case of null - it will not have any prototype property
obj.name = 'Tom';
console.log(obj);
console.log(obj.toString());
```

```
var obj = Object.create({});  
obj.name = 'Tom';
console.log(obj);
console.log(obj.toString());
```

```
var obj = Object.create(Object.prototype);   // It means obj is inheriting all properties of Object.prototype
obj.name = 'Tom';
console.log(obj);
console.log(obj.toString());
```

```
var obj = Object.create(null);
console.log(obj);

Object.setPrototypeOf(obj, Object.prototype);
console.log(obj);
```

```
var user = {
    name: 'Tom',
}

var tom = Object.create(user);
tom.name = 'Mike'
console.log(tom.name);
console.log(tom.__proto__.name);
```

#### Object.create with propert descriptors

```
var user = {
    name: 'Tom',
}

var tom = Object.create(user, {
    age: {
        value: 27,
        writable: true,
        configurable: true,
        ennurable: true
    }
});

console.log(tom);
```

---

#### Prototype chain

```
var obj1 = {
    a: 1,
    b: 2
}

var obj2 = Object.create(obj1);
obj2.c = 3;
obj2.d = 4;
console.log(obj2);

var obj3 = Object.create(obj2);
obj3.e = 5;
delete obj3.a;  // not work for inherited property
delete obj3.__proto__.__proto__.a;  // deletes property from obj1
console.log('b' in obj3);
console.log('valueOf' in obj3);
console.log(obj3.hasOwnProperty('b'));       // false for inherited property
console.log(obj3.hasOwnProperty('valueOf')); // false for inherited property

console.log(Object.keys(obj3)); // Owned properties

// Iterates only ennurable property
for(key in obj3){
    console.log(key);
}

for(key in obj3){
    if(obj3.hasOwnProperty(key)){
        console.log('Owned', key);    
    }
}

console.log(Object.getOwnPropertyNames(obj3));
```

> Ways to create objects
```
var obj = {};
var obj = new Object();
var obj = Object.create({});
var obj = Object.create(Object.prototype);
```


```
var obj = {
    a: 10
}

var obj2 = {
    __proto__: obj,
    b: 20
}

console.log(obj2);
```
---

#### Object.assign()

The Object.assign() method copies all enumerable own properties from one or more source objects to a target object.
It returns the target object.

Object.assign(target, ...sources)

```
var tom = {
    name: 'Tom'
}

var mike = {
    name: 'Mike',
    age: 7
}

var obj = Object.assign({}, mike, tom);
console.log(obj);
```

---

#### Object.seal()

Object.seal() is used to create a non-extensible object

```
var obj = {
    name: 'Mike',
    age: 27
}


Object.seal(obj);
obj.name = 'Tom';
delete obj.age;     // It will not delete in case of seal
obj.city = 'Bangalore';
console.log(obj);
```
---

#### Object.freeze()

Object.freeze() is used to create a non-extensible object, 
but where the existing value of the object is prevented from being changed 

```
var obj = {
    name: 'Mike',
    age: 27
}

Object.freeze(obj);
obj.name = 'Tom';
delete obj.age;     // It will not delete in case of seal/freeze
obj.city = 'Bangalore'; // It will not extend in case of freeze
console.log(obj);
```