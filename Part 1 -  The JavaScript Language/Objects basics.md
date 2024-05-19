- Use for store keyed collection of various data. 
- Figure bracket - `{..}` -> Object Literal.
- Object creation -
```js
let user = new Object();
let user = {};
```
- remove a property from object using `delete` keyword.
```js
let user = {name: Rajat};
delete user.name;
```
- There are two notations, with the help of that, we can access object value -
	- dot notation `obj.name`.
	- square bracket notation `obj["name"]`.
- when key name same as the value variable then we can use property shorthand like this -
```js
let user = {
	name: name,
	age: age,
}

let user = {
	name,
	age,
}
```
- `__proto__` object property can't set to the non-object value, it will ignore. 
- `in` operator -
```js
"key" in object;
```
- Walk over all the keys of the object, we can use `for..in` loop.
```js
for (key in object) {

}
```
- Object keys order, number are sorted in ascending order and strings order as creation order.
- It is simple object, we also have different types of object -
	- Arrays
	- Date
	- Error
---------
Copy
- Object are stored and copied by **reference**.
- Primitive value always copied as whole value.
- Comparison by reference. 
- Comparison like `< >` or compare with number, it convert the object into number.
- `Object.assign(dest, ...sources)`
```js
let userPermissions = {};
let permission1 = {canView: true};
let permission2 = {canEdit: true};

Object.assign(userPermissions, permission1, permission2);
```
- If object properties contain primitive values, then it works totally fine, if it contain reference than it copied the reference instead of copying the object itself.
- For fix this, we have to use deepCloning or structredCloning and we have `structureClone` method.
```js
let user = {
	name: "Rajat",
	sizes: {
		width: 10,
		height: 10,
	},
};

let cloneUser = structuredClone(user);
```
- When object has a function property, it fails.
- For that we can use `_.cloneDeep(obj)` from the lodash library.
- `...` spread operator perform shallow copy not the deep copy.
-------
Memory management 
- It happens automatically. 
- JavaScript remove the something from the memory depending on the reachability. 
- If something is not reachable, there is no meaning of remain that thing in the memory.
- It seems like `garbage collector` use `dfs` algorithm to find the reachable island, the island which become unreachable remove from the memory. 
--------
Object methods and this
- Actions are represents in JavaScript by functions in properties.
```js
let user = {};
user.sayHi = function() {
	console.log('Hi!!');
}
```
- Function that is a property of the object called *method*.
- Shorthand syntax - 
```
let user = {
	sayHi() {
		console.log("Hiii);
	}
}
```
- Sometime `object` method needs to access the yourself information for do the job then object method use `this` keyword.
- `this` value is the object "before dot", used to call the method.
- `this` keyword used anywhere, it should not be any object property.
```js
function sayHi() {
	console.log(this.name);
}
```
- in simple words, `this` value depend on the context where it calls, usually it call with object context. 
- Arrow functions don't have any this, if we use this in arrow function then it take this value from the outer normal function. 
------------
'new' operator
 - sometimes we need to create many similar objects, that can be done using constructor functions.
 - There are some convention for using constructor functions -
	 - They are regular functions but their first character of function name should be capital.
	 - And always call with `new` keyword.
- What `new` operator actually do -
	- Create a empty object and assigned to the `this`.
	- Execute the body of the function.
	- Return the `this` object.
- Constructor use for implement reusable object creation code.
- We can create a constructor function which can use only one time like this -
```js
let user = new function(){
	this.name = "John";
	this.isAdmin = false;
}
```
- It is same used by the `Math` object itself. 
- We can check that function is called by new keyword or not by using `new.target` method.
- If it undefined, it means function called without `new` operator.
```js
function User(name) {
	if(new.target == undefined){
		return new User(name);
	}
	this.name = name;
}
```
- We can omit paratheses.
```js
let user = new User();
let user = new User;
```
- We can also define the methods in constructor function.
- JavaScript provide constructor functions for built in object like `Date`, `Set` and others.
----------
Optional chaining (?.) (ECMA 2020)
- It is a safe way to access the nested properties of the object. 
- It is new addition in JavaScript and old JS engine require polyfills for the same.
- `?.` stops the evaluation if value left of this is null or undefined and return undefined. 
- We should not use this `?.` over use, otherwise code may prone to error and it difficult to find.
- `?.` it is not a operator but it is a syntax construct and it also have variant also `?.[]` or `?.()`.
- We can only use optional chaining in reading or deleting not in writing. 
----------
Symbol type
- It is unique identifier and it value can be created using `Symbol()`.
- We can also give a description, use for debugging `Symbol(description)`.
- symbol.description.
- Symbol keys are skipped from `for..in` loop (hiding symbolic property).
- `Object.keys(user)` also ignore the symbolic keys.
- Global symbols return the same symbol depending on their name, same name returns same symbol.
- `Symbol.for(key)` it return symbol depending on the key.
- `Symbol.keyFor(sym)` return symbol depending on the key.
- There are some well know system Symbol which JavaScript uses internally -
	- Symbol.hasInstance
	- Symbol.isConcatSpreadable
	- Symbol.toPrimitive
	- ...
- `Reflect.ownKeys(obj)` it returns all the keys of the object and `Object.getOwnPropertySymbols(obj)` return all symbol properties of the object.
- Use for creating hidden properties and we can use for fine tune the JavaScript behaviour using system Symbols.
-----------
Object primitive
- Result of `+` operator with two objects, can be another object.
- All objects are true.
- Numeric conversion happen when `-`, mathematical functions.
- Object to string -> when we expect string like in function arguments or object keys.
- Object to number -> when we do maths  (-, <. >).
- Object to default -> +, ==

**To do the conversion, JavaScript tries to find and call three object methods:**

1. Call `obj[Symbol.toPrimitive](hint)` – the method with the symbolic key `Symbol.toPrimitive` (system symbol), if such method exists,
2. Otherwise if hint is `"string"`
    - try calling `obj.toString()` or `obj.valueOf()`, whatever exists.
3. Otherwise if hint is `"number"` or `"default"`
    - try calling `obj.valueOf()` or `obj.toString()`, whatever exists.

- `obj[Symbol.toPrimitive]` it must return a primitive value.
- `obj.toString()` returns a string `[object object]` and `obj.valueOf()` return a object itself.