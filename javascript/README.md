# JavaScript Style Guide

## Formatting

* Use UTF-8.

* Use 2 space indent, no tabs.

* Use Unix-style line endings.

* Use spaces around operators, after commas, question marks, colons, semicolons,
  `if`, `else`, `switch`, `for`, `while`, `try`, `catch` and `function`
  statements, around `{` and before `}`.

* Indentate the `case` statements from the switch, and indentate the contents
  of the `case` statement from the `case` statement itself.

* Don't use spaces after `(`, `[` and before `]`, `)`.

* Use `{` and `}` for all statement modifiers, except for one-liners.

* Leave a new line before the `else`, `catch` and `finally` statements.
  ```javascript
  /* Bad */
  if (a === b) {
    console.log(a);
  } else {
    console.log(1);
  }

  /* Good */
  if (a === b) {
    console.log(a);
  }
  else {
    console.log(1);
  }
  ```

* Use an empty line before the return value of a method (unless it only has one
  line).

* Use an empty line after the variables definition.

* Use empty lines to break up a long function into logical paragraphs.

* Keep lines fewer than 80 characters.

* When function call takes more than 80 characters, you can break it up by
  placing one argument per line, and the closing parentheses and function call
  in a separate line.
  ```javascript
  /* Bad */
  doSomething(veryLongArgument1, veryLongArgument2, veryLongArgument3, veryLongArgument4);

  /* Good */
  doSomething(
    veryLongArgument1,
    veryLongArgument2,
    veryLongArgument3,
    veryLongArgument4
  );
  ```

* Avoid trailing whitespace.

* Don't align variables/constants assignments or object literals keys/values
  vertically.

* Use comma-first approach for defining variables only, using `var` only once at
  the beggining of the function, leaving one line per variable. If the initial
  value can't be assigned, use `null`.
  ```javascript
  var myVar = 3
    , myOtherVar = 4
    , owner = null;

  owner = {
    name: "Owner",
    dogs: [
      "Dog 1",
      "Dog 2"
    ]
  };
  ```

## Syntax

* Use `===` or `!==` to compare for equality/inequality.

* Use function declarations, instead of function expressions.
  ```javascript
  /* Bad */
  function myFunc() {
  }

  /* Good */
  var myFunc;

  myFunc = function () {
  };
  ```

* Avoid `++` and `--` operators, use `+= 1` and `-= 1` instead.

* In `for` loop statements, store the iterator and the array length in a
  variable.

* Use doublequotes for strings.

* Prefer using helper functions to iterate through collections or objects,
  instead of using `for` or `while`.

* Prefer using helper functions to build constructor functions and to emulate
  inheritance and mixins, instead of using the prototype directly.

* Never use `undefined` explicitly.

* Use the literal notation for `Array` and `Object` creation (`[]` and `{}`).

* Use dot notation when accessing properties.

* Avoid using `with`, `in` statements.

* Avoid using `eval`.

* Use an instance of `Error` when throwing errors.
  ```javascript
  /* Bad */
  throw "invalid!";

  /* Good */
  throw new Error("invalid!");
  ```

## Naming

* Use `camelCase` without the first letter capitalized for variables, object
  properties and methods, unless the object is to be used to interact with an
  API that uses a different naming.

* Don't capitalize acronyms in variables/property/method names.

* Use `CamelCase` with the first letter capitalized for constructor functions.

* Use `SCREAMING_SNAKE_CASE` for constants and enumeration keys.

* Use `_` for unused variables or to start private object properties/methods
  names.

* Use `self` to name a variable to store `this` in the scope, avoid using
  `bind`.

## Comments

* Comments longer than a word are capitalized and use punctuation.

* Use `/* */` style comments only.

* Use the JavaDoc syntax for multiline comments.

* Avoid superfluous comments.

## General

* Avoid writing methods that span more than 10 lines.

* Avoid writing methods that receive more than 3 parameters.

* Avoid storing objects in the global object.

* Prefer a modular approach for organizing your application.

* Assign values to variables to avoid passing long parameters or having long
  lines.

* Code in a functional way, avoid mutation when it makes sense.

* Do not mutate arguments unless that is the purpose of the method.

* Do not mess around in core classes when writing libraries.

* Do not program [defensively](http://www.erlang.se/doc/programming_rules.shtml#HDR11).

* Keep the code simple.

* Don't overdesign.

* Don't underdesign.

* Avoid bugs.

* Be consistent.

* Use common sense.

## References

* Ruby's [Chris Neukirchen's Ruby Style Guide](http://github.com/chneukirchen/styleguide)

* [geddy/js-styleguide](https://github.com/geddy/js-styleguide)
