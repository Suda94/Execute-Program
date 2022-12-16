# Execute-Program.
<h2> 1. learning:</h2>
<p>This course covers JavaScript as it exists today. It assumes basic familiarity with JavaScript:

You should know how to define a function and write an if.
You should have seen the this keyword before, but you don't need to know about its confusing quirks (there are many of them).
You should know common array operations, like map and filter. If you need to learn about these, we teach them in our Javascript Arrays course!
Variable scoping has often been a sore point in JavaScript. The simplest assignment syntax, x = 1, defines a global variable. That's rarely what we want!

Fortunately, modern versions of JavaScript have "strict mode". It prevents many kinds of mistakes, including global variable definitions like x = 1. Strict mode is enabled by putting the string 'use strict' at the top of a module or function.</p>
//
<h2> 2. let</h2>
<p>Add a value of x that makes this code produce the result shown at the bottom. We'll always run all of the code together from top to bottom: both the code that you can't change and the code that you wrote.

<br>function double(aNumber) {
 <br> return 2 * aNumber;}
<br>3
<br>const x = 3
<br>double(x);
<br>GOAL:
<br>6
<br>YOURS:
<br>6
<br>
<p>Before 2015, local variables in JavaScript were declared with the var keyword. When we define a var inside a function, it's only visible inside the function. We're allowed to use var in strict mode.

<br>function defineX() {
<br>  var x = 1;
<br>  return x + 1;}
<br>defineX();
<br>RESULT:
<br>2
<br>
However, trying to reference the variable outside of the function is an error.

Here's a code problem:

Reference x outside of the function, which will cause an error. For example, you can use a console.log or assign x a new value.

<br>function defineX() {
<br>  var x = 1;
}
<br>defineX();
<br>0;
<br>x=0;
<br>GOAL:
<br>ReferenceError: x is not defined
<br>YOURS:
<br>ReferenceError: x is not defined
<br>
Show Author's Answer
Functions create a variable scope. Variables defined inside the function are visible within the function, and invisible outside the function. This is good!

We expect an if block to behave the same way. If we put a var inside an if (...) { ... }, we expect the variable to be visible inside the if block, which it is:
<p>
<p>All vars are "function-scoped", which means that they're visible to the entire function body, no matter how they're defined within the function. This was a mistake in JavaScript's design: var x = 1 inside an if shouldn't be visible outside the if. It's too easy to declare a variable, thinking that it will be local to the if, then accidentally use it later in the function.

Fortunately, this problem was fixed in 2015, when let was introduced. With let, a variable defined inside the if isn't visible outside the if. Trying to access it will cause an error. (You can type error when a code example will throw an error.)</p>

<p>All vars are "function-scoped", which means that they're visible to the entire function body, no matter how they're defined within the function. This was a mistake in JavaScript's design: var x = 1 inside an if shouldn't be visible outside the if. It's too easy to declare a variable, thinking that it will be local to the if, then accidentally use it later in the function.

Fortunately, this problem was fixed in 2015, when let was introduced. With let, a variable defined inside the if isn't visible outside the if. Trying to access it will cause an error. (You can type error when a code example will throw an error.)

<br>
<br>function f() {
 <br> if (true) {
 <br>   let x = 1;
  }
 <br> return x;
}
<br>f();
<br>RESULT:
<br>ReferenceError: x is not defined
let handles nested scopes properly. For example, we can define an x in the function body, then define another x inside an if. Changing the "inner" x won't change the "outer" x.
<br>

<br>
<br>function f() {
 <br> let x = 'outer';
 <br> if (true) {
 <br>   let x = 'inner';}
 <br>return x;}
<br>f();
<br>RESULT:
<br>'outer'
<br>
Those variables hold different values even though they have the same name. That's called "shadowing": the inner let x shadows the outer let x. Opinions vary on whether shadowing should be used sparingly, or avoided altogether. Our opinion is: use it sparingly, and only when all of the alternatives feel awkward.

We've been using if for our examples, but let scoping rules apply to any block of code in curly braces, like { ... }. For example, an outer scope can't access a variable defined inside a while; that causes an error.</p>
