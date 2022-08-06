# JAVASCRIPT

```html
<script src="file.js"></script>
```


### strict mode
```javascript
"use strict"; //Modern JavaScript supports “classes” and “modules”  enable use strict automatically. 

//////////////////////////////////////////////////
//  nowadays there’s no reason to write such code

//immediately-invoked function expressions
(function() {
  var message = "Hello";
  alert(message); // Hello
})();

//that wrote fo local scope
(function() { alert("1"); })();
(function() { alert("2"); }());
!function() { alert("3"); }();
+function() { alert("4"); }();

```
### variables
```javascript
const COLOR_RED = "#F00";
let user = 'John', age = 25, message = 'Hello';
num = 5; // the variable "num" is created without USE STRICT
var message = 'Hello';//In older scripts, you may also find another keyword: var instead of let


//////////////////////////////////////////////

if (true) { var test = true; let test2= true; }
test; // true
test2; // test2 is not defined

function sayHi() { var phrase = "Hello"; }
phrase; // phrase is not defined 

//////////////////////////////////////////////

let user;
let user; // SyntaxError

var user = "Pete";
var user = "John";
user; // John

// Назначение в функции всегда д б выше вызова. Декларация м б ниже
function sayHi() {
  phrase = "Hello"; //assigments
  alert(phrase);
  var phrase; // declaration
}
sayHi();//hello

function sayHi() {
  alert(phrase);
  var phrase = "Hello";
}
sayHi();//undefined



```

### Data types
```javascript
let message = "hello";
message = 123456; // no error  cos dynamicaly typed

//There are 8 data types:

//null – a type with a single value null, meaning “empty” or “does not exist”,
//undefined – a type with a single value undefined, meaning “not assigned”,
//object and symbol – for complex data structures and unique identifiers, we haven’t learnt them yet.

// NUMBER
1. Infinity 
2. Nan
3. Regular number like 1 2 3 53.323. // not less or larger 9007199254740991
4. BigInt // larger regular , used rarely

( 1 / 0 ); // Infinity
( "not a number" / 2 ); // NaN, such division is erroneous
( "not a number" / 2 + 5 ); // NaN

const bigInt = 1234567890123456789012345678901234567890n // the "n" at the end means it's a BigInt


// STRING
let str = "Hello";
let str2 = 'Single quotes are ok too';

let name = "John";
alert( `Hello, ${name}!` );  //Backtiks quotes for embeded expr and var
alert( `the result is ${1 + 2}` ); // the result is 3


// BOOLEAN
let isGreater = 4 > 1;

// NULL - nothing

// UNDEFINED - is value is not assigned

// OBJECTS


typeof undefined // "undefined"
typeof 0 // "number"
typeof 10n // "bigint"
typeof true // "boolean"
typeof "foo" // "string"
typeof Symbol("id") // "symbol"
typeof Math // "object" 
typeof null // "object"  
typeof alert // "function"



let value = true;
value = String(value);
typeof value; // string

( "6" / "2" ); // 3, strings are converted to numbers

let str = "123";
let num = Number(str); // becomes a number 123

( Number(" 123 "));     // 123
( Number("123z") );     // NaN (error reading a number at "z")
( Number(true) );       // 1
( Number(false) );      // 0
( Number(null) );       // 0
( Number(indefined );   // NaN

( Boolean(1) ); // true
( Boolean(0) ); // false
( Boolean("hello") ); // true
( Boolean("") ); // false
( Boolean("0") ); // true
( Boolean(" ") ); // spaces, also true (any non-empty string is true)




```

### Операторы
```javascript
 
let x = 1; x = -x; // -1
 
( 8 % 3 ); // 2, a remainder of 8 divided by 3
( 2 ** 3 ); // 2³ = 8
( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)

let s = "my" + "string"; // mystring
( '1' + 2 ); // "12"
(2 + 2 + '1' ); // "41" and not "221"
('1' + 2 + 2); // "122" and not "14"
( 6 - '2' ); // 4, converts '2' to a number
( '6' / '2' ); // 3, converts both operands to numbers
 
// Converts non-numbers It actually does the same thing as Number(...), but is shorter.
( +true ); // 1
( +"" );   // 0
 
let apples = "2"; let oranges = "3";
( +apples + +oranges ); // 5
// ( Number(apples) + Number(oranges) ); // 5
 
let n = 2; n += 5; // now n = 7 (same as n = n + 5)
 
let n = 2; n *= 3 + 5; alert( n ); // 16  
 
let counter = 2;
counter++; // works the same as counter = counter + 1, but is shorter
( counter ); // 3
 
let counter = 1;
let a = ++counter; // (*)
(a); // 2
 
let counter = 1;
let a = counter++; // (*) changed ++counter to counter++
(a); // 1
 
let counter = 0;
counter++;
++counter;
( counter ); // 2, the lines above did the same
 
let counter = 0;
( ++counter ); // 1
 
let counter = 0;
( counter++ ); // 0
 
let counter = 1;
( 2 * ++counter ); // 4
 
let counter = 1;
( 2 * counter++ ); // 2, because counter++ returns the "old" value
 
//The comma operator allows us to evaluate several expressions, dividing them with a comma ,.
//Each of them is evaluated but only the result of the last one is returned.
let a = (1 + 2, 3 + 4);
alert( a ); // 7 (the result of 3 + 4)
 

( true || true );   // true
( false || true );  // true
( true || false );  // true
( false || false ); // false
( 1 || 0 ); // 1 (1 is truthy)
( null || 1 ); // 1 (1 is the first truthy value)
( null || 0 || 1 ); // 1 (the first truthy value)
( undefined || null || 0 ); // 0 (all falsy, returns the last value)
( true && true );   // true
( false && true );  // false
( true && false );  // false
( false && false ); // false
( 1 && 0 ); // 0
( 1 && 5 ); // 5
( null && 5 ); // null
( 0 && "no matter what" ); // 0
( 1 && 2 && null && 3 ); // null
( 1 && 2 && 3 ); // 3, the last one
( !true ); // false
( !0 ); // true
//A double NOT !! is sometimes used for converting a value to boolean type:
( !!"non-empty string" ); // true
( !!null ); // false



/*
result = a ?? b
equal
result = (a !== null && a !== undefined) ? a : b;
*/

let user; alert(user ?? "Anonymous"); // Anonymous (user not defined)
let user = "John"; alert(user ?? "Anonymous"); // John (user defined)

let firstName = null;
let lastName = null;
let nickName = "Supercoder";
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder
alert(firstName || lastName || nickName || "Anonymous"); // Supercoder
 
/*
|| returns the first truthy value.
?? returns the first defined value.
In other words, || doesn’t distinguish between false, 0, an empty string "" and null/undefined.
*/

let height = 0;
alert(height || 100); // 100
alert(height ?? 100); // 0

let x = 1 && 2 ?? 3; // Syntax error
let x = (1 && 2) ?? 3; // Works


```

### Comparisons

```javascript

( 2 == 1 ); // false (wrong)
( 2 != 1 ); // true (correct)
( 'Glow' > 'Glee' ); // true
( '2' > 1 ); // true, string '2' becomes a number 2

// When comparing values of different types, JavaScript converts the values to numbers.
( '01' == 1 ); // true, string '01' becomes a number 1
( true == 1 ); // true
( false == 0 ); // true
let b = " "; ( Boolean(b) ); // true
let b = "";  ( Boolean(b) ); // false 
let a = 0;   ( Boolean(a) ); // false
let b = "0"; ( Boolean(b) ); // true
(a == b); // true!
( 0 == false ); // true
( '' == false ); // true 
( 0 === false ); // false, because the types are different
( null === undefined ); // false
( null == undefined ); // true    they equal each other, but not any other value.

//< > <= >= null/undefined are converted to numbers:
//null becomes 0, while undefined becomes NaN.
//Comparisons convert null to a number, treating it as 0.
//That’s why null >= 0 is true and  null > 0 is false.
//== undefined and null equal each other and don’t equal anything else.
//That’s why null == 0 is false.

( null > 0 );  //  false
( null == 0 ); //  false
( null >= 0 ); //  true
( undefined > 0 );// false - undefined gets converted to NaN  
( undefined < 0 ); // false - undefined gets converted to NaN 
( undefined == 0 ); // false - undefined gets converted to NaN 



```

### Conditional branching: if, '?'

```javascript

let year = prompt(' year ?', '');

if (year < 2015) {
  alert( 'Too early...' );
} else if (year > 2015) {
  alert( 'Too late' );
} else {
  alert( 'Exactly!' );
}



let accessAllowed = (age > 18) ? true : false;



let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';

alert( message );


```


### Functions

```javascript

//Function Declaration- created as sepatate statement
//A Function Declaration can be called earlier than it is defined.
//in strict mode it s visible only inside blocks
function sayHi() {
  alert( "Hello" );
}

//Function Expression -  created inside another construction.
let sayHi = function() {
  alert( "Hello" );
};


function doNothing() { /* empty */ }
alert( doNothing() === undefined ); // true

function doNothing() { return; }
alert( doNothing() === undefined ); // true




//Calbacks

//The arguments showOk and showCancel of ask are called callback functions or just callbacks.

function ask(question, yes, no) {
  if (true) yes()
  else no();
}

function showOk() { }
function showCancel() { }
ask("Do you agree?", showOk, showCancel); //with func declaration
//or
ask( "yes", function() {  }, function() {  }); //with func expression ANONIMUS FUNC



//Arrow func

let sum = (a, b) => a + b; // let sum = function(a, b) {return a + b;}; 

let double = n => n * 2; //  let double = function(n) { return n * 2 }

let sayHi = () => alert("Hello!");




```

### Objects

```javascript
let user = new Object(); // "object constructor" 
let user = {};  // "object literal" 
var x="work";

let user = {    
  lastname,  // same as lastname:lastname
  name: "John", 
  age: 30       
  "likes birds": true 
  0: "test" // same as "0": "test"  (the number 0 is converted to string "0")
  ['periodOf' + x ]: 5 //  computed properties
};
user.isAdmin = true;
delete user.age;
( user["0"] ); // test
( user[0] ); // test (same property)
( user.noSuchProperty === undefined ); // true
user["likes birds"] = true;
(user["likes birds"]); // true
delete user["likes birds"];
( "age" in user ); // true



for (let key in user) {
  alert( key );  // name, age, isAdmin
  alert( user[key] ); // John, 30, true
}


let user = { name: 'John' };
let admin = user;
admin.name = 'Pete';
(user.name); // 'Pete'
(user==admin);// true

let clone = {}; 
for (let key in user) {
  clone[key] = user[key];
}

// copies all properties from permissions1 and permissions2 into user
Object.assign(user, permissions1, permissions2);

For nested objects cloning use _.cloneDeep from lodash


// these objects do the same
user = {
  sayHi: function() { }
};
user = {
  sayHi() { }
};



let user = { name: "John" };
let admin = { name: "Admin" };
function sayHi() {
  alert( this.name );
}
user.f = sayHi;
admin.f = sayHi;
user.f(); // John 
admin.f(); // Admin 



function User(name) {
  this.name = name;
  this.isAdmin = false;
}

let user = new User("Jack");




// create a function and immediately call it with new
let user = new function() {
  this.name = "John";
  this.isAdmin = false;
};

//This constructor can’t be called again, because it is not saved anywhere
//this trick aims to encapsulate the code that constructs the single object.



function User(name) {
  if (!new.target) { // if you run me without new
    return new User(name); // ...I will add new for you
  }
  this.name = name;
}
let john = User("John"); // 
alert(john.name); // John




function BigUser() {
  this.name = "John";
  return { name: "Godzilla" };  // <-- returns this object
}
alert( new BigUser().name );  // Godzilla, got that object




```

### optional chaining 

```javascript

// We can use ?. for safe reading and deleting, but not writing

let user = {}; // user has no address
alert( user?.address?.street ); // undefined (no error)


let userAdmin = {
  admin() {
    alert("I am admin");
  }
};
let userGuest = {};
userAdmin.admin?.(); // I am admin
userGuest.admin?.(); // nothing 


let key = "firstName";
let user1 = {
  firstName: "John"
};
let user2 = null;
alert( user1?.[key] ); // John
alert( user2?.[key] ); // undefined

let user = null;
user?.name = "John"; // Error, doesn't work
// because it evaluates to undefined = "John"

```

### symbol type

```javascript
let id = Symbol();
let id1 = Symbol("id");
let id2 = Symbol("id");

alert(id1 == id2); // false
alert(id1); // TypeError
alert(id1.toString());// Symbol(id1) 
alert(id1.description);// id 


let user = { // belongs to another code
  name: "John"
};
let id = Symbol("id");
user[id] = 1;
alert( user[id] );

/*
What’s the benefit of using Symbol("id") over a string "id"?

As user objects belongs to another code, and that code also works with them,
we shouldn’t just add any fields to it. That’s unsafe.
But a symbol cannot be accessed accidentally, the third-party code 
probably won’t even see it, so it’s probably all right to do.


*/
```

### objects to primitives

```javascript

let user = {
  name: "John",
  money: 1000,
  [Symbol.toPrimitive](hint) {
    alert(`hint: ${hint}`);
    return hint == "string" ? `{name: "${this.name}"}` : this.money;
  }
};
(user); // hint: string -> {name: "John"}
(+user); // hint: number -> 1000
(user + 500); // hint: default -> 1500




let user = {
  name: "John",
  money: 1000,
  // for hint="string"
  toString() {
    return `{name: "${this.name}"}`;
  },
  // for hint="number" or "default"
  valueOf() {
    return this.money;
  }

};
(user); // toString -> {name: "John"}
(+user); // valueOf -> 1000
(user + 500); // valueOf -> 1500
```





### types: Numbers

```javascript

//using the String/Number/Boolean without new is a useful thing. 
//They convert a value to the corresponding type:
//to a string, a number, or a boolean (primitive).
let num = Number("123"); // convert a string to number


//e multiplies the number by 1 with the given zeroes count.
let billion = 1000000000;
let billion = 1_000_000_000;
let billion = 1e9;
let ms = 0.000001;
let ms = 1e-6;


//Hexadecimal numbers
( 0xff ); // 255
( 0xFF ); // 255 
//Binary and octal numeral systems are rarely used
let a = 0b11111111; // binary form of 255
let b = 0o377; // octal form of 255
( a == b ); // true, the same number 255 at both sides


let num = 255;
( num.toString(16) );  // ff
( num.toString(2) );   // 11111111


Math.floor()// 3.1 becomes 3, and -1.1 becomes -2.
Math.ceil()//  3.1 becomes 4, and -1.1 becomes -1.
Math.round()// 3.1 becomes 3, 3.6 becomes 4, the middle case: 3.5 rounds up to 4 too.
Math.trunc()// 3.1 becomes 3, -1.1 becomes -1.


let num = 12.34;
( num.toFixed(5) ); // "12.34000"





( 0.1 + 0.2 ); // 0.30000000000000004
( 0.1.toFixed(20) ); // 0.10000000000000000555
let sum = 0.1 + 0.2;
( sum.toFixed(2) ); // String   0.30

let sum = 0.1 + 0.2;
( +sum.toFixed(2) ); //Number   0.3



( isNaN(NaN) ); // true
( isNaN("str") ); // true
( NaN === NaN ); // false


//isFinite(value) converts its argument to a number and returns true 
if it’s a regular number, not NaN/Infinity/-Infinity:

( isFinite("15") ); // true
( isFinite("str") ); // false, because a special value: NaN
( isFinite(Infinity) ); // false, because a special value: Infinity

//Please note that an empty or a space-only string is treated 
as 0 in all numeric functions including isFinite.


( +"100px" ); // NaN
( +"100" ); // 100
( parseInt('100px') ); // 100
( parseFloat('12.5em') ); // 12.5
( parseInt('12.3') ); // 12, only the integer part is returned
( parseFloat('12.3.4') ); // 12.3, the second point stops the reading
( parseInt('a123') ); // NaN, the first symbol stops the process
( parseInt('0xff', 16) ); // 255
( parseInt('ff', 16) ); // 255, without 0x also works
( parseInt('2n9c', 36) ); // 123456


( Math.random() ); // 0.123456789432
( Math.max(3, 5, -10, 0, 1) ); // 5
( Math.min(1, 2) ); // 1
( Math.pow(2, 10) ); // 2 in power 10 = 1024




```



### types: Strings

```javascript
let single = 'single-quoted';
let double = "double-quoted";
let backticks = `backticks`;

function sum(a, b) {
  return a + b;
}
(`1 + 2 = ${sum(1, 2)}.`); // 1 + 2 = 3.


let guestList = `Guests:
 * John
 * Pete
 * Mary
`;
(guestList); //  multiple lines

let str1 = "Hello\nWorld"; // two lines using a "newline symbol"
let str2 = `Hello
World`;
(str1 == str2); // true

( `My\n`.length ); // 3


let str = `Hello`;
( str[0] ); // H
( str.charAt(0) ); // H
( str[str.length - 1] ); // o

let str = `Hello`;
( str[1000] ); // undefined
( str.charAt(1000) ); // '' (an empty string)

for (let char of "Hello") {
  alert(char); // H,e,l,l,o 
}


let str = 'Hi';
str[0] = 'h'; // error
alert( str[0] ); // doesn't work


( 'Interface'.toUpperCase() ); // INTERFACE
( 'Interface'.toLowerCase() ); // interface


let str = 'Widget with id';
( str.indexOf('Widget') ); // 0, because 'Widget' is found at the beginning
( str.indexOf('widget') ); // -1, not found, the search is case-sensitive
( str.indexOf("id") ); // 1, "id" is found at the position 1 (..idget with id)

let str = 'Widget with id';
( str.indexOf('id', 2) ) // 12

( "Widget with id".includes("Widget") ); // true
( "Hello".includes("Bye") ); // false
( "Widget".includes("id", 3) ); // false, from position 3 there is no "id"
( "Widget".startsWith("Wid") ); // true, "Widget" starts with "Wid"
( "Widget".endsWith("get") ); // true, "Widget" ends with "get"


let str = "stringify";
( str.slice(0, 5) ); // 'strin'
( str.slice(0, 1) ); // 's'

let str = "stringify";
( str.slice(2) ); // 'ringify'

let str = "stringify";
( str.slice(-4, -1) ); // 'gif'

let str = "stringify";
( str.substring(2, 6) ); // "ring"
( str.substring(6, 2) ); // "ring"
alert( str.slice(2, 6) ); // "ring" (the same)
alert( str.slice(6, 2) ); // "" (an empty string)
//Negative arguments are (unlike slice) not supported, they are treated as 0.

let str = "stringify";
( str.substr(2, 4) ); // 'ring', from the 2nd position get 4 characters
//The first argument may be negative, to count from the end:


let str = "stringify";
( str.substr(-4, 2) ); // 'gi', from the 4th position get 2 characters
Let’s recap these methods to avoid any confusion:



```

### types: Arrays - ordered data type

```javascript


let arr = new Array();
let arr = [];

let fruits = ["Apple", "Orange", "Plum"];
( fruits[0] ); // Apple
( fruits.length ); // 3
alert( fruits ); // Apple,Orange,Plum


// mix of values
let arr = [ 'Apple', { name: 'John' }, true, function() { alert('hello'); } ];
( arr[1].name ); // John
arr[3](); // hello


let fruits = ["Apple", "Orange", "Pear"];

( fruits.pop() ); // remove "Pear" and alert it
( fruits ); // Apple, Orange

let fruits = ["Apple", "Orange"];
fruits.push("Pear");
( fruits ); // Apple, Orange, Pear

let fruits = ["Apple", "Orange", "Pear"];
( fruits.shift() ); // remove Apple and alert it
( fruits ); // Orange, Pear

let fruits = ["Orange", "Pear"];
fruits.unshift('Apple');
( fruits ); // Apple, Orange, Pear

let fruits = ["Apple"];
fruits.push("Orange", "Peach");
fruits.unshift("Pineapple", "Lemon");
( fruits ); // ["Pineapple", "Lemon", "Apple", "Orange", "Peach"]




let arr = ["Apple", "Orange", "Pear"];
for (let i = 0; i < arr.length; i++) {
  alert( arr[i] );
}

let fruits = ["Apple", "Orange", "Plum"];
for (let fruit of fruits) {
  alert( fruit );
}

let arr = ["Apple", "Orange", "Pear"];
for (let key in arr) {
  alert( arr[key] ); // Apple, Orange, Pear
}



let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

( matrix[1][1] ); // 5, the central element

let arr = [1, 2, 3];
( arr ); // 1,2,3
( String(arr) === '1,2,3' ); // true

( [] + 1 ); // "1"
( [1] + 1 ); // "11"
( [1,2] + 1 ); // "1,21"

( "" + 1 ); // "1"
( "1" + 1 ); // "11"
( "1,2" + 1 ); // "1,21"


( [] == [] ); // false
( [0] == [0] ); // false
( 0 == [] ); // true
('0' == [] ); // false
( 0 == '' ); // true, as '' becomes converted to number 0
('0' == '' ); // false, no type conversion, different strings


let arr = ["I", "go", "home"];
delete arr[1]; // remove "go"
( arr[1] ); // undefined
// now arr = ["I",  , "home"];
( arr.length ); // 3

let arr = ["I", "study", "JavaScript"];
arr.splice(1, 1); // from index 1 remove 1 element
( arr ); // ["I", "JavaScript"]

let arr = ["I", "study", "JavaScript", "right", "now"];
arr.splice(0, 3, "Let's", "dance");
( arr ) //  ["Let's", "dance", "right", "now"]

let arr = ["I", "study", "JavaScript", "right", "now"];
let removed = arr.splice(0, 2);
( removed ); // "I", "study" <-- array of removed elements

let arr = ["I", "study", "JavaScript"];
// from index 2 // delete 0 // then insert "complex" and "language"
arr.splice(2, 0, "complex", "language");
( arr ); // "I", "study", "complex", "language", "JavaScript"

let arr = [1, 2, 5];
arr.splice(-1, 0, 3, 4);
( arr ); // 1,2,3,4,5

let arr = ["t", "e", "s", "t"];
( arr.slice(1, 3) ); // e,s (copy from 1 to 3)
( arr.slice(-2) ); // s,t (copy from -2 till the end)

arr.slice()// creates a copy of arr.


let arr = [1, 2];
( arr.concat([3, 4]) ); // 1,2,3,4
( arr.concat([3, 4], [5, 6]) ); // 1,2,3,4,5,6
( arr.concat([3, 4], 5, 6) ); // 1,2,3,4,5,6

let arr = [1, 2];
let arrayLike = {
  0: "something",
  length: 1
};

( arr.concat(arrayLike) ); // 1,2,[object Object]
//But if an array-like object has a special
//Symbol.isConcatSpreadable property,
//`then it’s treated as an array by concat: its elements are added instead:
let arr = [1, 2];
let arrayLike = {
  0: "something",
  1: "else",
  [Symbol.isConcatSpreadable]: true,
  length: 2
};
( arr.concat(arrayLike) ); // 1,2,something,else


["Bilbo", "Gandalf", "Nazgul"].forEach((item, index, array) => {
(`${item} is at index ${index} in ${array}`);
});


let arr = [1, 0, false];
( arr.indexOf(0) ); // 1
( arr.indexOf(false) ); // 2
( arr.indexOf(null) ); // -1
( arr.includes(1) ); // true

const arr = [NaN];
alert( arr.indexOf(NaN) );
// -1 (should be 0, but === equality doesn't work for NaN)
alert( arr.includes(NaN) );// true (correct)



let result = arr.find(function(item, index, array) {
  // if true is returned, item is returned and iteration is stopped
  // for falsy scenario returns undefined
});
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

let user = users.find(item => item.id == 1);



let results = arr.filter(function(item, index, array) {
  // if true item is pushed to results and the iteration continues
  // returns empty array if nothing found
});
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

let someUsers = users.filter(item => item.id < 3);



let result = arr.map(function(item, index, array) {
  // returns the new value instead of item
});
let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
alert(lengths); // 5,7,6




let arr = [ 1, 2, 15 ];
arr.sort();
alert( arr );  // 1, 15, 2  // The items are sorted as strings by default.


function compare(a, b) {
  if (a > b) return 1; // if the first value is greater than the second
  if (a == b) return 0; // if values are equal
  if (a < b) return -1; // if the first value is less than the second
}
function compareNumeric(a, b) {
  if (a > b) return 1;
  if (a == b) return 0;
  if (a < b) return -1;
}
let arr = [ 1, 2, 15 ];
arr.sort(compareNumeric);
alert(arr);  // 1, 2, 15



arr.sort( (a, b) => a - b );


let countries = ['Österreich', 'Andorra', 'Vietnam'];
alert( countries.sort( (a, b) => a > b ? 1 : -1) );
// Andorra, Vietnam, Österreich (wrong)
alert( countries.sort( (a, b) => a.localeCompare(b) ) );
// Andorra,Österreich,Vietnam (correct!)


let arr = [1, 2, 3, 4, 5];
arr.reverse();
( arr ); // 5,4,3,2,1



let names = 'Bilbo, Gandalf, Nazgul';
let arr = names.split(', ');
for (let name of arr) {
  alert( `A message to ${name}.` ); 
}

let arr = 'Bilbo, Gandalf, Nazgul, Saruman'.split(', ', 2);
alert(arr); // Bilbo, Gandalf


let str = "test";
( str.split('') ); // t,e,s,t

let arr = ['Bilbo', 'Gandalf', 'Nazgul'];
let str = arr.join(';'); 
( str ); // Bilbo;Gandalf;Nazgul 


let value = arr.reduce(function(accumulator, item, index, array) {
  // ...
}, [initial]);
/*
accumulator – is the result of the previous function call, 
        equals initial the first time (if initial is provided).
item – is the current array item.
index – is its position.
array – is the array.
*/

let arr = [1, 2, 3, 4, 5];
let result = arr.reduce((sum, current) => sum + current, 0);
alert(result); // 15


let arr = [1, 2, 3, 4, 5];
let result = arr.reduce((sum, current) => sum + current);

alert( result ); // 15
//The result is the same. That’s because if there’s no initial,
//then reduce takes the first element of the array as the
//initial value and starts the iteration from the 2nd element.


let arr = [];
// Error: Reduce of empty array with no initial value
// if the initial value existed, reduce would return it for the empty arr.
arr.reduce((sum, current) => sum + current);

//The method arr.reduceRight does the same, but goes from right to left.


alert(typeof {}); // object
alert(typeof []); // same
alert(Array.isArray({})); // false
alert(Array.isArray([])); // true

arr.find(func, thisArg);
arr.filter(func, thisArg);
arr.map(func, thisArg);
// ...
// thisArg is the optional last argument
The value of thisArg parameter becomes this for func.


let army = {
  minAge: 18,
  maxAge: 27,
  canJoin(user) {
    return user.age >= this.minAge && user.age < this.maxAge;
  }
};

let users = [
  {age: 16},
  {age: 20},
  {age: 23},
  {age: 30}
];

let soldiers = users.filter(army.canJoin, army);

alert(soldiers.length); // 2
alert(soldiers[0].age); // 20
alert(soldiers[1].age); // 23
/*
If in the example above we used users.filter(army.canJoin),
then army.canJoin would be called as a standalone function,
with this=undefined, thus leading to an instant error.
A call to users.filter(army.canJoin, army) can be replaced with
users.filter(user => army.canJoin(user)), that does the same.
The latter is used more often, as it’s a bit easier
to understand for most people.
*/





```
