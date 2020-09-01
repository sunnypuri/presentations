## Higher order function

A Higher Order function is a function that receives a function as an argument or returns the function as output.


Examples: forEach, map, reduce, filter, bind



> Using for loop

```
var list = [1, 2, 3, 4, 5];

for(let i=0; i<list.length; i++) {
    list[i] = list[i]*2;
}
console.log(list);
```


> Using forEach

```
var list = [1, 2, 3, 4, 5];

list.forEach(function(item, i, arr){
    arr[i] = arr[i] * 2;
});
console.log(list);
```



> Using map

```
var output = list.map(function(item){
    return item * 2;
});

console.log(output);
```


> Filter Odd values

```
var output = list.filter(function(item){
    return item % 2 !== 0;
});

console.log(output);
```



> Sum all values

```
var output = list.reduce(function(result, item) {
    return result + item;
}, 0);

console.log(output);
```

```
var output = list.map(i=> i*3).filter(i => i%2!==0).reduce((r, i) => r+i, 0);
console.log(output);
```


> Double using reduce

```
var output = list.reduce(function(result, item) {
    result.push(item * 2);
    return result;
}, []);

console.log(output);
```



```
function greet() {
    console.log('Hey');
}

greet();
greet.call();
greet.apply();
console.log(greet.bind()());
```