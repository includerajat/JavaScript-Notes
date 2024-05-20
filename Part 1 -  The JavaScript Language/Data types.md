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