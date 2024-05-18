- Debugging is very important for a coder, it helps us to find bugs and for fixing.
- *Sources* panel in the dev tools has 3 parts -
	- File Navigator
	- Code Editor
	- JavaScript Debugging
- We can pause the execution of our script by using `debugger` command and this command only works when development tool open.
- Debugger panel shows different dropdown stack tabs.
	- Call Stack - show all the functions.
	- Scope - Current variables.
		- Global
		- Local
- Resume button `F8` - go to the next breakpoint.
- Step `F9` - Run the next command.
- Step Over `F10` - Go to next statement but don't go into the function.
- Step into `F11` - Same as `Step` but behave differently for async functions. 
- Step Out `Shift + F11` - Continue the execution till the end of the current function. 
--------------
Coding Style
- ![[Pasted image 20240518174744.png]]
	- Curly braces on the same line after space.
	- Vertical indentation for group logical block together. 
- Linters tools that check code style and help to improve them. 
------------
Comments 
- “if the code is so unclear that it requires a comment, then maybe it should be rewritten instead”.
- Factor out the function like if we have a function which do two things, then we can create a new function which do one thing and other function do another thing.
- Special comment syntax - `JSDocs`.
```js
/**
*
* @param {number} x The number to raise.
*/
```
- [JSDocs 3](https://jsdoc.app/)
- If the code has anything subtle and counter-intuitive, it’s definitely worth commenting.
-----------
Ninja Code 
- Short is always better.
- Use abbreviations. 
-------------
Testing 
Will learn later

--------------
Polyfills and transpilers
- transpilers translate one source code to another means translate latest syntax construct to older which old browser support (Babel).
- New feature include more than syntax constructs and operators like built in function.
- Script which updates/adds function is called polyfills (core-js polyfills.io)
