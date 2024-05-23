- JavaScript provides methods for primitive type also and they are not objects. 
- Object allow us store multiple values as properties, we have different type of objects in JS like `functions`.
- We can access methods and properties of strings, numbers, Boolean, symbol. 
- For accessing properties and methods, special object is created and after that work it is destroyed. 
- Object wrapper - `String`, `Number`, `Boolean`, `BigInt`, `Symnbol`.
- When we access any properties or method of primitive type, first special object is created using `ObjectWrapper` and then that method is accessed and then that special object destroyed. 
```js
let str = "Hello";
let upperCaseStr = str.toUpperCase();

let n = 12.3456;
let fixedN = n.toFixed(4);
```
- Primitive can't store any data, this means after accessing any method or properties, that wrapper method, destroyed.
```js
let str = "Hello";
str.test = "Hello";

console.log(str.test); // undefined
```
- After line 2, wrapper object would be destroyed and it has no idea about the test property of str variable. 
------------
Numbers
- Numbers are stored in 64 bit format IEEE 754 (double precision floating point number).
- Different ways to write a number -
```js
let num = 100000000;
num = 1_000_0000;
// two zero count
num = 12e2; // 1200
// e2 -> *100
// e-2 -> /100
```
- Hexadecimal - starts with `0xfff` -> 255
- Binary -> `0b111` -> 8
- Octal -> `0o112` ->  74
- `num.toString(base)` -> return the string of the number with the given base (2 to 36).
- We can directly call the method on number using `..` two dot instead of first initializing into the variable.
```js
1123..toString(10);
(323).toString(2);
```
- `toFixed(n)` 
- Calculation `0.1 + 0.2 == 0.3 // false`
- In decimal number system, if we divide any number with 10 or any power of 10, it would work find but if we divide by 3, then number would hard to represent in decimal because it will have endless decimal part. 
- Same in binary, number divide by 2 or it power, work fine but divide by 10 become an endless fraction.
- `isNaN(value)` convert `value` to number and then check it is equal to NaN or not.
- `isFinite(value)` convert `value` to number and then check it is a regular number and it is not equal to `NaN`, `Infinity`, `-Infinity`.
```js
isNaN(NaN); // true
isNaN("Str"); // true
isFinite("13"); // true
isFinite("sf"); // false
```
- `Number.isNaN()` and `Number.isFinite()` are more strict function, they don't convert the value. 
- `Object.is(a,b)` it is same as `===` operator but it has only 2 difference that is
```js
Object.is(NaN,NaN); // true
Object.is(0,-1); // false
```
- `parseInt()` and `parseFloat()`
- `parseInt(str, radix)`
- Decimal number stored with precision in number and if we want, how the number stored in the memory, we can use `num.toFixed(20)` method.
-----------------
Strings
- UTF-16
- backticks provide a functionality to write a multiline string. 
- Backtick allow us to write a template function before the first backtick and this feature known as [tagged templates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_templates);
- String length - `length` property.
- `str.at(pos)` method.
- Iterate over the string using `for..of` loop.
- String is immutable.
- `str.indexOf(substr[,pos])`
- `str.includes(substr[,pos]`
- `str.startsWith` & `str.endsWith`.
- `str.slice(start[,end])` - part a string start with start with not including end. 
- `str.substring(start[,end])` if end is small then start, then it simply swap the values (negative arguments treated as zero).
- `str.substr(start[, length])` - it is browser only feature. 
- `str.codePointAt(pos)` 
- `String.fromCodePoint(code)`
- `str.localeCompare(str2)`.
- `str.repeat(n)`.
---------------
Arrays
- `Array` store ordered collection like users, elements and so on.
```js
let arr = new Array();
arr = [];
arr = ['one', 'two', 'three];
```
- `lenght` property.
- `arr.at(-1)` at method. 
- `push` appends element at the end.
- `shift` the element from the begging and make second element first and return the first element.
- `for..of` loop.
```js
let digits = ['one', 'two', 'three'];

for (let digit of digits) {
	console.log(digit);
}
```
- Clear the array `arr.length = 0` and length property is not a elements in the array, it is actually highest index + 1.
- Another ways of creating an Array.
```js
let arr = new Array('Apple', 'Boy', 'Cat');

arr = new Array(3);
// it will create the array with length 3 and all the elements in the array are undefined. 
```
- `toString` return a comma separated string.
--------
Array Methods
- `.splice` method, it can do everything, insert, replace or remove the element from the array.
- `arr.splice(start[, deleteCount, elem1, .., elemn])` return the array of remove elements.
- `arr.slice([start],[end])` - it return an array between start and end and it won't modify the array.
- if object has property `Symbol.isConcatSpreadable`true then, complier spread the object and treat as an array.
- `arr.forEach(function(item, index, array) {}`
- `indexOf` method not able to find `NaN` in an array, we should use `includes` for that. 
- `arr.find((item, index, array) => {})`
- `arr.filter` return an array of matching elements.
- `arr.map` transform the array and return it.
- `arr.sort` sort the array in place and items sort as string by default.
- We can modify the behavior by passing the function as argument in the `sort` method.
- `arr.reverse()`
- `str.split(delim)` we can use this method on string to convert into the array depending on the delim.
- `arr.join(glue)` convert the array to string adding glue between the element.
- `arr.reduce((accum, item, index, array) , [initial])` return a value of array. if initial value is not present in the function then reduce function use first value as initial value and start iteration from second index.
- `Array.isArray(value)` use for checking object is array or not. 
------------------
Iterables
- *Iterables* objects are generalization of an array.
- When `for..of` starts it's called a method `Symbol.iterator` and it must return an iterator object which has `next` method.
- Afterward, `for..of` works on that return object and that `next` method should return an object with fields `done` and `value`.
```js
let range = {
    from: 1,
    to: 5,
};

range[Symbol.iterator] = function() {
    return {
        current: this.from,
        final: this.to,
        next() {
            if (this.current <= this.final) {
                return {
                    done: false,
                    value: this.current++,
                };
            }
            return {
                done: true,
            };
        },
    };
};

for (let num of range) {
    console.log(num);
}
```
- Array and strings are most widely used iterables.
- `iterables` are the object that implement the `Symbol.iterator` method.
- Array like objects are object they have indexes and length.
- `Array.from` take an `iterables` or array-like object and convert into real Array.
- `Array.from` break right with surrogate pairs also.
----------
Map and Set
- Objects are used for store keyed collection where array are used for ordered collection and Map also used for stored key collection but main difference with object is that, it can store any type of key.
```js
let map = new Map();

map.set('1', 'str1');
map.set(1, 'num1');
map.set(true, 'bool1');

map.get('1');
map.get(1);

map.size;

map.delete(1);

map.has(true);

map.clear();
```
- `map.keys()` return an iterable for keys.
- `map.values()` return an iterable for values;
- `map.entries()` return an iterable for entries `[key,value]` default.
- map.forEach (( value, key, map))