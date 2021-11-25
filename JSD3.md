>**Day-3**

>**1. Promises in javascript**

**Promises are used to handle asynchronous operations in javascript.**

Before promises, callbacks were used to handle asynchronous operations. But due to limited functionality of callback, using multiple callbacks to handle asynchronous code can lead to unmanageable code.

Promise object has four states -

- **Pending** - Initial state of promise. This state represents that the promise has neither been fulfilled nor been rejected, it is in the pending state.
- **Fulfilled** - This state represents that the promise has been fulfilled, meaning the async operation is completed.

* Rejected - This state represents that the promise has been rejected for some reason, meaning the async operation has failed.

**i) resolve:** is a function that will be called, when the async operation has been successfully completed.

**ii)** **reject:** is a function that will be called, when the async operation fails or if some error occurs.

>Examples of a promise:

**Promises are used to handle asynchronous operations like server requests, for the ease of understanding, we are using an operation to calculate the sum of three elements.**

In the function below we are returning a promise inside a function:

```jsx
function sumOfThreeElements(...elements){
    return new Promise((resolve,reject)=>{
        if(element.length > 3){
            reject("only three ele,ments or less are allowed");

        }
        else{
            let sum =0;
            let i=0;
            while(i < elements.length){
                sum = sum + elements[i];
                i++;

            }
            resolve("Sum has been calculated:" +sum);

        }
    })
}
```
* In the code above, we are calculating the sum of three elements, if the length of elements array is more than 3, promise is rejected, else the promise is resolved and the sum is returned.

* We can consume any promise by attaching then() and catch() methods to the consumer.

**i)** **then():** method is used to access the result when the promise is fulfilled.

**ii)** **catch():** method is used to access the result/error when the promise is rejected.

In the code below, we are consuming the promise:
```jsx
sumOfThreeElements(4,5,6).then(result => console.log(result)).catch(error => console.log(error));
// In the code above, the promise is fulfilled so the then() method gets executed

sumOfThreeElements(7, 0, 33, 41).then(result => console.log(result)).catch(error => console.log(error));
// In the code above, the promise is rejected hence the catch() method gets executed

```

- **Settled** - This state represents that the promise has been either rejected or fulfilled.

A promise is created using the **Promise** constructor which takes in a callback function with two parameters, **resolve** and **reject** respectively.



>**2. Async/Await Function**

We all know that Javascript is a Synchronous which means that it has an event loop that allows you to queue up an action that won’t take place until the loop is available sometime after the code that queued the action has finished executing. But there’s a lot of functionalities in our program which makes our code Asynchronous. One of them is the Async/Await functionality.

>**i) Async:** 

It simply allows us to write promises based code as if it was synchronous and it checks that we are not breaking the execution thread. It operates asynchronously via the event-loop. `Async` functions will always return a value. It makes sure that a promise is returned and if it is not returned then javascript automatically wraps it in a promise which is resolved with its value.

>examples
```jsx

const getData = async () =>{
    let data = "Hello_World";
    return data;

}

getData().then(data => console.log(data));

//output
Hello_World
```

>**ii)Await:**

Await function is used to wait for the promise. It could be used within the async block only. It makes the code wait until the promise returns a result. It only makes the async block wait.

```jsx 
const getData = async () =>{
    let y = await 'Hello_World';

}
console.log(1);
getData();
console.log(2);

//output is 1
2
Hello_World
```

> **3. WeakSet**

In javascript, Set is a collection of unique and ordered elements.

Just like Set, WeakSet is also a collection of unique and ordered elements with some key differences:

- Weakset contains only objects and no other type.
- An object inside the weakset is referenced weakly. This means, if the object inside the weakset does not have a reference, it will be garbage collected.
- Unlike Set, WeakSet only has three methods, **add()** , **delete()** and **has()** .

```jsx
const newSet = new set([4, 5, 6, 7]);
console.log(newSet);
//output set {4,5,6,7}

const newSet2 = new weakSet([3, 4, 5]); //throws an error

let obj1 = {message: 'helloworld'};
const newSet3 = new weakSet([obj1]);
console.log(newSet3.has(obj1)); // True
```
>**4. Compose and Pipe**

>**i) Compose**

* In algebra, function composition ****allows you to apply one function to the output of another function.


* In this example, the function `g` is applied to the result of applying the function `f` to `x`. As we can see, function composition works from right to left.

* The same result can be achieved in JavaScript with `compose`:

**const compose = (g,f) => x => g(f(x));**

* Let’s suppose we want to get the name of a user and uppercase it. First of all, we have to write a function that extracts the name of the user:

```jsx
const user = {name: 'Surajsingh', password: 789456}
const getUserName = (user) => user.name
getUserName(user)
// 'Surajsingh'
```
* And then a function that uppercases strings:

```jsx
const upperCase = (string) => string.toUpperCase()
upperCase('SURAJSINGH')
// 'SURAJSINGH'
```

* Now we can compose the two functions to have just one function that executes both actions: Get the name and uppercase it.

* We can use the implementation of `compose()` that we saw before:

* The problem with this implementation of `compose()` is that it takes as parameters just two functions (in our example, `upperCase()`and `getUserName()`).

* Let’s suppose we want to add another function that returns the first four characters of a string:

```jsx
const firstFour = (string) => string.substring(0,4)
firstFour(‘SURAJSINGH’);
// 'SURA'
```
* How can we compose more than two functions at a time?

* We can use `Compose` and the `reduceRight()` method:

```jsx
const compose = (...functions) => x => functions.reduceRight((acc, fn) => fn(acc), x);
```
* In this implementation, `compose()` takes rest parameters (any number of parameters — in this example, any number of functions) and returns a function that takes the initial value `x`. It then uses the `reduceRight()`method to iterate from right to left over each function `fn` in `functions`and apply it, in turn, to the accumulated value `acc`.

* In simpler words, `compose()` applies right to left any number of functions to the output of the previous function.

* With this new implementation of `compose()`, we can now create a function that gets the name of the user, uppercases it, and returns just its first four characters:

```jsx
const compose = (...functions) => x => functions.reduceRight((acc, fn) => fn(acc), x);
const user = {name: 'Surajsingh', password: 789456}
const getUserName = (user) => user.name
const upperCase = (string) => string.toUpperCase()
const firstFour= (string) => string.substring(0,4)
compose (firstFour, upperCase, getUserName) (user);
// 'SURA'
```
* It’s like a list of commands that work from right to left (as in the math notation sense). The function getUserName() is the last argument when we call compose() because it is the first function that is to be executed.

>**ii)** **Pipe**

* `Pipe` is exactly like `compose()`, but it works left to right. I personally prefer it over `compose()` because you can think of it as a sequence of events.

* If we want to recreate our `compose()` function above but with `pipe()`, we can use this implementation:

```jsx
const pipe = (...functions) => x => functions.reduce((acc, fn) => fn(acc), x);
```

* As you noticed, we now use `reduce()` instead of  `reduceRight()`, as the function iterates left to right.

* Our final result will be:

```jsx
const pipe = (…functions) => x => functions.reduce((acc, fn) => fn(acc), x);
const user = {name: 'Surajsingh', password: 1234}
const getUserName = (user) => user.name
const upperCase = (string) => string.toUpperCase()
const firstFour= (string) => string.substring(0,4)
pipe (getUserName, upperCase, firstFour) (user);

```

* As a sequence of events, pipe() applies getUserName() to our initial data, then it applies upperCase() to the result of applying getUserName() to our initial data. Finally, it will applyfirstFour() to the output from applying upperCase() to the result of applying getUserName() to our initial data.

>**5. OOPS**




