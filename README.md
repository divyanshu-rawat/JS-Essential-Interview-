# JS-Essential-Interview ★
Essential JS Interview Questions, that will come handy durning JS Interviews. 👋

> Here JS BIN Comprises of code snippets, of the following Questions, along with explanation as comments. 📖

**Question 1**

What is a potential pitfall with using typeof bar === "object" to determine if bar is an object? How can this pitfall be avoided?

[JS BIN](https://jsbin.com/qeyenuh/edit?js,console).

##

**Question 2**

What will the code below output to the console and why?

```js (function(){
var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```
[JS BIN](https://jsbin.com/qacaruh/edit?js,console).

##

**Question 3** 

What will the code below output to the console and why?

```js

var myObject = {
    foo: "bar",
    func: function() {
        var self = this;
        console.log("outer func:  this.foo = " + this.foo);
        console.log("outer func:  self.foo = " + self.foo);
        (function() {
            console.log("inner func:  this.foo = " + this.foo);
            console.log("inner func:  self.foo = " + self.foo);
        }());
    }
};
myObject.func();

```

[JS BIN](https://jsbin.com/xaxefud/1/edit?js,console)

##

**Question 4**

What is the significance of, and reason for, wrapping the entire content of a JavaScript source file in a function block?

```js
  /*
  
    This is an increasingly common practice, employed by many popular JavaScript libraries (jQuery, Node.js, etc.). This  
    technique creates a closure around the entire contents of the file which, perhaps most importantly, creates a private 
    namespace and thereby helps avoid potential name clashes between different JavaScript modules and libraries.


    Another feature of this technique is to allow for an easily referenceable (presumably shorter) alias for a global 
    variable. This is often used, for example, in jQuery plugins. jQuery allows you to disable the $ reference to the jQuery 
    namespace, using jQuery.noConflict(). If this has been done, your code can still use $ employing this closure technique, 
    as follows:

    (function($) { jQuery plugin code referencing $ } )(jQuery);
  
  */

```

##

**Question 5**

What is the significance, and what are the benefits, of including 'use strict' at the beginning of a JavaScript source file?

```js
    /*
    
    Makes debugging easier - Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions,
    
    Prevents accidental globals - Without strict mode, assigning a value to an undeclared variable automatically creates a global variable with that name. This is one of the most common errors in JavaScript. In strict mode, attempting to do so throws an error.
    
    Eliminates this coercion - Without strict mode, a reference to a this value of null or undefined is automatically coerced to the global. This can cause many headfakes and pull-out-your-hair kind of bugs. In strict mode, referencing a a this value of null or undefined throws an error.
    
    Disallows duplicate parameter values - Strict mode throws an error when it detects a duplicate named argument for a function (e.g., function foo(val1, val2, val1){}), thereby catching what is almost certainly a bug in your code that you might otherwise have wasted lots of time tracking down.
    
    Throws error on invalid usage of delete - The delete operator (used to remove properties from objects) cannot be used on non-configurable properties of the object. Non-strict code will fail silently when an attempt is made to delete a non-configurable property, whereas strict mode will throw an error in such a case.
    
    
    */

```

##

**Question 6**

Consider the two functions below. Will they both return the same thing? Why or why not?

```js
    
function foo1()
{
  return {
      bar: "hello"
  };
}

function foo2()
{
  return
  {
      bar: "hello"
  };
}

```

[JS BIN](https://jsbin.com/tajimor/1/edit?js,console)

##

**Question 7**

What is NaN? What is its type? How can you reliably test if a value is equal to NaN?

```js
    
/* 

The NaN property represents a value that is “not a number”. This special value results from an operation that could not be performed either because one of the operands was non-numeric (e.g., "abc" / 4), or because the result of the operation is non-numeric.

While this seems straightforward enough, there are a couple of somewhat surprising characteristics of NaN that can result in hair-pulling bugs if one is not aware of them.

For one thing, although NaN means “not a number”, its type is, believe it or not, Number:

*/

console.log(typeof NaN === "number");  // logs "true"

/*

Additionally, NaN compared to anything – even itself! – is false:

*/

console.log(NaN === NaN);  // logs "false"

/*

A semi-reliable way to test whether a number is equal to NaN is with the built-in function isNaN(), but even using isNaN() is an imperfect solution.

A better solution would either be to use value !== value, which would only produce true if the value is equal to NaN. Also, ES6 offers a new Number.isNaN() function, which is a different and more reliable than the old global isNaN() function.

*/


```

##

**Question 8**

What will the code below output? Explain your answer.

```js
    
    console.log(0.1 + 0.2);
    console.log(0.1 + 0.2 == 0.3);
    
```

[JS BIN](https://jsbin.com/tepiguj/1/edit?js,console)

##

**Question 9**

In what order will the numbers 1-4 be logged to the console when the code below is executed? Why?

```js
    
    (function() {
        console.log(1); 
        setTimeout(function(){console.log(2)}, 1000); 
        setTimeout(function(){console.log(3)}, 0); 
        console.log(4);
    })();

```

[JS BIN](https://jsbin.com/boyuruw/1/edit?js,console)

##

**Question 10** 

Write a simple function (less than 160 characters) that returns a boolean indicating whether or not a string is a palindrome.

[JS BIN](https://jsbin.com/edit?js,console)

##

**Question 11**

Write a sum method which will work properly when invoked using either syntax below.

```js
    
    console.log(sum(2,3));   // Outputs 5
    console.log(sum(2)(3));  // Outputs 5

```

[JS BIN](https://jsbin.com/piwuvog/3/edit?js,console)

##

**Question 12**

Consider the following code snippet:

```js
    
for (var i = 0; i < 5; i++) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', function(){ console.log(i); });
  document.body.appendChild(btn);
}

```

(a) What gets logged to the console when the user clicks on “Button 4” and why?

(b) Provide one or more alternate implementations that will work as expected.


[JS BIN](https://jsbin.com/gupecin/1/edit?js,console)

##

**Question 13**

Assuming d is an “empty” object in scope, say:

```js 
    var d = {};
  
```

…what is accomplished using the following code?

```js
    [ 'zebra', 'horse' ].forEach(function(k) {
	d[k] = undefined;
});

```

```js
    /*
        The snippet of code shown above sets two properties on the object d. Ideally, any lookup performed on a JavaScript             object with an unset key evaluates to undefined. But running this code marks those properties as “own properties” of           the object.

        This is a useful strategy for ensuring that an object has a given set of properties. Passing this object to                   Object.keys will return an array with those set keys as well (even if their values are undefined).
    
    */

```

##

**Question 14**

What will the code below output to the console and why?

```js
	var arr1 = "john".split('');
	var arr2 = arr1.reverse();
	var arr3 = "jones".split('');
	arr2.push(arr3);
	console.log("array 1: length=" + arr1.length + " last=" + arr1.slice(-1));
	console.log("array 2: length=" + arr2.length + " last=" + arr2.slice(-1));

```
[JS BIN](https://jsbin.com/fejulit/edit?js,console)

##

**Question 15**

What will the code below output to the console and why ?

```js
	
	console.log(1 +  "2" + "2");
	console.log(1 +  +"2" + "2");
	console.log(1 +  -"1" + "2");
	console.log(+"1" +  "1" + "2");
	console.log( "A" - "B" + "2");
	console.log( "A" - "B" + 2);

```

[JS BIN](https://jsbin.com/cucaqay/1/edit?js,console)

##

**Question 16**

What is a “closure” in JavaScript? Provide an example.

```js
/*
	A closure is an inner function that has access to the variables in the outer (enclosing) function’s scope chain. The 	     closure has access to variables in three scopes; specifically: (1) variable in its own scope, (2) variables in the      	     enclosing function’s scope, and (3) global variables.
	
*/

```

[JS BIN](https://jsbin.com/jadoxud/1/edit?js,console)

##

**Question 17** 

What will be the output of the following code:

```js 

	for (var i = 0; i < 5; i++) {
	    setTimeout(function() { console.log(i); }, i * 1000 );
	}

```

Explain your answer. How could the use of closures help here?

[JS BIN](https://jsbin.com/kovezox/1/edit?js,console)


##

**Question 18**

What would the following lines of code output to the console?

```js
	
	console.log("0 || 1 = "+(0 || 1));
	console.log("1 || 2 = "+(1 || 2));
	console.log("0 && 1 = "+(0 && 1));
	console.log("1 && 2 = "+(1 && 2));

```

[JS BIN](https://jsbin.com/xanifer/1/edit?js,console)

##

**Question 19**

What will be the output when the following code is executed? Explain.

```js

console.log(false == '0')
console.log(false === '0')

```

```js

/*

The code will output:

console.log(false == '0') // true
console.log(false === '0') // false

In JavaScript, there are two sets of equality operators. The triple-equal operator === behaves like any traditional equality operator would: evaluates to true if the two expressions on either of its sides have the same type and the same value. The double-equal operator, however, tries to coerce the values before comparing them. It is therefore generally good practice to use the === rather than ==. The same holds true for !== vs !=.

*/

```

##

**Question 20**

What is the output out of the following code? Explain your answer.


```js

var a={},
    b={key:'b'},
    c={key:'c'};

a[b]=123;
a[c]=456;

console.log(a[b]);

```

[JS BIN](https://jsbin.com/nanepic/2/edit?js,console)

##

**Question 21** 

What will the following code output to the console:

```js

console.log((function f(n){return ((n > 1) ? n * f(n-1) : n)})(10));

```

Explain your answer.

```js

/*

The code will output the value of 10 factorial (i.e., 10!, or 3,628,800).

Here’s why:

The named function f() calls itself recursively, until it gets down to calling f(1) which simply returns 1. Here, therefore, is what this does:

f(1): returns n, which is 1
f(2): returns 2 * f(1), which is 2
f(3): returns 3 * f(2), which is 6
f(4): returns 4 * f(3), which is 24
f(5): returns 5 * f(4), which is 120
f(6): returns 6 * f(5), which is 720
f(7): returns 7 * f(6), which is 5040
f(8): returns 8 * f(7), which is 40320
f(9): returns 9 * f(8), which is 362880
f(10): returns 10 * f(9), which is 3628800


*/
```

##

**Question 22** 

Consider the code snippet below. What will the console output be and why?

```js

(function(x) {
    return (function(y) {
        console.log(x);
    })(2)
})(1);

```

[JS BIN](https://jsbin.com/bilaguk/1/edit?js,console)

##

**Question 23**

What will the following code output to the console and why:

```js

var hero = {
    _name: 'John Doe',
    getSecretIdentity: function (){
        return this._name;
    }
};

var stoleSecretIdentity = hero.getSecretIdentity;

console.log(stoleSecretIdentity());
console.log(hero.getSecretIdentity());

```

What is the issue with this code and how can it be fixed?

[JS BIN](https://jsbin.com/maxepew/edit?js,console).

##

**Question 24**

Create a function that, given a DOM Element on the page, will visit the element itself and all of its descendents (not just its immediate children). For each element visited, the function should pass that element to a provided callback function.

The arguments to the function should be:

* a DOM element
* a callback function (that takes a DOM element as its argument)

[JS BIN](https://jsbin.com/yadakob/1/edit?js,console)

##

**Question 25** 

Testing your this knowledge in JavaScript: What is the output of the following code?

```js

	var length = 10;
	function fn() {
		console.log(this.length);
	}

	var obj = {
	  length: 5,
	  method: function(fn) {
	    fn();
	    arguments[0]();
	  }
	};

	obj.method(fn, 1);
	
```

[JS BIN](https://jsbin.com/paxutuz/edit?js,console)

##

**Question 26**

Consider the following code. What will the output be, and why?

```js

(function () {
    try {
        throw new Error();
    } catch (x) {
        var x = 1, y = 2;
        console.log(x);
    }
    console.log(x);
    console.log(y);
})();

```

[JS BIN](https://jsbin.com/zivavup/1/edit?js,console)

##

**Question 27**

What will be the output of this code?

```js

var x = 21;
var girl = function () {
    console.log(x);
    var x = 20;
};
girl ();




*/

```


```js

/*

Neither 21, nor 20, the result is undefined

It’s because JavaScript initialization is not hoisted.

(Why doesn’t it show the global value of 21? The reason is that when the function is executed, it checks that there’s a local x variable present but doesn’t yet declare it, so it won’t look for global one.)

*/

```

##

**Question 28**

What will this code print?

```js

for (let i = 0; i < 5; i++) {
  setTimeout(function() { console.log(i); }, i * 1000 );
}

```

```It will print 0 1 2 3 4, because we use let instead of var here. The variable i is only seen in the for loop’s block scope.```

##

**Question 29**

What do the following lines output, and why?

```js

console.log(1 < 2 < 3);
console.log(3 > 2 > 1);

```

```js

/*

The first statement returns true which is as expected.

The second returns false because of how the engine works regarding operator associativity for < and >. It compares left to right, so 3 > 2 > 1 JavaScript translates to true > 1. true has value 1, so it then compares 1 > 1, which is false.

*/

```

##

**Question 30**

Imagine you have this code:

```js

var a = [1, 2, 3];

```

a) Will this result in a crash?

```js

a[10] = 99;

```

b) What will this output?

```js

console.log(a[6]);

```

[JS BIN](https://jsbin.com/vonizof/1/edit?js,console)


##

**Question 31**

What is the value of typeof undefined == typeof NULL?

```
    The expression will be evaluated to true, since NULL will be treated as any other undefined variable.

    Note: JavaScript is case-sensitive and here we are using NULL instead of null
```

##

**Question 32**

What would following code return?

```js
console.log(typeof typeof 1);
```

``` typeof 1 will return "number" and typeof "number" will return string. ```

##

**Question 33**

What will the following code output and why?

```js
var b = 1;
function outer(){
   	var b = 2
    function inner(){
        b++;
        var b = 3;
        console.log(b)
    }
    inner();
}
outer();
```

[JS BIN](https://jsbin.com/cicojey/1/edit?js,console)


**Question 34**

What will be the output of the code below?

```js

var y = 1;
  if (function f(){}) {
    y += typeof f;
  }
  console.log(y);


```

[JS BIN](https://jsbin.com/modoru/1/edit?js,console)


**Question 35**

What is the drawback of creating true private methods in JavaScript?

```

One of the drawbacks of creating true private methods in JavaScript is that they are very memory-inefficient, as a new copy of the method would be created for each instance.

```

[JS BIN](https://jsbin.com/fuciced/edit?js,console)


**Question 36**

Write a mul function which will produce the following outputs when invoked?

```js

console.log(mul(2)(3)(4)); // output : 24 
console.log(mul(4)(3)(4)); // output : 48

```


[JS BIN](https://jsbin.com/yotadih/1/edit?js,console)


**Question 37**

What will be the output of the code below?

```js

var bar = true;
console.log(bar + 0);   
console.log(bar + "xyz");  
console.log(bar + true);  
console.log(bar + false);   

```

[JS BIN](https://jsbin.com/tojiyuv/1/edit?js,console)


**Question 38**

What is the difference between the function declarations below?

```js

var foo = function(){ 
    // Some code
}; 

function bar(){ 
    // Some code
}; 

```

*The main difference is the function foo is defined at run-time whereas function bar is defined at parse time. *


**Question 39**

What will be the output of code below?

```js
var salary = "1000$";

 (function () {
     console.log("Original salary was " + salary);

     var salary = "5000$";

     console.log("My New Salary " + salary);
})();

```

[JS BIN](https://jsbin.com/sizeqes/1/edit?js,console)



