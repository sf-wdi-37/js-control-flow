<!--
Creator: SF WDI Team
Last Edited by: Jean
Location: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# JavaScript Control Flow

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

"Control flow" refers to the way our computers move through a program's code.   Understanding control flow allows us to trace the flow of a program based on its code. This skill is essential for programming in every language and paradigm.  In particular, **conditionals** and **loops** are fundamental to understanding modern programming languages.

### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- Predict the output of boolean expressions, including "truthy" and "falsey" values.
- Write syntactically correct conditional statements.
- Compare & contrast for and while loops.

### Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- Create and change variables of many types in the Chrome developer tools.
- Access and change values with objects and arrays.


### Boolean Logic

At the very lowest level, sequences of 1s and 0s called "binary code" drive everything a computer does, from outputting text in the terminal, to displaying complex video game graphics, to communicating with other computers across the internet.

Boolean logic is the closest web developers need to get to thinking about binary code.  In pure boolean logic, every value is either true or false.

#### Boolean Values in JavaScript

JavaScript has `true` and `false`:

```js
typeof(true)    // boolean
typeof(false)   // boolean
```

JavaScript also treats every value as "truthy" or "falsey".  

To work within this system, we have to memorize which values are "falsey." It can take practice to quickly predict results, but developers can use this truthy/falsey system to write shorter code for conditional expressions.

To check whether some value is truthy or falsey, try the following structure in your JavaScript console:

```js
var myValue = "fishing";
if(myValue){
  console.log(myValue, " is truthy!");
} else {
  console.log(myValue, " is falsey!");
}
```

#### Basic Boolean Operators

An "operator" is represents a simple operation that can be done on an input to give some output, like `+` and `-` from math!

These operators give boolean outputs, but in JavaScript their inputs could be anything.

| English | "and" | "or" | "not" | "not not" |
| ------------- |:-------------|:-------------|:-------------| :------- |
| Javascript | `&&` | &#124;&#124; | `!` | `!!` | |  
| e.g. | `a && b` | a  &#124;&#124; b | `!b` | `!!b` |
| spoken | A and B | A or B | not B | not NOT B |

> The `!` operator is sometimes pronounced 'bang!'.


#### Boolean Comparison Operators

These operators give boolean outputs, but in JavaScript their inputs could be anything.  

| strict equality | loose equality | not strictly equal | not loosely equal | greater than | less than | greater than or equal to | less than or equal to |
| ------------- |:-------------|:-------------|:-------------|:-------------|:-------------|:-------------|:-------------|
| `===` | `==` | `!==` | `!=` | `>` | `<` | `>=` | `<=` |
| spoken | A and B | A or B | not B | not NOT B |

> Strict equality checks type and value, while loose equality only compares value.

## Check for Understanding

1. What is the outcome of the following expressions?

  * true || false
  * false && false
  * true && false
  * (false || true) && true
  * false && ((true || false) && (false || true))

  <details><summary>answers</summary>
  ```js
  * true || false    	   // true
  * false && false	     // false
  * true && false	       // false
  * (false || true) && true	// true
  * false && ((true || false) && (false || true))	// false
  ```
  Note that JavaScript is lazy when it can quit evaluating a boolean expression early. For example, in the last expression above, you can tell from just the first `false &&` that the whole expression will be false.
  </details>

1. Which of the following are falsey?
  * `"abc"`
  * `""`
  * `1`
  * `-0`
  * `Math.PI`
  * `NaN`
  * `Array`
  * `[]`
  * `Object`
  * `{}`
  * `null`
  * `undefined`

  <details><summary>answers</summary>
  truthy: `-0`, `""`, `NaN`, `null`, `undefined`      
  </details>

1. What is the outcome of the following expressions?
  *  1 && 6
  *  0 || "hi"
  *  ["a","b","c"] || "123"
  *  false || null

  <details><summary>answers</summary>
  ```js
  *  1 && 6                     // 6
  *  0 || "hi"                  // "hi"
  *  ["a","b","c"] || "123"     // ["a","b","c"]
  *  false || null              // null
  ```
  </details>




### Conditionals

![commuter flow chart](https://camo.githubusercontent.com/f545891799690188cd2d25b1d06687af66627ab1/687474703a2f2f63646e2e746865626f6c646974616c69632e636f6d2f7061706572636c69702f68746d6c5f696d616765732f33353130382f696d616765732f6f726967696e616c2f77696c6c2d796f752d62652d6c6174655f66696e616c2e706e67)

#### `if/else`

The boolean expression inside an `if`'s parentheses will always be evaluated as truthy or falsey to determine what will happen next.

A diehard Giants fan might have the following rules for baseball games:

```js
if (giantsPlaying) {
  getTickets();
}

if (!giantsPlaying) {
  watchOnTV();
}
```

We can rephrase this more succinctly using `if` and `else`.

```js
if (giantsPlaying) {
  getTickets();
} else {
  watchOnTV();
}
```


A slightly more complex boolean expression will help our Giants fan save some money by adding another requirement to purchase tickets:

```js
if (giantsPlaying && gameInSF){
  getTickets();
} else {
  watchOnTV();
}
```

#### `else if`

 Here's a sample ruleset for commuters:

```js
var destination = "GA";
if ( hasBike ) {
  rideToGA();
} else if ( hasTransitPass ) {
  busToGA();
} else {
  walkToGA();
}
```


#### Nested `if`s

A strategy for choosing what to drink:

```js
var drink;

if (sleepy) {
  if (before5pm) {
    drink = "coffee";
  } else {
    drink = "black tea";
  }
} else {
  if (hungry){
    drink = "smoothie";
  } else {  
    drink = "water";
  }
}
```


#### `switch`


A `switch` statement checks the value of one variable or expression to determine which of many "cases" to jump to.  Here's code for a vending machine with a different price for each row:

```js
switch (row){
	case 1: 	
		price = 0.25;
		break;
	case 2:
		price = 0.50;
		break;
	case 3:
		price = 0.75;
		break;
	case 4:
		price = 1.00;
		break;
	default:  // the rest of the products (rows 5-7)
		price = 1.25;
}			
```


###Conditional Control Flow Tricks

**Loose Control Flow** (watch out for edge cases!)

```js
if ( username ) {
	// submit signup form
}

// same intent as

if ( username.length > 0) {
	// submit signup form
}
```

**Ternary operator**

```js
var username = last_name ? first_name + last_name : first_name;

// same as

var username = first_name;
if ( last_name ) {
	username = first_name + last_name;
}
```

**Conditional assignment: `||` to set to a default value**

```js
var bestCity = yourCity || "San Francisco";

// same as

var bestCity = "San Francisco";
if ( yourCity ) {
	bestCity = yourCity;
}

```

**Conditional Execution: `&&` to handle issues**

```js
badThing && alert("Uh oh!")

// same as

if ( badThing ) {
	alert("Uh oh!");
}

```

#### Check for Understanding: Conditionals!

Whiteboard with a partner:

Jimmy loves roller coasters, but there are a bunch of rules (ugh!) for riding:

For starters, it costs 5 tokens. Here's how we might code that:

```js
// assume we'll have a tokens variable
// storing the number of tokens
if ( tokens >= 5 ) {
    console.log("Step right up!");
} else {
    console.log("Sorry, you can't ride")
}
```

Pseudocode or edit the code above to check the following requirements:

1. Add a requirement that riders must be at least 4ft tall.   
  <details><summary>answer</summary>
    ```js
    if ( tokens >= 5 && height >= 4) {
        console.log("Step right up!");
    } else {
        console.log("Sorry, you can't ride.");
    }
    ```
  </details>

2. Add a requirement that riders must be at least 12 years old.  
  <details><summary>answer</summary>
    ```js
  	if ( tokens >= 5 && height >= 4 && age >=12) {
  	    console.log("Step right up!");
  	} else {
  	    console.log("Sorry, you can't ride.");
  	}
    ```
  </details>

3. Replace the previous rule: now riders under 12 can participate when they're accompanied by an adult.  

  <details><summary>answer</summary>
    ```js
    if ( tokens >= 5 && height >= 4 ) {
      if (age >= 12 || hasAdult){
          console.log("Step right up!");
      } else {
        console.log("Sorry, you can't ride.");
      }
    } else {
        console.log("Sorry, you can't ride.");
    }
    ```
  </details>

4. (If the boss isn't looking, you can go on in!)  


  <details><summary>answer</summary>
    ```js
    if (!bossLooking){
  		console.log("Step right up!");
  	} else {
  		if ( tokens >= 5 && height >= 4 ) {
  			if (age >= 12 || hasAdult){
  			    console.log("Step right up!");
  			} else {
  				console.log("Sorry, you can't ride.");
  			}
  		} else {
  		    console.log("Sorry, you can't ride.");
  		}
  	}
    ```
  </details>

5. Riders with a park pass get in free.


  <details><summary>answer</summary>
    ```js
    if (!bossLooking){
  		console.log("Step right up!");
  	} else {
  		if ( (tokens >= 5 || hasPass) && height >= 4 ) {
  			if (age >= 12 || hasAdult){
  			    console.log("Step right up!");
  			} else {
  				console.log("Sorry, you can't ride.");
  			}
  		} else {
  		    console.log("Sorry, you can't ride.");
  		}
  	}
    ```
  </details>



### Loops

Whenever we want to repeat something in code, we use a loop.  We can think of every loop as three parts: **initialization** (setup), **continue condition**, and **update expression**.


#### `while` loops


![endless pizza cartoon](http://38.media.tumblr.com/7d49b42da305f9d6302110c50ac6894e/tumblr_mmz3qo9q1N1rdutw3o1_400.gif)  
_While pizza is available, take pizza!_

In while loops, the initial setup happens before the loop. The continue condition goes inside the `while` parentheses. The updates happen inside the loop.



```js
var minutesBeforeWork = 80;                    // setup:  plan to wake up early
while (minutesBeforeWork > 30) {               // continue condition: leave enough time to get day clothes on
  minutesBeforeWork = minutesBeforeWork - 5;   // update: hit snooze!
}
```

#### `for` loops

For loops allow the setup, continue condition, and update expression to live inside the `for` loop parentheses.

```js
for (var count = 1; count <= 3; count++){
  console.log(count);
}
console.log("Go Team!");
```


For loops for arrays usually use a counter variable to move through the indices of the array.

```js
var friends = ["Bali", "Nat", "Kelly"]
for (var i = 0; i < friends.length; i++) {
  console.log(friends[i] + " is a nice person");
}

```

We'll see how to use special iterator methods to move through arrays sequentially. Iterator methods are wonderful for that.  For loops in JavaScript are much more flexible than iterator methods, though, so it's important to get a handle on them.


For loops only really need a continue condition (or the loop will never end!). We can do setup before the loop, and we can do updating inside the loop. In this way, a for loop can look a lot like a while loop.

```js
var minutesBeforeWork = 540;
for( ; minutesBeforeWork > 30; ) {
  minutesBeforeWork = minutesBeforeWork - 5;
}
```

Here's an example that takes advantage of JavaScript for loops' flexibility (perhaps at the cost of readability!).  

```js
for (var height=48, yearlyGrowth=1, age=8; age<=18; height += yearlyGrowth){
   if (growthSpurt){
      yearlyGrowth = 6;
   } else {
      yearlyGrowth = 1;
   }
   age++;
}
console.log("Adult height is ", height, " inches!");
```

#### `break`

The reserved word `break` will break us out of a loop immediately.  

```js
for (var i = 0; i < 10; i+=2) {
  console.log(i);
  break;
}

var j=0;
while (j < 10) {
  console.log(j);
  break;
  j += 2;
}
```

#### Check for Understanding: Loops!

Use a `for` or `while` loop to console log a shuttle launch countdown:  "T minus 10", then "9", "8", "7", "6", "5", "4", "3", "2", "1", "0", "Liftoff!".

<details><summary>answer</summary>
  ```js
  console.log("T minus 10");
  for (var i=9; i>=0; i--){
    console.log(i);   // can log i.toString() to convert
  }
  console.log("Liftoff!");
  ```

  ```js
  console.log("T minus 10");
  i = 9;
  while (i>=0){
    console.log(i);   // can log i.toString() to convert
    i--;
  }
  console.log("Liftoff!");
  ```
</details>


### Independent Practice

Practice with this [training](https://github.com/sf-wdi-labs/js-control-flow-training/).  


### Closing Thoughts

The most important things to practice right now are:

- predicting the output of boolean expressions.
- working with more complex, nested conditionals and/or loops.
- remembering the three-part structure of loops and the syntax for each kind of loop.
