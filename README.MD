 Javascript Interview Questions.

Sum of array using Reduce 

const arr = [1,2,3,4,5];

const output = arr.reduce( (arr,curr) => {
    arr=arr+curr;
    return arr;
},0);

console.log(output);// 15

Find maximum number from array using Reduce:

const arr = [2,5,1,9,3];

const max = arr.reduce( (max, curr) => {
    if(curr > max){
        max = curr;
    }
        return max;
},0);

console.log(max); // 9

Input 
const users = [
	{fnm: 'Raj', lnm: 'shimpi', age: 29},
{fnm: 'Sayali', lnm: 'shimpi', age: 25},
{fnm: 'Sarthak', lnm: 'shimpi', age: 19},
{fnm: 'Shraddha', lnm: 'shimpi', age: 29},
]

Output : { 29: 2, 25: 1, 19: 1 }

const users = [
	{fnm: 'Raj', lnm: 'shimpi', age: 29},
    {fnm: 'Sayali', lnm: 'shimpi', age: 25},
    {fnm: 'Sarthak', lnm: 'shimpi', age: 19},
    {fnm: 'Shraddha', lnm: 'patel', age: 29},
]


let output = users.reduce((user, curr) => {
    console.log(user)
    console.log(curr)
    console.log('========');
    if(user[curr.age])
        user[curr.age]= ++user[curr.age];
    else
        user[curr.age] = 1;
    return user;
},{})

console.log(output); // { '19': 1, '25': 1, '29': 2 }

First log output:
{}
{ fnm: 'Raj', lnm: 'shimpi', age: 29 }
========
{ '29': 1 }
{ fnm: 'Sayali', lnm: 'shimpi', age: 25 }
========
{ '25': 1, '29': 1 }
{ fnm: 'Sarthak', lnm: 'shimpi', age: 19 }
========
{ '19': 1, '25': 1, '29': 1 }
{ fnm: 'Shraddha', lnm: 'patel', age: 29 }
========

Find the First Name whose age is more then 28.
Input 
const users = [
	{fnm: 'Raj', lnm: 'shimpi', age: 29},
{fnm: 'Sayali', lnm: 'shimpi', age: 25},
{fnm: 'Sarthak', lnm: 'shimpi', age: 19},
{fnm: 'Shraddha', lnm: 'shimpi', age: 29},
]

Output : [Raj, Shraddha]

const output = users.filter(user=> user.age  > 28 ).map(usernm => usernm.fnm);

console.log(output); // [ 'Raj', 'Shraddha' ]

To Reverse Array:
const orgArr = [1,3,5,7,9];
const revArr = []
for( const item of orgArr) {
	revArr.unshift(item);
}
console.log(revArr); // [ 9, 7, 5, 3, 1 ]

Sum of all numbers in array

const orgArr = [1,3,5,7,9];
const sumArr= 0;
for( const item of orgArr) {
	sumArr += item;
}
console.log(sumArr ); // 25

To remove duplicates from the array.
const orgArr = [1,3,1,2,3,7,5,7,9];
const orgArr = [1,3,1,2,3,7,5,7,9];
const uniqueArr = [];
for(item of orgArr){
    if(!uniqueArr.includes(item)){
        uniqueArr.push(item);
    }
}
console.log(uniqueArr) // [ 1, 3, 2, 7, 5, 9 ]

Find intersection of two arrays.
let arr1 = [1,2,3,4,5,6];
let arr2 = [1,3,5,7,9,2];
let common = [];
for(i=0; i<arr1.length; i++){
    if(arr2.includes(arr1[i])){
        common.push(arr1[i]);
    }
}
console.log(common) // [ 1, 2, 3, 5 ]


Rotate an array to the right side by a specific number of positions.
let rotateArr = [1,2,3,4,5,6];
let stepsToShift = 2;

function rotate(rotateArr, stepsToShift){
    for(var i=0; i<stepsToShift; i++){
            rotateArr.unshift(rotateArr.pop());
    }
        return rotateArr;
}

console.log(rotate(rotateArr, stepsToShift)) // [ 5, 6, 1, 2, 3, 4 ]


How to find the number of occurence of no/string.

Number : 
   const noArr = [1,1,8,3,3,2,5,3,6,1,8];
   const map = {};
   noArr.forEach(i=>map[i] ? map[i]= map[i]+1 : map[i]=1);
   console.log(map); //  { '1': 3, '2': 1, '3': 3, '5': 1, '6': 1, '8': 2 }

String : 
const strArr = 'Hello world';
const map1 = {};
const splitStrArr = strArr.toLowerCase().split("");
splitStrArr.forEach(i=> map1[i] ? map1[i] = map1[i]+1 : map1[i]=1);
console.log(map1);  // { h: 1, e: 1, l: 3, o: 2, ' ': 1, w: 1, r: 1, d: 1 }

//toLowerCase() / toUpperCase() / if you want to check capital and small then simply strArr.split().


11. Write the code for success and failure promise.

Success Promise Case :

const successPromiseObj = new Promise ((resolve, reject) => {
	let req = true;
	if(req == true) 
	{
		resolve("Request Success");
    }
    else{
    	reject("Request Fail");
    }
});
successPromiseObj.then((value)=> {
	console.log(value);					//  Request Success
},(error)=>{
	console.log(error);
});
successPromiseObj.catch((e) => console.log(e));


Fail Promise Case :

const rejectPromiseObj = new Promise((resolve, reject) => {
	reject("Fail");
})
.then(e => console.log("success"))
.catch((e)=>console.log(e)); 			// Fail


12. Currying Function.
First parameter remains the same but the rest changes every time.



const sum = a => b => a+b;
const ans = sum(5)(6);
console.log(ans); // 11

     B.
const priceCal = (price) => {
    return (dPer) => {
        return price * dPer;
    }
}
const disAmt = priceCal(300);
console.log(disAmt(0.3));   // 90
console.log(disAmt(0.4));   // 120
console.log(disAmt(0.5));   // 150

13. Fibonacci series:
function fibonacci(num){
    let num1 = 0;
    let num2 = 1;
    let sum;
    let i = 0;
    let arr = [];
    arr.push(num1);
    arr.push(num2);
    for(i=2; i<num; i++){
        sum = num1 + num2;
        num1 = num2;
        num2 = sum;
        arr.push(num2);
    }
    return arr;
}

console.log(fibonacci(6));  // [ 0, 1, 1, 2, 3, 5 ]

14. JS  Hacks:
a. 
function show(){
    console.log(nameP); // undefined
    var nameP;
    
    console.log(data); / /undefined
    var data = "a";
    
    console.log(age); // ERROR! ReferenceError: Cannot access 'age' before initialization
    let age;
    
    console.log(info); // ERROR! ReferenceError: Cannot access 'info' before initialization
    let info = "raj";m
}

show();

b. 
var i;
for (i=0; i<3; i++){
    setTimeout(()=> console.log(i)); // 3, 3, 3
}

for (let i=0; i<3; i++){
    setTimeout(()=> console.log(i)); // 0, 1, 2
}

c.  
const income= {
    skills : 108,
    monthly(){
        return this.skills * 2;
    }
    //yearly : () = 10 * this.skills;
};

console.log(income.monthly());  // 216
// console.log(income.yearly()); // SyntaxError: Unexpected identifier 'yearly' , it was giving error on commented line above also.

d. 
console.log(+true); // 1
console.log(true); // true
console.log(+false); // 0
console.log(false); // false

e.  
let a = {
    greeting: 'Hi'
}

let z = a;
z.greeting = 'Hello Dear';

console.log(a.greeting); // Hello Dear

f. 
let a = 108;
let b = new Number(108);
let c = new Number(108);
let d = 108;

console.log(a==b);  // true
console.log(a===b); // false

console.log(b==c); // false
console.log(b===c);// false

console.log(a==d); // true
console.log(a===d); // true

g.
function Human( fname, lname ){
    this.firstName = fname;
    this.lastName = lname;
}

const mrs = new Human("Rajashree", "Shimpi");
console.log(mrs); // Human { firstName: 'Rajashree', lastName: 'Shimpi' }

const rock = Human("deo", "Manjrekar");
console.log(rock); // undefined

h.
function checkAge(data){
    if(data === {age: 18}){
        console.log("You are eligible");
    }
     else if(data == {age: 18}){
        console.log("You are eligible");
    }
    else {
        console.log("No Age");
    }
}

checkAge({age: 18}) // No Age

i. 
const obj = {1: "a", 2: "b", 3: "c"};
const set = new Set([1,2,3,4,5]);

console.log(obj.hasOwnProperty("1")); // true
console.log(obj.hasOwnProperty(1));   // true

console.log(set.has("1"));          // false
console.log(set.has(1));            // true

j.
const obj = {
    a: "1",
    b: "2",
    a: "3"
}

console.log(obj); // { a: '3', b: '2' }

k.
var num = 10;
var num = 12;
console.log(num); // 12

let num1 = 10;
let num1 = 12; // error at this line for num1
console.log(num1); //SyntaxError: Identifier 'num' has already been declared

15. Increment and Decrement:
let salary = 10;
console.log('salary : 10');			// salary: 10
console.log("*----------------*");		// *----------------*
console.log('salary++: ', salary++);	// 10
console.log('salary: ', salary);		// 11
console.log('++salary: ', ++salary);	// 12
console.log('salary: ', salary);		//  12
console.log("*----------------*");		//  *----------------*
console.log('salary--: ', salary--);		// 12
console.log('salary: ', salary);		// 11
console.log('--salary: ', --salary);		// 10
console.log('salary: ', salary);		// 10
console.log("*----------------*");		// *----------------*


16. Call, Apply and Bind Methods.

Syntax : functionName.call(thisArg, arg1, arg2 ... argn);

function hello(b,c){
    console.log(this,b,c);
}
obj={
    a:5
}
hello.call(obj,3,4); // { a: 5 } 3 4
The first argument is always passed.
I want to get the value of obj inside the hello function, within the scope of this.
For this reason, we use call, bind, and apply.
Say hello.call (object) = This code passes a reference object to the hello method, which may then be called.

hello.apply(obj,[3,4]); // { a: 5 } 3 4
The call function is similar to the apply function, with the exception of passing thisArg directly and the rest of the arguments as an array.
apply only accepts two arguments: this and an array of elements to pass.

// hello.bind(obj,5,6);
const fs = hello.bind(obj,5,6);
fs();    // { a: 5 } 5 6
In terms of signature, bind and call are pretty similar.
However, binding returns a function.
Call changes the reference while giving arguments, whereas // Bind changes the reference but does not execute the function immediately, resulting in no output for the commented line.(// hello.bind(obj,5,6);)
Because it is a returning function, we are passing it to a variable and then calling it to get the output.
17. What is the difference between rest and spread operator ? 
From ES6 onwards there are (...) used in many places.
Sometimes they are called the Rest operator and sometimes the very same (...)
Are called Spread operator.

Rest operator : 
function sum(...nums){
    console.log(nums);
}

sum(2,3,4);     // [ 2, 3, 4 ]
sum(1,2);       // [ 1, 2 ]

function sum1(...nums, a){
    console.log(nums, a);
}

sum1(1,2,5);       // SyntaxError: Rest parameter must be last formal parameter
Meaning ...nums should come last in sequence bcz its rest parameter 

function sum2(a,...nums){
    console.log(a, nums);
}

sum2(1,2,5);       // 1 [ 2, 5 ]

function sum(){
    console.log(arguments);
}
sum(2,3,4,5) // [Arguments] { '0': 2, '1': 3, '2': 4, '3': 5 }
Above arguments code we can not run using the arrow function.
const sum1 = () => {
     console.log(arguments);
}
 sum1(2,3,4,5) // we will get error
// ----------------------------------
const sum2 = (...nums) => {
    console.log(nums);
}

sum2(2,3,4,5) // [ 2, 3, 4, 5 ]
Using rest we are able to use the arrow function as in the above example. So whenever we use (...) with a function to deal with any number of parameters, then we call it Rest operator, i.e. for the rest of parameters.

Spread Operator : 
As the rest operator puts the separate data values in one array, the Spread does exactly the opposite. to expand an iterable, such as an array or string, into individual elements.
let arr1 = [1,2,3,4];
let arr2 = [...arr1, 6, 7, 8];
let arr3 = [9,10, ...arr1, 7];
console.log(arr1); // [ 1, 2, 3, 4 ]
console.log(arr2); // [ 1, 2, 3, s4, 6, 7, 8 ]
console.log(arr3); // [ 9, 10, 1, 2, 3, 4, 7 ]

18. How does a closure work in JS ? 
 When a function comes under another function a “closure” is created.
Closure pattern remembers outer variable & also helps to access outer scope members.
Closure helps remember  outer variable and also helps to access outer scope members.
function outer(){
    return function (){
        console.log("Inner function called");
    }
}
const closure = outer();
closure(); // Inner function called
Inner function called outside of function , that’s possible because of Closure.
We will get same  output with arrow function as well as below,
const outer = () => {
    return () => {
        console.log("Inner function called");
    }
}

const closure = outer();
closure(); // Inner function called

Example Counter : 
const addCounter = () => {
    let counter = 0;
    return () => {
        counter++;
        console.log(counter);
    }
} 
const cl = addCounter();
cl();   // 1
cl();   // 2
cl();   // 3

The main advantage of “closure” is that any member which is private for certain scope,
Can be accessed keeping it private so that the variable is away from any accidental change of value.

19. Memory management and garbage collection ?
When we declare a variable, object, array or function all are stored somewhere in the memory.
Suppose we have below object created : 
let obj {
	a : 10;
}
When the program ends the data inside the location is garbage which needs to be cleared.
Similarly we have to think about function and variables as well. Once the program ends all this needs to be cleared.
This process of Garbaging is called as Garbage collector. JS does Garbage collection automatically.
The Garbage collection considers references & it tries to release the memory if a location is not “reachable”.
E.g. let obj = { name : ‘Sonu’ };
let obj = null;
Now , “name will not have any reference.” (This will automatically collected by GC).

There is an algo that is “Mark and sweep” :  The algo starts from the root object and checks for the references linked. If we find any unreachable location then those are locations to be removed. It starts from top and marks the unreachable location once done everything then it removes marked location. This is supportable by modern browsers. 
There was some problem with older browser of memory leaks (Circular ref) but bcz of this algo now its handling this situations as well.
Circular ref example : 
let teacher = new Teacher();
let stud = new Stud();
teacher.stud = stud;
stud = null
stud.teacher= teacher;

20. Exception handling in JS .

try {
  const result = parseInt('not a number');
  if (isNaN(result)) {
    throw new Error('Invalid input');
  }
} catch (error) {
  console.error(error.message);
}

In this example, the parseInt() function will throw an exception because the input is not a valid number. We catch the exception and throw a new Error with a custom message. The catch block then logs the error message to the console.

try {
 // code that may throw an exception
} catch (error) {
 // code to handle the exception
}

20. Exception handling in JS .

