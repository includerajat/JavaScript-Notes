- We can run JavaScript anywhere, we only need JavaScript engine.
- Running JavaScript in browser, we can use `<script>` tag, if `src` attribute set then content under this tag ignored. 
- Don't require to pass `type` or `language` attribute anymore.
- `alert()` is a browser specific command.
- **Syntax constructs** are building block of programming language, they define the structure of the language.
- It should be a good practice to end a statement with semi colon.
- We can comments in JavaScript language for better understanding of the code.
```
// Sing line comment
/*
Multi line comment 
*/
```
- In ES5 (2009), new feature introduce and also modified some existing one but JavaScript care about the compatibility of the old code, that's why some feature is not enable by default.
- We can use `'use strict'` directive for enabling these feature, it should be added in the top of the script or starting of the function, other wise `'use strict'` may not be enabled.
- Modern JavaScript feature like classes and modules automatically enable the `'use strict'`.
- Variable is a `named storage` for data and we can declare variable in JavaScript using `let`,`var` and `const` keyword. 
```
// declare variable
let message = 'hello';
// assign variable
message = 'World';
```
- Variable name contains only *letters, number, $ and _* and it won't start from digits.
- We use constant values for **hard coded** values, because sometime it difficult to remember hard coded value and prone to mis spell. We declare hard coded constant value by capital letter and underscore. Some constant values are not hardcoded but they don't change after execution like `pageLoadTime`.
- 
```
const COLOR_RED = '#ff0000';
const pageLoadTime = getPageLoadTime();
```
- There is subtle difference between `var` and `let` and variable name should be descriptive and it tells us about what data it store like `let userName = 'Rajat Jindal';`
-------
- There are 8 data types in JavaScript.
- It has special numeric values like `Infinity`, `-Infinity` and `NaN`;
- `NaN` represents the error in mathematical computational and it propagate in whole expression except this `NaN ** 0 == 1`.
- Number type safely represents the number between `2^53^-1` and `-(2^53^-1)`.
- If we need more precision and we are using number more or less above mention then we can use `bigint` type.
- It's created adding `n` end of the number like `let bigInt = 44234343243424n`.
- String 
- Boolean (logical type) - result of comparisons.
- null - not refer to any object or null pointer.
- undefined - value is not defined.
- Object - special data type and it is collection of data.
- Symbol - create unique identifiers. 
- typeof operator 
-------------
- modal - user need to interact with modal window first, after that, they can interact with rest of the page.
- `prompt(title, [default])` if user choose `cancel` or click `esc` button then this function return `null`. 
- `confirm(question)` - `OK` - true otherwise false.
----------
Type Conversion
- String conversion when we expect string value.
- Number conversion, undefined - NaN and NULL - 0, string whitespace removed, it happens during Mathematical operations. 
- Boolean - it happens in logical operations
- false -> "", 0, null, undefined and NaN
- + operator used in string, then it merge the string (if any operand is string then it convert another one in string also).
- Other operator like `-`,`*`,`/` convert the string to number.
- unary `+` operator, just convert the string to number;
- [Precedence Table]([Operator precedence - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#table))
- assignment operator has more precedence than comma.
- Chained assignment evulgated from right to left.
- Increment/decrement operator only applied to the variable. 
- `,` return only the last result.
---------
Comparison
- All comparison results is `Boolean`.
- Both operand are strings then their UNICODE compare.
- Comparing different types, JavaScript convert into the number.
- `null` and `undefined` is equal to each other in equality (`==`) not to others.
---------
- `if` statement evaluate the expression as Boolean.
- Use `?` ternary operator when we want to use the output of the result.
------------
Logical Operator
- `||`, `&&`, '!', `??` result can be any type or use on any type.
- If operand is not Boolean then operand converted into Boolean for evaluation.
- `||` finds the first truthy value.
- `&&` finds the first `falsy` value.
- `&&` has higher precedence then `||`.
- `!` convert the operand into Boolean type.
- `??` -> Nullish coalescing operator and it treats `null` and `undefined` similarly. 
- It's return the defined (value is not `undefined` or `null`) value.
- `??` operator precedence same as `||` operator.
- We can use for assigning value like `x ??= 10`.
----------------
Loops
- `for..in` to loop over object properties.
- `for..of` to loop over iterable objects.
- Single execution of the loop is called *iteration*.
- Condition evaluated or converted into *Boolean*.
```
for(begin; condition; step){
	...
}
```
- `break` directive for breaking the loop on some specific condition. 
- `continue` directive stop the current iteration and force to start new one. 
- *Syntax constructs* that are not expressions, we can use in the `?` ternary operator like we can't use the `break` and `continue` directive with `?` ternary operator.
- label we can use for modify the behavior of `break` or `continue` directive. 
```js
labelName: for (...) {
	...
	if (...) {
		...
		break labelName;
	}
}
```
- Switch statement - 
```js
switch(x){
	case 'value':
		...
		[break];
	case 'anotherValue':
		...
		[break];
	default:
		...
		[break];
}
```
- Switch uses `strict equality` while comparing value with cases.
- We can group case together. 
--------
- Functions - use code many times without repetition. 
- *Function declaration ↓*
```js
function functionName(arguments[, anotherArguments]) {
	...
}
```
- function always get a copy of argument, not the argument itself.
- **Functions** are actions, name usually a *verb*. 
- *Function Expression ↓*
```js
const functionName = function() {
	...
};
```
-  **A function is a value.**
- Callback function - passing function as value means we pass a function in function and expect it that, that function will execute passed function in future.
- Global function declaration defines first in the script.
- Function expression use when we need function depending on the condition.
```js
const sayHi = isUserPremium ? function() { console.log('Hi!! Premium user :)'); } : function() { console.log('Hi!! user :)'); };
```
- Arrow functions -
```js
let arrowFunction = (param1, param2, ...) => expression;
```