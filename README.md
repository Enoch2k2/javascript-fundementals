# javascript-fundementals
## Comments
Multiline comment
```
/*
  Study Group Agenda:
  - Comments
  - Variables
  - Hoisting
  - Functions
  - scope
  - DataTypes
  - Conditionals
  - Loops
  - Arrays
  - Objects (if time)
*/
```

single line comments
```
// This is a one line Comments
// TODO: continue working on feature
// this is /* some comment */ and this is us continuing code
```

## Variables
Declaration Variable types:
```
// declaration variableName = value
var variableName = "someValue"
let variable2Name = "somevalue"
const variable3Name = "someValue"
```

Variable type meanings:
```
var = no restraints and gets hoisted. Never use
let = can be re-assigned but not re-declared. Does not get hoisted. Use in place of var.
const = can't be re-assigned and does not get hoisted. Use when you want the value to not change. If you set to an array, when you add to the array, it doesn't change the array from the previous array in memory so arrays are fine. It just means you can't change the array to an object.
```

Re-declaring variables using the variables defined above:
```
var variableName = "someOtherValue"; // works
let variable2Name = "someOtherValue"; // gives error
variable2Name = "someOtherValue"; // works
const variable3Name = "someOtherValue"; // gives error
variable3Name = "someOtherValue"; // gives error
```

What really happens when you hoist
```
console.log(greeting) // logs undefined
var greeting = "hello";
```
gets hoisted to:
```
var greeting; // gets declared at the top or hoisted

console.log(greeting); // logs undefined

greeting = "hello world!"
```

## Functions

Different Kinds of functions:
```
// standard hoisted function
 function greeting(name = "Javascript Programmer") {
   console.log(`Hello, ${name}`);
 }
// let declared function, not hoisted
 let greeting = function greeting2(name = "Javascript Programmer") {
   console.log(`Hello, ${name}`);
 }
 greeting();
// let declared arrow function, not hoisted
 let greeting = (name = "Javascript Programmer") => {
 console.log(`Hello, ${name}`);
}
```
Simplier Arrow function syntax with implicit returns, no {}:
```
// one parameter, fine to add parameter with no ()
let greeting = name => `Hello, ${name}!`;

// multiple parameters, need ()
let addTwoNums = (num1, num2) => num1 + num2;
```

Aliasing Functions
Since function definitions can be values in javascript, you can assign the function definition to a variable. You can also pass function definitions into other functions as parameters, this is called a callback function.
```
// aliasing
let greeting2 = greeting;
greeting2();
greeting("Bob");
```

example of callback function:
```
function doMath(callback, num1, num2) {
  return callback(num1, num2);
}

function addTwoNums(num1, num2) {
  return num1 + num2;
}

function subtractTwoNums(num1, num2) {
  return num1 - num2;
}

doMath(addTwoNums, 1, 3) // gives us 4
doMath(subtractTwoNums, 3, 1) // gives us 2
```

## Scope
Global Scope and the Local Scope:
```
let pet = "dog";

function whatKindOfPet() {
   // since we declared pet again inside function it becomes a local variable`
  let pet = "cat";
  console.log(pet);
}

whatKindOfPet(); // console logs cat;
console.log(pet); // since the global variable was ignored due to a local variable declared with the same name, dog gets console logged.
```
Re-Assigning Global Variables in the scope of a function:
```
let pet = "dog";

function whatKindOfPet() {
   // re-assigns the global pet variable
  pet = "cat";
  console.log(pet);
}

whatKindOfPet(); // console logs cat;
console.log(pet); // since the global variable was re-assigned and a local variable not declared, pet re-assigns to cat in the function and cat gets console logged.
```

## Datatypes
```
// truthy
"strings" - string
1234324 - integer
23423.2342 - float
true - boolean
[] - array
{ sayHello: () => "Hello!" } - object

// falsy
false - boolean
undefined - default internal version of no value or no declaration
null - no value same as nil in ruby
0 - 0 is falsy in javascript
```

## Conditionals
Example If Condition:
```
function SayHelloToGrandma(string) {
  // if(condition) { /* logic */ }
  if(string == "I LOVE YOU GRANDMA!") {
    return "I LOVE YOU TOO!"
  } else if(string.toUpperCase() == string) {
    return "NOT SINCE 1939!"
  } else {
  return "HUh? Speak up sonny!"
  }
}
```
Example of switch:
```
function SayHelloToGrandma(string) {
  switch(string) {
    case "I LOVE YOU GRANDMA!":
      return("I LOVE YOU TOO!");
      // use break if no return is given so rest of the lines that meet truthy don't get ran.
    case string.toUpperCase():
      return "NOT SINCE 1939!"
    default:
      return "HUh? Speak up sonny!"
  }
}
```

## Looping


For Loop:
To break down the for loop, it is divded into 3 steps, declaring a counter variable (here it's i), the condition as to when to stop iterating, so as long as i is less than the amount of elements in our array. Then we call i++ to increment i by 1.
```
let array = [1,2,3,4,5];

for(let i = 0; i < array.length; i++) {
  console.log(array[i] * 5);
}

// prints out 5, 10, 15, 20, 25
```

For In Loop:
we assign a variable (name) to represent each element inside the array
```
let array = [1,2,3,4,5];

for(let number in array) {
  console.log(number * 5);
}

// prints out 5, 10, 15, 20, 25
```

while loop:
Same as ruby, we give a condition as to when to break out of the loop
```
 let stoppingNumber = 15;
 let startingNumber = 0;
 while(startingNumber < stoppingNumber) {
  console.log(++startingNumber); // adding the ++ in front of a number will increment first before displaying the incremented number
 }
 
 // prints out 1 - 14
```

do while loop:
This loop will always run at least once:
```
do {
  console.log('I will only log once');
} while(false);
```

here's an example of it running multiple times:
```
let i = 0;
do {
  console.log(++i);
} while(i < 16);

// prints 1-15
```

## Arrays
The structure of arrays is the same as Ruby in many ways.

creating an array:
```
let array = []
```

However in javascript there are some key differences. One of the key differences is that you can non-destructively modify an array. Meaning that you get a new array that looks like the old array, but same change had occured. We'll go through the destructive modifiers first and then go to the non-destructive.

### Destructive Array Modifiers

adding to end of an array:
The shovel method doesn't exist in javascript, but same as ruby's push method.
```
let array = []

array.push("hello")

array // now equals ["hello"]

array.push("world")

array // now equals ["hello", "world"]
```

adding to beginning of array:
```
let array = [];

array.unshift("Hello");

array // array now equals ["Hello"]

array.unshift("World");

array // array now equals ["World", "Hello"]
```

Removing from end of an array:
```
let array = ["hello", "world"]
array.pop();
array // array now equals ["hello"]
```

Removing from front of an array:
```
let array = ["hello", "world"]
array.shift();
array // array now equals ["world"]
```

Non-Destructive Modifiers:

making a clone of the array:
```
 let array = ["hello", "world"]
 
 let newArray = [...array] // the ...array is our way of telling javascript to give us back an entirely new array, but keep all the elements inside the array variable
```

making a clone of the array and adding a new element in the front:
```
 let array = ["world"]
 
 let newArray = ["hello", ...array]
 array // array is still ["world"]
 newArray // newArray is ["hello", "world"]
```

When we break down the above process in steps, we are saying, lets create a new array `[]`. Lets insert "hello" into the array `["hello"]`. Now lets add all of the elements after the "hello" element `["hello", "world"]`.

So now knowing that, we can expect adding to the end of an array non-destructively being something super similiar:
```
let array = ["hello"];
let newArray = [...array, "world"];

array // stays ["hello"]
newArray // becomes ["hello", "world"] as the array elements was spread before we added the last element in the new array we created.
```

Non-destructively removing an element from the beginning of an array:
```
// we use slice(startNumber, upToButNotIncludingEndIndex);
let array = [0,1,2,3,4,5]

let newArray = array.slice(1, array.length) // returns [1,2,3,4,5] a new array, we add 1 because the 1 index is the second element and thats the element we want to start slicing our new array from. Then we add array.length, since we grab all the elements up to but not including this number index wise, we are able to get all of the remaining elements.

array is still [0,1,2,3,4,5]
newArray is [1,2,3,4,5]
```

And the same with removing from the end of an array:
```
let array = [0,1,2,3,4,5];

let newArray = array.slice(0, array.length - 1); // we start at the 0 index and say we want up to but not including the last index value of this array leaving out the element at the last index.

array is still [0,1,2,3,4,5]
newArray is [0,1,2,3,4]
```

## Array iterators (bonus)

Some of the array iterators commonly used:

forEach:
```
// forEach (works a lot like ruby's each, and takes in a callback function (which is a function definition we pass in as an argument for another function to call))
let array = ["hello", "bob", "javascript", "is", "a", "lot", "of", "fun"];

function printNames(name, index) {
  console.log(`${index + 1}. ${name}`);
}

array.forEach(printNames)

or we could define the function inside the () as well

array.forEach(function(name, indea) {
  console.log(`${index + 1} ${name}`);
})

either way works
```

map:
Same as ruby except we have to return in our callback function what we want to represent each element in our new array:
```
let array = [1,2,3,4,5];

array.map(function(number) {
  return number * 5;
});

This gives us back [5, 10, 15, 20, 25]
```

find an element:
Basically same as ruby except once again using the return keyword and a callback:
```
let array = ["bob", "sarah", "taco", "bell", "is", "amazing"]

instead of defining a standard function as we had been doing, lets do an array function with implicit return values as the callback!

array.find(name => name == "sarah") // woo much cleaner! Also, this returns "sarah" because sarah was found, otherwise it would give us null
```

find multiple elements:
In ruby we used select to find multiple elements (or find_all), in javascript we have a function that does the same thing called filter:
```
let array = [1,2,3,4,5,6]

array.filter(number => number % 2 == 0)
// so here we are filtering through the array and only selecting numbers that are even resulting in an array of [2,4,6]
```

find index of an element:
We also have a way to get the index position of a particular element:
```
let array = ["bob", "sarah", "taco", "bell", "is", "amazing"];

array.indexOf("bell") // gives us 3
```

## Objects
In javascript, we don't have hashes. Instead we have objects which look a lot like and act a lot like hashes. Here are some key differences:
```
similiar:
- Objects consist of key / values
- Objects are wrapped in {}
- you can access objects with object["key"]

difference:
- keys can be assigned to functions
- you can access objects with dot notation - object.key
- like with arrays, we have destructive and non-destructive functions to call to modify an object or get a new modified object
```

Pretty neat right? So lets take a closer look on how we create objects:
```
  let object = {}
```

Pretty familiar right? Lets describe a person in our object.
```
  object["firstName"] = "Bob"
  object.lastName = "Smith"
  
  let key = "age"
  let age = 27
  object[key] = age;
  // example of dynamically setting the key of an object, you can only do that with bracket notation and unable to do it with dot notation ( object.key = age; ). This would give us a key called key set to 27.
```

Great now we have Bob Smith who is 27 years old. Bob Smith has determined since he's been alive in our code for 5 seconds, that he's already an amazing developer. Let's add a function to Bob Smith's Object to explain what he likes to do!
```
object.favoriteHobby = function() {
  console.log("I love to program!");
}
```

What just happened here? Ruby tells us that if we add methods to our hashes that everything goes up in smoke! Well good thing this is javascript and not hashes. Just like ruby objects can have instance methods, javascript objects can have what we call prototype functions that these objects can call. Lets have our object known as Bob Smith tell us his favorite hobby!

```
object.favoriteHobby(); // logs to the console I love to program!
```

Now then, wouldn't it be nice if we could make multiple Bob Smiths? We you definitely can with Object Oriented classes, which we will get to soon! Coming soon to a cohort near you.
