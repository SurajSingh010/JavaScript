# Javascript

> **what is javscript?**

*  JavaScript is a dynamic, weakly typed programming language which is compiled at 
runtime. It can be executed as part of a webpage in a browser or directly on any 
machine (“host environment”).

*  JavaScript was created to make webpages more dynamic (e.g. change content on a 
page directly from inside the browser).

* JavaScript is totally independent from Java and has nothing in common with Java.

> **How js is executed?**

* The source code is passed through a program called a compiler, which translates it into bytecode that the machine understands and can execute. In contrast, JavaScript has no compilation step. Instead, an interpreter in the browser reads over the JavaScript code, interprets each line, and runs it.

* Inside of browser JS code run inside JS engine. the most common JS engine we know is V8 (often called as chrome JS engine)

* [This video](https://www.youtube.com/watch?v=iLWTnMzWtj4&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=3&ab_channel=AkshaySaini) Beautifully explains about JS code execution which in the future will be very helpful in understanding concepts like "hoisting.

>**What is Typescript?**


* TypeScript is a strongly typed programming language that builds on JavaScript. It is a language that is a superset of JavaScript.

* JavaScript is a dynamically typed language, meaning that the software will not treat type differences as errors up until runtime. This often resulted in a lot of bugs and frustration. However, TypeScript offers optional static typing. Once static typing is declared, a variable does not change its type and can only take in certain values. The compiler alert developers of any type-related errors (syntax or semantic), which results in early bug detection.


# Basics Of Javascript

> 1. Javascript Control Flow Structure

* Control Flow is a fundamental concept in programming that allows you to dictate how your code runs under different conditions or until a certain condition is met.

* Control Flow is an important concept to learn in all programming languages, so the theory carries across multiple languages.

*  Probably the most common Control Flow Structure you will encounter is some variety of the if, else, else if structure.
  * For examples:
  1. **If:**
       <p> The if statement simply makes an evaluation and then does something depending on if the evaluation was true or false.</p>
>For examples:       
```javascript
if (23> 34) {
  console.log("23 is greater than 34");
}
 
```   
  2. **Else:**
            <p>The example above will do something if the statement evaluates to true, but what if we wanted to do something if it evaluates to false? Well, we could use the **else** clause.</p>
> For examples:

```javascript
if (23> 34) {
  console.log("23 is greater than 34");
}else {
  console.log("24 is greater");
}

```
    
3. **Else If:**
   <p>  If we want to evaluate one statement, or evaluate a second statement, we could use else if.</p>
> For examples:
```javascript
if (23> 34) {
  console.log("23 is greater than 34");
}else if (45> 65) {
  console.log("45 is greater than 65");
}else {
  console.log("None of the statements are true");
}
```

4. **Switch:**
            <P>Writing out lots of **if statements** can become a bit tedious if you have lots of possibilities. A simple way around this problem is to use a **switch** statement instead.</p>

> For examples:
```javascript
var tress= "green";
switch(tress){
case "purple":    
    console.log("Trees are purple");
    Break;
case "pink":
    console.log("Trees are pink");
		break;
case "green":
    console.log("Trees are green");
		break;    
default:
    console.log("Trees are of unknown colour");    
}
```
<p>So instead of writing 3 if statements and an else statement, we can just write a switch statement that reduces the amount of code we need to write. In this example, the switch statement evaluates the variable “trees” and runs code depending on what it equals. If it does not equal any of the supplied cases, it falls back to the default case.</p>
    
5. **Break:**
           <p> If you want to stop a loop at a certain point, before the condition has been satisfied, you can use a break.
           </p>

 > For examples:
 ```javascript
 let log = ["Good", "Good", "Good", "Error", "Good"];
let length = log.length;

for (let i = 0; i < length; i++) {
  if (log[i] === "Good") {
    console.log("System running ok");
  } else {
    alert("OMG there's an error!");
    break;
  }
}

```
<p>In this example, we loop through the array and a print a message if the system is ok. But if there is an error in the log, we need to break out of the loop straight away and send an alert.</p>

> 2. Operators

<p> Here are some more operators that you can use in your if ,else if statements.</p>

* \> -less than
* \>= -less than equal to
*  < -greater than
*  <= -Greater Than Equal To
*  ==   - Equal to (will convert datatypes during this conversion while comparison)
*  === - Equal to(will not convert datatypes during this conversion while comparison)
*   ! =    - Not equal to
*  &&   - AND Operator (Both the condition should be true )
* ||       - OR Operator (One of the condition should be true )
* ++ - Post/Pre Increment
* \--  - Post/Pre Decrement
> Examples of and operator

```javascript

let sky= "blue";
let grass= "green";

if (sky=== "blue"&& grass=== "green") {
  console.log("The sky is blue and the grass is green");
}

```
> Examplesn of OR Operator
```javascript
let sky= "blue";
let grass= "green";

if (sky === "blue" || grass === "green") {
  console.log("The sky might be blue and / or the grass might be green");
}
```

> 3. Javscript Loops

<p>You may encounter situations, when a block of code needs to be executed several number of times. In general, statements are executed sequentially: The first statement in a function is executed first, followed by the second, and so on.</p>

>**Types of loops in JS**
* **For** - loops through a block of code a number of times
* for/in - loops through the properties of an object
* for/of - loops through the values of an iterable object
* while - loops through a block of code while a specified condition is true
* do/while - also loops through a block of code while a specified condition is true

> **1. For loop**
   
 <p> When you want to run a block of code number of time until certain condition for loop is used.</p>

 > For example
```javascript
for (let i= 0; i< 10; i++) {
  console.log("Hello x "+ i);
}
```

>**2. For in Loop**
 <p> When you want to loop through an Object, you can’t use a counter because the properties have names, not numbers.</p>

> Take this object for examples:
```javascript
const cat = {
  name: "Francine",
  age: "2 months",
  colour: "grey",
};
```
<p> In order to print the properties and the values from this Object, we could use the for in loop like this:
</p>

```javascript
for (let property in cat) {
  console.log(property + ": " + cat[property]);
}
```
<p>
Here we are getting each property from the Cat Object. We can then access the value of each property using bracket notation and passing the property name.
</p>

>**3. For lopps**

1. The **while** loop is similar to the **for** loop in that it will keep running your code until a condition is satisfied. **for** loops are great if your code relies on counting or you are iterating through a known set of items, but sometimes you need to loop through something using a different conditional.

1. **while** loops can be used to do the same job as a **for** loop, but it means you have to write more code out.

```jsx
// While 
var i = 0;
while (i <= 100) {
  console.log(i);
  i++;
}

// For
for (let i = 0; i <= 100; i++) {
  console.log(i);
}
```

 It’s better to use **while** loops when you need to use a condition such as *true* or *false*.

```jsx
let mySwitch = true;

while (mySwitch) {
    console.log("I'll only bother you once");

    mySwitch = false;
}
```

In the example above, the **while** loop will keep looping whilst the switch is set to true.

>**4. Do while Loop**
```jsx
let i = 0;

do {
  console.log("i = " + i);
  i++;
} while (i < 100);

// expected output: 
"i": 0
"i": 1
"i": 2
	upto
"i": 99
```
<p>The do while loop is similar to the while loop in that it will run your code until a condition is satisfied. However, the evaluation happens at the end of the loop, rather than the start, so your code will always run at least once.</p>

> **5. for of loop**
   <p>The for...of statement creates a loop iterating over iterable objects, including: built-in String, Array, array-like objects</p>

> For examples

```jsx
const array1 = ['a', 'b', 'c'];

for (const element of array1) {
  console.log(element);
}

//expected output: "a"
//expected output: "b"
//expected output: "c"
```
>**4. Javascript Functions**

1. A function is a block of code designed to perform a particular task. A function is executed when "something" invokes it (calls it).

>**Syntax:**

2. A function is defined with the ***function*** keyword, followed by a **name**, followed by parentheses **()**.

3. Function names can contain letters, digits, underscores, and dollar signs (same rules as variables).

1. The parentheses may include parameter names separated by commas:**(*parameter1, parameter2, ...*)**

1. The code to be executed, by the function, is placed inside curly brackets: **{}**
```jsx
function name(parameter1, parameter2, parameter3) {
  // code to be executed
}
```
>Example:

We have one sum of two number which accept two **parameter** and it prints the addition of two number.

```jsx
function sum_two_number(a,b) {
  console.log(`Addition: ${a+b}`)
}
```
Now how to use(call) this function. Simply call the function and pass the two **argument**.
```jsx
sum_two_numbe(10,20);

//expected output
// Addition: 30
```
**Parameters vs Arguments**

The terms *parameter* and *argument* are often used interchangeably, because the context usually makes it clear what the intended meaning is. The following is a rule of thumb for distinguishing them.

- ***Parameters*** are used to define a function. They are also called formal parameters and formal arguments. In the following example, **param1** and **param2** are parameters:
    
    ```jsx
    function foo(param1, param2) {...}
    ```
    
- ***Arguments*** are used to invoke a function. They are also called actual parameters and actual arguments. In the following example, **3** and **7** are arguments:
    
    ```jsx
    foo(3, 7);
    ```
> **5. Scope**

*  Scope is the accessibility of variables, functions, and objects in some particular part of your code during runtime. In other words, scope determines the visibility of variables and other resources in areas of your code. 

*  If variables are declared using **`let`** and **`const`** then it is a blocked scoped variable.

*  Variables declared with the `**var`** keyword can NOT have block scope.

* In the JavaScript language there are two types of scopes:

- Global Scope
- Local Scope
- Block Scope
- Function Scope

>**1. Block Scope**

Variables declared inside a { } block cannot be accessed from outside the block.

>For example

```jsx
{
let x=2;
// x can be used here
}
// x can NOT be used here
```

>**2. Local Scope**

Variables declared within a JavaScript function, become **LOCAL** to the function.

```jsx
// code here can NOT use carName

function myFunction() {
  let carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```

>**3. Function Scope**

JavaScript has function scope: Each function creates a new scope. Variables defined inside a function are not accessible (visible) from outside the function.

Variables declared with `var`, `let` and `const` are quite similar when declared inside a function. They all have **Function Scope**

```jsx
function myFunction() {  
			var carName = "Volvo";   
// Function Scope
}
```

>**4. Global Scope**

A variable declared outside a function, becomes **GLOBAL**.

```jsx
let carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}
```

>**6. Array**

In JavaScript, array is **a single variable that is used to store different elements**. ... Unlike most languages where array is a reference to the multiple variable, in JavaScript array is a single variable that stores multiple elements.

>**There is two way to declare an array:**

```jsx
let House = [ ]; // method 1 
let House = new Array(); // method 2
``` 
### **Initialization of an Array**
>**Example (For Method 1):**
```jsx
// Intializing While Declaring
let car = ["Maruti","Mustang_Gt","Mercedez_Benz"];

```
>**Example(For Method 2):**

```jsx
// Creates an array having elements 1 to 5
let  numbers = new Array(1,2,3,4,5);

// creates an array of 3 undefined elements
let number1= new Array(3);

```

### **Array Methods**
> **1. Concat()**
    
<p>It returns a new array object that contains two or more merged arrays.

```jsx
let array1=[1,2,3,4]
let array2=[8,9,10]
console.log(array1.concat(array2));

//expected output
[1,2,3,4,8,9,10]
```
>**2. find()**
<p> It returns the value of first elemnt that satisfies the specified condition.
</p>

```jsx
let array=[1,2,3,4];
array.find(c=>c>1)

// Expected Output
2
```
>**3. findIndex()**
<p> it returns the index value of the first element in the given array that sastisfies the specified condition.</p>


```jsx
let array=[1,2,3,4,5,6]
array.findIndex((n)=>n==6)

//expected output
5
```
>**4. includes()**
<p> it checks whether the given array contains the specified element. </p>

```jsx
let array=[1,2,3,4,5]
array.includes(5)
// expected output 1: true
array.includes(7)
// expected output 2: false
```
> **5. pop()**

It removes and returns the last element of an array.

```jsx
let array=[1,2,3,4];

array.pop()
//expected output:
 4

console.log(array)
//ouptut
[1,2,3]
```
> **6. shift()**

It removes and returns the first element of an array.

```jsx
let array1=[1,2,3,4];

array1.shift()
//expected output:
 1

console.log(array1)
//ouptut
[2,3,4]
```
>**7. push()**

it adds one more elements to the end of the array

```jsx
let array1=[1,2,3,4];

array1.push(5)
//expected output:
 5

console.log(array1)
//ouptut
[1,2,3,4,5]
```
>**8. unshift()**

It adds one or more elements in the beginning of the given array.

```jsx
let array1=[1,2,3,4];

array1.unshift(5)
//expected output:
 5

console.log(array1)
//ouptut
[5,1,2,3,4]
```
>**9. map()**

It calls the specified function for every array element and returns the new array
```jsx
let array1=[1,2,3,4];

array1.map((x)=>x*2)

//expected output
 [2, 4, 6, 8]
```

>**10. forEach()**

It invokes the provided function once for each element of an array.

```jsx
let array1=[1,2,3,4];

array1.forEach((x)=>console.log(x))

//expected output
1
2
3
4
```
>**11. filter()**
* The filter() method creates a new array filled with elements that pass a test provided by a function.

* The filter() method does not execute the function for empty elements.

* The filter() method does not change the original array.

```jsx
const ages = [32, 33, 16, 40];

const result = ages.filter(checkAdult);

function checkAdult(age) {
  return age >= 18;
}

//expected output
Get every element in the array that has a value of 18 or more:

32,33,40
```



>**12. reduce()**

This used to reduce the array to a single value and executes a provided function for each value of the array (from left-to-right) and the return value of the function is stored in an accumulator.

```jsx
const array1 = [1, 2, 3, 4];
const reducer = (previousValue, currentValue) => previousValue + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15
```


>  **7.  object**

* In JavaScript, an **object is a standalone entity, with properties and type**. Compare it with a cup, for example. A cup is an object, with properties. A cup has a color, a design, weight, a material it is made of, etc. The same way, JavaScript objects can have properties, which define their characteristics.

* Objects are variables too. But objects can contain many values.

* This code assigns **many values** (Fiat, 500, white) to a **variable** named car:

```jsx
const car={
name:"Fiat",
model:500,
color:white,
};
```

>**Object Definition**

You define (and create) a JavaScript object with an object literal. 

>Example

```jsx
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
```

>**Object Properties**

The **name:values** pairs in JavaScript objects are called **properties**:

|Property|Property Value|
|----|----|
|firstName|Suraj|
|lastName|Singh|
|age|22|
|eyeColor|Brown|

>**Accessing Object Properties**

You can access object properties in two ways:

```jsx
objectName.propertyName

or

objectName["propertyName"]
```

```jsx
// example1
person.lastName;

//example2
person["lastName"];
```

Objects can also have **methods**. Methods are **actions** that can be performed on objects. Methods are stored in properties as **function definitions**.

Example

```jsx
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue",
	fullName: function() {
			return this.firstName + " " + this.lastName;
			}
};
```










        
