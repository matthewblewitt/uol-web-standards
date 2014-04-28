#Javascript Style Guide

JavaScript is the main client-side scripting language used by many of our projects. This style guide is a list of dos and don'ts for JavaScript programs.

##JavaScript Language Rules

###var

Declarations with var: Always

####Decision:

When you fail to specify var, the variable gets placed in the global context, potentially clobbering existing values. Also, if there's no declaration, it's hard to tell in what scope a variable lives (e.g., it could be in the Document or Window just as easily as in the local scope). So always declare with var.

###Constants

*Use `NAMES_LIKE_THIS` for constant values.
*Use `@const` to indicate a constant (non-overwritable) pointer (a variable or property).
*Never use the `const` keyword as it's not supported in Internet Explorer.

####Decision:

#####Constant values

If a value is intended to be constant and immutable, it should be given a name in `CONSTANT_VALUE_CASE`. `ALL_CAPS` additionally implies `@const` (that the value is not overwritable).

#####Primitive types (number, string, boolean) are constant values.

Objects' immutability is more subjective — objects should be considered immutable only if they do not demonstrate observable state change. This is not enforced by the compiler.

#####Constant pointers (variables and properties)

The `@const` annotation on a variable or property implies that it is not overwritable. This is enforced by the compiler at build time. This behavior is consistent with the const keyword (which we do not use due to the lack of support in Internet Explorer).

A `@const` annotation on a method additionally implies that the method cannot not be overridden in subclasses.

A @const annotation on a constructor implies the class cannot be subclassed (akin to final in Java).

#####Examples

Note that `@const` does not necessarily imply `CONSTANT_VALUES_CASE`. However, `CONSTANT_VALUES_CASE` does imply @const.

```js
/**
 * Request timeout in milliseconds.
 * @type {number}
 */

goog.example.TIMEOUT_IN_MILLISECONDS = 60;
```

The number of seconds in a minute never changes. It is a constant value. `ALL_CAPS` also implies @const, so the constant cannot be overwritten.

The open source compiler will allow the symbol to be overwritten because the constant is not marked as @const.

```js
/**
 * Map of URL to response string.
 * @const
 */
MyClass.fetchedUrlCache_ = new goog.structs.Map();
/**
 * Class that cannot be subclassed.
 * @const
 * @constructor
 */

sloth.MyFinalClass = function() {};
```

In this case, the pointer can never be overwritten, but value is highly mutable and not constant (and thus in `camelCase`, not `ALL_CAPS`).

###Semicolons

Always use semicolons.
Relying on implicit insertion can cause subtle, hard to debug problems. Don't do it. You're better than that.

There are a couple places where missing semicolons are particularly dangerous:

```js
// 1.
MyClass.prototype.myMethod = function() {
  return 42;
}  // No semicolon here.

(function() {
  // Some initialization code wrapped in a function to create a scope for locals.
})();


var x = {
  'i': 1,
  'j': 2
}  // No semicolon here.

// 2.  Trying to do one thing on Internet Explorer and another on Firefox.
// I know you'd never write code like this, but throw me a bone.
[ffVersion, ieVersion][isIE]();


var THINGS_TO_EAT = [apples, oysters, sprayOnCheese]  // No semicolon here.

// 3. conditional execution a la bash
-1 == resultOfOperation() || die();
```

####So what happens?

JavaScript error - first the function returning 42 is called with the second function as a parameter, then the number 42 is "called" resulting in an error.
You will most likely get a 'no such property in undefined' error at runtime as it tries to call x[ffVersion, ieVersion][isIE]().
die is always called since the array minus 1 is NaN which is never equal to anything (not even if resultOfOperation() returns NaN) and THINGS_TO_EAT gets assigned the result of die().
Why?

JavaScript requires statements to end with a semicolon, except when it thinks it can safely infer their existence. In each of these examples, a function declaration or object or array literal is used inside a statement. The closing brackets are not enough to signal the end of the statement. Javascript never ends a statement if the next token is an infix or bracket operator.

This has really surprised people, so make sure your assignments end with semicolons.

Clarification: Semicolons and functions

Semicolons should be included at the end of function expressions, but not at the end of function declarations. The distinction is best illustrated with an example:

```js
var foo = function() {
  return true;
};  // semicolon here.

function foo() {
  return true;
}  // no semicolon here.
```

##JavaScript Style Rules










