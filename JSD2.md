# Javascript Advance
>**1. Hosting in JavaScript?**

Hosting in javascript by which we can access a variable and function even before you intialize it  or you have put some value or you can access without any error.

> for examples

```jsx
getName();
console.log(x);
console.log(getName);
var x=7;
function getName(){
    console.log("Namste_javascript");
}
//Expected output is
Namste_javascript
undefined
f getName{

}
```
even before  code start executing  a memory is allocated to variable and function.
```jsx
Namste_javascript
undefined
f getName{

}
```

if we remove var x=7 then x= not defined

```jsx
getName();
console.log(x);
console.log(getName);
var x=7;
function getName2(){

}
var  getName=()=>{
    console.log("Namste_javascript");

}

//expected output
getName is not a function and is allocated even before executing as undefined just like variable and f getName2() conatins proper function
```

```jsx
getName();
console.log(x);
console.log(getName);
var x=7;
var getName2= function(){

}
var  getName=()=>{
    console.log("Namste_javascript");

}
```
Even in this way also we declared a function but memory is allocated in global sapce is getName2: undefined and getName: undefined.

```jsx
getName();
console.log(x);
console.log(getName);
var x=7;
function getName(){
    
}
```
Only in case of proper function Declaration we get an getName as a function in global space of call stack

>**2. Passed by value and passed by refrence**

* In javascript, primitive datatypes are passed by value and non-primitive datatypes are passed by refrence
* For understanding passed by value and passed by reference, we need to understand what happens when we create a variable and assign a value to it,

```jsx
let x=2;
```

* In the above example, we created a variable x and assigned it a value “2”. In the background, the “=” (assign operator) allocates some space in the memory, stores the value “2” and returns the location of the allocated memory space. Therefore, the variable x in the above code points to the location of the memory space instead of pointing to the value 2 directly.

* Assign operator behaves differently when dealing with primitive and non primitive data types.
>**assigningment operator dealing with primitive type:=>**

In the above example, assign operator knows that the value assigned to y is a primitive type (number type in this case), so when the second line code executes, where the value of y is assigned to z, the assign operator takes the value of y (234) and allocates a new space in the memory and returns the address. Therefore, variable z is not pointing to the location of variable y, instead it is pointing to a new location in the memory.

```jsx
let y = #8454; // y pointing to address of the value 234

let z = y; 
        
let z = #5411; // z pointing to a completely new address of the value 234
        
// Changing the value of y
y = 23;
console.log(z);  
// Returns 234, since z points to a new address in the memory so changes in y
 //will not effect z
```

From the above example, we can see that primitive data types when passed to another variable, are passed by value. Instead of just assigning the same address to another variable, the value is passed and new space of memory is created.

>**Assign operator dealing with non-primitive types:=>**

```jsx
let obj = { name: "Vivek", surname: "Bisht" };
let obj2 = obj;
console.log (obj ===obj2);

//output : true


```
* In the above example, the assign operator, directly passes the location of the variable obj to the variable obj2. In other words, the reference of the variable obj is passed to the variable obj2.

```jsx
let obj = { name: "Vivek", surname: "Bisht" };
let obj2 = obj;        
obj.name = "Akki"; *// changing the value of obj*        
console.log(obj2);
        
*// output Returns {name:"Akki", surname:"Bisht"}since both the variables are pointing to the same address.
```

* From the above example, we can see that while passing non-primitive data types, the assign operator directly passes the address (reference).

* Therefore, non-primitive data types are always **passed by reference.**

>**3. Higher Order Function**

a function which takes another function as arguments OR Return a function from it is called a higher order Function. 

Higher order functions are a result of functions being **first-class citizens** in javascript.

>Examples of higher order functions:

```jsx
function x(){
    console.log("namstejavascript");

}
function y(x){
    x();

}
```
in above examples y takes another function as higher order function and x is a callback function.

>**4. This Keyword**

**The “this” keyword refers to the object that the function is a property of. The value of “this” keyword will always depend on the object that is invoking the function.**

Confused? Let’s understand the above statements by examples:

```jsx
function doSomething() {
  console.log(this);
}
        
doSomething();
```

What do you think the output of the above code will be?

***Note - Observe the line where we are invoking the function.**

Check the definition again:

**The “this” keyword refers to the object that the function is a property of.**

In the above code, function is a property of which object?

Since the function is invoked in the global context,**the function is a property of the global object.**Therefore, the output of the above code will be **the global object.** Since we ran the above code inside the browser, the global object is **the window object.**

Example 2:

```jsx
let obj = {
    name:  "vivek",
    getName: function(){
    console.log(this.name);
  }
}
        
obj.getName();
```

In the above code, at the time of invocation, the getName function is a property of the object **obj**, therefore, the **this** keyword will refer to the object **obj**, and hence the output will be “vivek”.

Example 3:

```jsx
 let obj = {
    name:  "vivek",
    getName: function(){
    console.log(this.name);
  }
        
}
        
let getName = obj.getName;
        
let obj2 = {name:"akshay", getName };
obj2.getName();
```

Can you guess the output here?

The output will be “akshay”.

Although the getName function is declared inside the object **obj**, at the time of invocation, getName() is a property of **obj2**, therefore the “this” keyword will refer to **obj2**. The silly way to understanding the **this** keyword is, whenever the function is invoked, check the object before the **dot**. The value of **this** keyword will always be the object before the **dot**.

If there is no object before the dot like in example1, the value of this keyword will be the global object.

Example 4:

```jsx
let obj1 = {
    address : "Mumbai,India",
    getAddress: function(){
    console.log(this.address); 
  }
}
       
let getAddress = obj1.getAddress;
let obj2 = {name:"akshay"};
obj2.getAddress();
```

Can you guess the output?

**The output will be an error.**

Although in the code above, the this keyword refers to the object **obj2**, obj2 does not have the property “address”‘, hence the getAddress function throws an error.

>**call(), apply(), bind():=>**

>**a)=> call():**

* We can do function borrowing and we can borrow a function from another object and use it with data of some other object.

```jsx
let name = {
    firstname:"suraj",
    lastname: "Singh"
    printFullName: function(){
        console.log(this.firstname+" "+lastname)
    }
}
name.printFullName();

let name2 ={
    firstname:"sachin"
    lastname:"Tendulkar"

}
name.printFullName.call(name2);

// expected output is 
suraj singh
Sachin Tendulkar
```
* we can also remove printFullName method outside to use it multiple times.
```jsx
let name = {
    firstname:"suraj",
    lastname: "Singh"
   
}
let printFullName = function(){
        console.log(this.firstname+" "+lastname)
    }
printFullName.call(name);

let name2 ={
    firstname:"sachin"
    lastname:"Tendulkar"

}
printFullName.call(name2);

// expected output is 
suraj singh
Sachin Tendulkar

```
>Let's just take a one more examples where we cover apply() and bind() methods.

```jsx
let name = {
    firstname:"suraj",
    lastname: "Singh"
   
}
let printFullName = function(hometown, state){
        console.log(this.firstname+" "+lastname+"from"+hometown+ "," + state);
    }
printFullName.call(name);

let name2 ={
    firstname:"sachin"
    lastname:"Tendulkar"

}
printFullName.call(name, "thane","maharashtra");
printFullName.call(name2, "mumbai","maharashtra");
// expected ouput is 
suraj singh from  thane, maharshtra
sachin Tendulkar from mumbai,maharsahtra
```
* call method where ew passes a argument individually by comma sperated
>**b)=>apply()**

```jsx
printFullName.apply(name2, ["mumbai","maharashtra"])

```
the diffrence between call and apply is that in aplly second argument is passed as an array list.
>**c)=>bind()**

Looks Exactly same as call method only and the diffrence is instead of calling directly bind method returns a new function, where value of this is bound to the main(owner object).

>lets take  a example 
```jsx
let printMyName = PrintFullName.bind(name2, "mumbai", "maharsahtra");
console.log(printMyName);
printMyName();
```
Here we can return a fullname with an object and return as copy of method and when we invokes the function then it will print result as **sachin Tendulkar from mumbai,mahrashtra** otherwise it will return a function or copy of method.

>**5. Arrow Function**

* Arrow functions were introduced in the ES6 version of javascript.They provide us with a new and shorter syntax for declaring functions. Arrow functions can only be used as a function expression. 

* Let’s compare the normal function declaration and the arrow function declaration in detail:

```jsx
// Traditional Function Expression
let add = function(a,b){
  return a + b;
}

// Arrow Function Expression
let arrowAdd = (a,b) => a + b;
```

Arrow functions are declared without the function keyword. If there is only one returning expression then we don’t need to use the return keyword as well in an arrow function as shown in the example above. Also, for functions having just one line of code, curly braces { } can be omitted.

```jsx
// Traditional function expression
let multiplyBy2 = function(num){
  return num * 2;
}
// Arrow function expression
let arrowMultiplyBy2 = num => num * 2;
```

If the function takes in only one argument, then the parenthesis () around the parameter can be omitted as shown in the code above.

```jsx
var obj1 = {
  valueOfThis: function(){
    return this;
  }
}
var obj2 = {
  valueOfThis: ()=>{
    return this;
  }
}

obj1.valueOfThis(); // Will return the object obj1
obj2.valueOfThis(); // Will return window/global object
```

* The biggest difference between the traditional function expression and the arrow function, is the handling of the **this** keyword. By general definition, the **this** keyword always refers to the object that is calling the function. 

* As you can see in the code above, **obj1.valueOfThis()** returns obj1, since **this** keyword refers to the object calling the function. In the arrow functions, there is no binding of the **this** keyword.

* The **this** keyword inside an arrow function, does not refer to the object calling it. It rather inherits its value from the parent scope which is the window object in this case. Therefore, in the code above, **obj2.valueOfThis()** returns the window object.

>**6. Rest parameter and Spread Operator**

>**a) Spread Operator**

* spread operator is three periods and this operator allows expressions to be expanded in places where multiple arguments and varibles are expected.
 
```jsx
// add the element of an existing array into an new array
var certsToAdd = ['algorithms and data-structure', 'Front End libraries'];
var certifications = ['python', ...certsToAdd, 'data visulaization', 'Java Programming']
console.log(certifications);
//Expected output is:=>  ['python', 'algorithms and data-structure', 'Front End libraries', 'data visulaization', 'Java Programming']
``` 
> one more examples are pass elements of an array as arguments to a function

```jsx
function addThreeNumbers(x, y, z){
    console.log(x+y+z)
}
var args = [1,2,3];
addThreeNumbers(...args);
//expected output is 6
```

>to copy arrays

```jsx
var arr = [1, 2, 3]
var arr2 = [...arr];
arr2.push(5);
console.log(arr);
console.log(arr2);
//Expected output is [1, 2, 3] and  [1, 2, 3, 5]
```
>Concatenate arrays
```jsx
var arr1=[0,1,2];
var arr2 = [3,4,5];
arr1 = [...arr1,"Hello",...arr2];
console.log(arr1)
// expected output is [0, 1, 2, 'Hello', 3, 4, 5]
```

>**b) Rest parameters**

* it is  a opposite of spread operator 

* rest parametrs collect a multiple element and condense into an a single array element.

>examples 
```jsx
function multiply(multiplier, ...theArgs){
    return theArgs.map(function(element){
        return multiplier *element;
    });
}

var arr = multiply(2, 1, 2 ,3);
console.log(arr)
//Expected output is [2, 4, 6]
```
- **Note- Key differences between rest parameter and spread operator:**
- **Rest parameter is used to take a variable number of arguments and turns into an array while the spread operator takes an array or an object and spreads it**
- **Rest parameter is used in function declaration whereas the spread operator is used in function calls.**



