# javascript-style-guide


## What is a style guide

A style guide is a set of *standards* to be followed during the writing and designing of code. The implementation of a style guide provides uniformity in code style and formatting. Style guides typically cover guidelines regarding indentation (tabs vs. spaces), variable naming conventions, where best to apply whitespace, and so on.

## Why use a style guide

When you write code you have to think about who will be using it and maintaining it. This most likely will not always be you, and this is especially true if you're working in a team.

Following a style guide helps improve the overall quality of the code you write. This will help facilitate other developers with maintenance and will save time when making changes, adding new features or just when reading it over (code intake).

Readable source code is easier for us to understand as well. It's easier to browse, locate and fix bugs in and more easy to optimize. It can also give us a clearer picture of how the code fits into a larger body of work.

Being consistent will reduce lead time required to understand your code, and if created in a team, will look like one person wrote it. This clarifies how changes and updates to an implementation should be styled or structured.

## About this style guide

This is a guide for writing consistent and aesthetically pleasing JavaScript code. It is inspired by Google's style-guides that they use for open source projects, along with some logical reasoning.

There is a .jscsrc file which enforces these rules as closely as possible. You can either use that and adjust it, or use this script to make your own. You can install JSCS via NPM using `npm install jscs -g`. There are also a large number of plug-ins available for use in your favorite editor or task manager.

* Atom plugin: [https://atom.io/packages/linter-jscs](https://atom.io/packages/linter-jscs)
* Brackets Extension: [https://github.com/globexdesigns/brackets-jscs](https://github.com/globexdesigns/brackets-jscs)
* Grunt task: [https://github.com/jscs-dev/grunt-jscs/](https://github.com/jscs-dev/grunt-jscs/)
* Gulp task: [https://github.com/jscs-dev/gulp-jscs/](https://github.com/jscs-dev/gulp-jscs/)
* Overcommit Git pre-commit hook manager: [https://github.com/brigade/overcommit/](https://github.com/brigade/overcommit/)
* SublimeText 3 Plugin: [https://github.com/SublimeLinter/SublimeLinter-jscs/](https://github.com/SublimeLinter/SublimeLinter-jscs/)
* Syntastic VIM Plugin: [https://github.com/scrooloose/syntastic/blob/master/syntax_checkers/javascript/jscs.vim/](https://github.com/scrooloose/syntastic/blob/master/syntax_checkers/javascript/jscs.vim/)
* Web Essentials for Visual Studio 2013: [https://github.com/madskristensen/WebEssentials2013/](https://github.com/madskristensen/WebEssentials2013/)
* IntelliJ IDEA, RubyMine, WebStorm, PhpStorm, PyCharm plugin: [https://www.jetbrains.com/webstorm/help/jscs.html](https://www.jetbrains.com/webstorm/help/jscs.html)

This guide was created by [Joseph Szczesniak](https://github.com/NukaPunk) and is licensed under the [is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/). You are encouraged to fork this repository and make adjustments according to your preferences.

![CC BY SA 4.0 License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)

## JSCS Linting

If you install one of the above linters, you will be able to have your text editor or IDE automatically check your work to see if it follows this style guide.

Here is a tutorial for installing the Atom plug-in, and some examples of usage.

### Installation

Open Atom and go to preferences by pressing `cmd + ,`. Click on `install` and search for `linter-jscs`.  Install the package. Here is a gif of the process:

![Installing](https://github.com/PrimeAcademy/javascript-style-guide/blob/master/screencap1.gif)

Once you have it installed, you can copy the `.jscsrc` file from this repository into the root of your project and the style guide will be read in automatically.

## Formatting

### 80 Character Line Limit

Limit your lines to 80 characters. This is to maintain human readability, and to train you to keep your logic short and concise. Your editor should have a line to show this in the editor. We do not enforce this in comments or regex statements.

### 2 Space Indentations

To improve human readability you should use spaces to indent your code. Different editors display tabs differently, and using tabs requires you to know what the indentation of a tab is going to look like, and require it to always be consistent. Therefore we will not use tabs. 2 spaces is preferred because it is quicker and leaves code more compressed horizontally. It is also very similar to the old days of using 2 spaces after a period, so that's neat.

Save time and configure your editor to insert 2 spaces when you press the tab button to save you from having to press the space bar twice. Also configure auto indenting to use 2 spaces, and then you can adjust code quickly.

### Semicolons

Even though semicolons are technically optional in JavaScript, it is important that you use them. Interpreters can make mistakes without them.

Valid
```javascript
var a = 1;
var fn = function () {
    //...
};
```
Invalid
```javascript
var a = 1
var fn = function () {
    //...
}
```

Example:
```javascript
// define a function
var fn = function () {
    //...
} // semicolon missing at this line

// then execute some code inside a closure
(function () {
    //...
})();
```

This will be interpreted as:
```javascript
var fn = function () {
    //...
}(function () {
    //...
})();
```

Block statements (the keywords `do`, `for`, `if`, `else`, `switch`, `case`, `try`, `catch`, `void`, `while`, `with`, and `function`) do not require semicolons.

Valid

```javascript
if (x) {
  x++;
}
```

Invalid

```javascript
if (x) {
  x++;
};
```


### Curly Braces

Not using curly braces can lead to errors. Block statements (the keywords `do`, `for`, `if`, `else`, `switch`, `case`, `try`, `catch`, `void`, `while`, `with`, and `function`) should have braces. Curly braces must also start on the same line as the statement to avoid undefined errors. If you must split parameters onto new lines, use four spaces and keep curly braces on the same line as the final parameter.

Valid

```javascript
if (x) {
  x++;
}
```

Invalid

```javascript
if (x) x++;
```

Invalid

```javascript
if (x)
{
  x++;
}
```

### Else On Same Line

When writing `if` statements, `else` must be on the same line as the ending curly brace of the `if`.

Valid
```javascript
if (x < 0) {
  x++;
} else {
  x--;
}
```

Invalid
```javascript
if (x < 0) {
  x++;
}
else {
  x--;
}
```

### Single Quotes

Always use single quotes except when using JSON. JSON strings must be double quoted.

Valid
```javascript
var x = 'x';
```
Invalid
```javascript
var x = "x";
```
Valid
```javascript
var jsonString = '{"key1":"value1"}';
```

### Strings

Use single quotes to create strings. If you need to break a string into multiple lines, use `+` to concatenate.

Valid
```javascript
var x = 'multi' +
    'line';
var y = 'single line';
```
Invalid
```javascript
var x = "multi \
    line";
```

### Remove Trailing Whitespace

Remove all trailing whitespace. Programmers who have gotten fast will use the `end` key or `cmd + arrow` keys to navigate to the end of the current line. If you have whitespace at the end of your code, this is frustrating.  

### Variable Declarations

Always use `var` when declaring variables. When a comma is forgotten, JavaScript will add a semicolon, thus elevating a var-less property to the global scope. This may have unintended consequences, so just don't do it.

Valid
```javascript
var a = require('a');
var b = require('b');
var x = 1;
var y = 2;
for (var i = 0, var j = arr.length; i < j; i++) {}
```

Invalid

```javascript
var a = require('a'),
  b = require('b');
var x = 1,
  y = 2;
var x, y = 2, z;
for (i = 0, j = arr.length; i < j; i++) {}
```

### Spaces

Always put a single space after block statements (the keywords `do`, `for`, `if`, `else`, `switch`, `case`, `try`, `catch`, `void`, `while`, `with`, and `function`). Binary operators (`=`, `,`, `+`, `-`, `/`, `*`, `==`, `===`, `!=`, `!==`, etc.) should also be surrounded with spaces.  In addition, put space before and after the `?` or `:` in conditional expressions.

The opening/closing braces and curly braces after keywords, block statements, and literal objects should also have spacing.

Valid
```javascript
if (x) {
    x++;
}
x !== y;
var a = b ? c : d;
```

Invalid
```javascript
if(x) {
    x++;
}
x!== y;
x !==y;
x!==y;

var a = b? c : d;
var a = b ?c : d;
var a = b ? c: d;
var a = b ? c :d;

```

### No Spaces

Object and Array brackets, parenthesis, and line breaks should not contain spaces.  Braces that belong to a function should not have a spaces. Likewise, when you call and expression, do not use spaces.

Valid
```javascript
var x = {a: {b: 1}};
var x = [[1]];
var x = (1 + 2) * 3;
var x = a[1];
function(){}
foo();
```

Invalid
```javascript
var x = { a: { b: 1 } };
var x = [ [ 1 ] ];
var x = ( 1 + 2 );
var x = a[ 1 ];
function () {}
foo ();
```

In addition, there should be no space after object keys, but before their values.

Valid
```javascript
var y = {
    a: 1,
    b: 2
}
var x = {a: 1};
```

Invalid
```javascript
var y = {
    a:1,
    b :2
}
var x = {a : 1};
```


### Line breaks

There is no need for multiple line breaks. Also, don't put line breaks after block statements (the keywords `do`, `for`, `if`, `else`, `switch`, `case`, `try`, `catch`, `void`, `while`, `with`, and `function`).

Valid
```javascript
x++;

if (cond){
    foo();
}
```

Invalid
```javascript
x++;


if (cond)
{
    foo();
}
```

## Naming Conventions

### Constants

Constants should always be in uppercase, and use underscores to separate out words. If you're using ECMA6 you should also use the `const` keyword. Do not use object properties as constants, only use primitives. JavaScript will not protect your properties from being overwritten.

Valid
```javascript
const MAX_NUMBER_OF_ATTEMPTS = 5;
```

Invalid
```javascript
const maxNumberOfAttempts = 5;
```
Invalid
```javascript
const MY_OBJECT = { key: "value"};
```

### Variables

All public variables should be camelCase. The leading character is lowercase, and all other words should be capitalized. If a variable is private, start it with an underscore. Trailing underscores are acceptable.


Valid
```javascript
var camelCase = 0;
var CamelCase = 1;
var _camelCase = 2;
var camelCase_ = 3;
```

Invalid
```javascript
var lower_case = 1;
var Mixed_case = 2;
var mixed_Case = 3;
```

### Constructors

Constructors should always be capitalized.

Valid
```javascript
var a = new Car();
```

Invalid
```javascript
var a = new car();
```

## Conditionals and Operators

### Operators Before Line Breaks

Valid

```javascript
x = y ? 1 : 2;
x = y ?
  1 : 2;
```

Invalid

```javascript
x = y
  ? 1 : 2;
```
### Unary Operators

Unary operators should be "stuck to the right". There should not be a space between the unary operators and the variables on which they're being used.

Valid
```javascript
x = !y; y = ++z;
```

Invalid
```javascript
x = ! y; y = ++ z;
```

## Functions

### Parameters

Parameters should be separated with a comma and a space for readability.

If you have to write parameters on separate lines, use two spaces to indent them. Then, the following code should be indented another two spaces to preserve readability.

Valid

```javascript
function (paramOne, paramTwo,
  paramThree) {
    x++;
}
```

Invalid

```javascript
function (paramOne,paramTwo,
paramThree) {
  x++;
}
```

## Objects

### Always use dot notation, when possible.

Valid
```javascript
var a = b.c;
var a = b[c];
var a = b[c.d];
var a = b[1];
var a = b.while; // reserved words can be property names in ES5
```

Invalid
```javascript
var a = b['c'];
```


## Miscellaneous

### Do Not Use with.

Use of the `with` statement is not recommended, as it may be the source of confusing bugs and compatibility issues.

Invalid

```javascript
with (x) {
  prop++;
}
```

## JSDocs

JSDoc is an API documentation generator for JavaScript, similar to JavaDoc or PHPDoc. The purpose is to document the API of your JavaScript application or library. You add documentation comments directly to your source code, right along side the code itself. The JSDoc Tool will scan your source code, and generate a complete HTML documentation website for you.

Our style guide adheres to the Closure Compiler's annotation style. The Closure Compiler looks for type information in JSDoc tags. Because JavaScript has no way to declare types, the Closure Compiler can use data type information about JavaScript variables to provide enhanced optimization and warnings. Because JavaScript has no syntax for declaring the type of a variable, you must use comments in the code to specify the data type.

>The following is taken from [Getting Started with JSDoc 3](http://usejsdoc.org/about-getting-started.html) and adheres to the Creative Commons Attribution-ShareAlike 3.0 License.

### Commenting your code

JSDoc comments should be placed immediately before the code being documented. It must start with a `/**` sequence in order to be recognized by the JSDoc parser. Comments beginning with `/*`, `/***`, or more than 3 stars will be ignored. This is a feature to allow you to suppress parsing of comment blocks. In addition, inline comments `//` are ignored.

### Description

The simplest documentation is just a description.

```JavaScript
/** This is a description of the foo function. */
function foo() {
}
```

### Documentation Tags

Special Documentation Tags can be added to your descriptions to give more information.

For instance, use the `@constructor` tag to decorate a function as a constructor.

```JavaScript
/**
 * Represents a book.
 * @constructor
 */
function Book(title, author) {
}
```

You should also describe input parameters using the `@param` tag.

```JavaScript
/**
 * Represents a book.
 * @constructor
 * @param {string} title - The title of the book.
 * @param {string} author - The author of the book.
 */
function Book(title, author) {
}
```

See a full list of tags at the [JSDocs website](http://usejsdoc.org/).

###  Closure Compiler Tags

Please read [Annotating JavaScript for the Closure Compiler](https://developers.google.com/closure/compiler/docs/js-for-compiler?hl=en) for more information on JSDocs tags that affect on the behavior of the Closure Compiler, Type Expressions, and Generic Types.
