---
layout: post
title: "Variable Assignment - Part 1"
---

<br>
In this two part series we dig deep how variable assignment is handled in javascript, the different data types, how they are assigned values, how the are compared and passed. The concepts are straight forward and easy to conceptualise but its far easier to confuse if you are not careful. 

Variable assingment can be divided in to two groups , the primitive types and the reference types. We discuss in this first post the first data type, primitive types. 
<br />
<br />

### Primitive Type<br>

* Number type:			&ensp;&ensp; 3.1416, 9, 12
* Boolean type:			&ensp;&ensp;true, false
* String type:				&ensp;&ensp;&ensp;&ensp;"Hello, World"
* Null type:					&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;Null			
* Undefined type:		Undefined

(As of ES2015 there is an additional primitive value called [Symbol](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Symbol). )
<br />
<br />

### Primitive Types are _compared_ by value
<br />
During variable assignment a primitive's value is stored directly to the variable we are assigning it to.

This is exactly as you would expect. If we assign two different variables the exact same primitive value both variable would have a value that is exactly the same as each other.

When we compare these two variables what we are comparing is the value that they contain.

```javascript
var foo = "Hello World";
var bar = "Hello World";
foo === bar // true
```
foo's value which is "Hello world" is being compared to bar's value which also exactly the same "Hello world". 

```javascript
foo === bar // is the same as below
"Hello World" === "Hello World"
```
Pretty straight forward so far, right?
<br />
<br />

### Primitive Types are _immutable_
<br />
There is no way we can change or mutate a primitive's value.

```javascript
var foo = 1; // foo is 1
foo = 2; // foo is now 2
```

It is tempting to think that we are assigning foo's value on the first line which is number 1 to number 2 on the second line. But all we are doing on the second line is assigning a new number to the variable foo without the involvement of 1 at all.

```javascript
var foo = 1; // foo is assigned to number 1
foo = 2; // foo is assigned to number 2
```

You can think of it as if foo is given the value of number 1 on the first line then on the second line it is given a new value of 2. Value 1 is completed unaffected by the assignment of foo to value 2.
<br />
<br />

### Primitive Types are _passed_ by value
<br />
Primitive types are also passed by their value. Take the example below:

```javascript
var foo = 1;
function bar(foo) {
	foo = 2;
}
console.log(foo) // ??
```
If we pass foo to function bar what we are really passing is the value of foo which is 1 and of course the value 1 would not be mutated to value 2.

```javascript
var foo = 1
function bar(1) {
	1 = 2; // cant change the values
}
console.log(foo) // foo is still 1
```

The assignment inside function bar would have not any effect to variable foo at all. Hence foo would still equal to 1.

Combining it all, what do you think would foo's value be?

```javascript
var foo = 1;
var bar = foo;
bar = 2;
foo // ??
```

```javascript
var foo = 1;
var bar = foo; // bar gets assigned value of foo which is 1
var bar = 1; // the second line code is the same as this
bar = 2; // bar gets assigned a new value which is 2
foo // is still 1
```

You can think of it this way:<br>

Line 1: foo is given a value 1<br>
Line 2: bar is given the value of foo which is 1
(At this point both bar and foo has the value of 1.)<br>
Line 3: we assign bar to value 2.<br>
Now bar has a value of 2, foo still has the value of 1. Foo is completed unaffected by our new assignment to bar in Line 3, hence foo is still 1.
<br>

Thats it for now! We would compare and contrast primitive types with reference type on the next post.