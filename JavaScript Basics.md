# 🏆 ידע טכני:

  

# 🏆 String Methods
  ```javascript
   let text = '  JavaScript is awesome!  ';

   // Trim whitespace
   console.log(text.trim()); // Output: JavaScript is awesome!

   // Split -
   // split(separator)
   // split(separator, limit)
   // takes a pattern and divides this string into an ordered list of substrings by searching for the pattern,
 // puts these substrings into an array. Returns an array!
   let words = text.split(' '); 
   console.log(words); // Output: ['JavaScript', 'is', 'awesome!']

   const str = 'The quick brown fox jumps over the lazy dog.';
   const words = str.split(' ');
   console.log(words[3]);  // "fox"
   
   const chars = str.split('');
   console.log(chars[8]);  // "k"
   
   const strCopy = str.split();
   console.log(strCopy);   //Array ["The quick brown fox jumps over the lazy dog."]


   // Replace
   console.log(text.replace('awesome', 'amazing')); // Output: JavaScript is amazing!
 

  // substring -
  // substring(indexStart)
  // substring(indexStart, indexEnd)
  // return a new string
  const str = 'Mozilla';  
  console.log(str.substring(1, 3));   // "oz"
  
  console.log(str.substring(2));  // "zilla"



// padStart -
// Pads this string with another string until the resulting string reaches the given length.
// The padding is applied from the start of this string.
// padStart(targetLength)
// padStart(targetLength, padString)
const str1 = '5';

console.log(str1.padStart(2, '0'));  // "05"

const fullNumber = '2034399002125581';
const last4Digits = fullNumber.slice(-4);
const maskedNumber = last4Digits.padStart(fullNumber.length, '*');

console.log(maskedNumber);  // "************5581"
```






---
# 🏆 Arrays Methods
```javascript
// Creating an array -
const arr1 = new Array(element0, element1, /* …, */ elementN);
const arr2 = Array(element0, element1, /* …, */ elementN);
const arr3 = [element0, element1, /* …, */ elementN];

// To create an array with non-zero length, but without any items, either of the following can be used:
// This...
const arr1 = new Array(arrayLength);

// ...results in the same array as this
const arr2 = Array(arrayLength);

// This has exactly the same effect
const arr3 = [];
arr3.length = arrayLength;

// In addition to a newly defined variable as shown above, arrays can also be assigned as a property of a new or an existing object:
const obj = {};
// …
obj.prop = [element0, element1, /* …, */ elementN];

// OR
const obj = { prop: [element0, element1, /* …, */ elementN] };


// If you wish to initialize an array with a single element,
// and the element happens to be a Number, you must use the bracket syntax.
// When a single Number value is passed to the Array() constructor or function,
// it is interpreted as an arrayLength, not as a single element.
const arr = [42];       // creates an array with only one element: the number 42.
const arr = Array(42);  // This creates an array with no elements and arr.length set to 42.
// This is equivalent to:
const arr = [];
arr.length = 42;
```


```javascript
// toString -
const array1 = [1, 2, 'a', '1a'];
console.log(array1.toString());  // "1,2,a,1a"


// join -
// joins all elements of an array into a string. If array.length is 0, the empty string is returned.
// join()
// join(separator)
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());  // "Fire,Air,Water"
console.log(elements.join(''));  // "FireAirWater"
console.log(elements.join('-'));  // "Fire-Air-Water"


// push -
// Adds one or more elements to the end of an array and returns the resulting length of the array.
const myArray = ["1", "2"];
myArray.push("3"); // myArray is now ["1", "2", "3"]


// pop -
// Removes the last element from an array and returns that element.
const myArray = ["1", "2", "3"];
const last = myArray.pop();
// myArray is now ["1", "2"], last = "3"

// shift -
// Removes the first element from an array and returns that element.
const myArray = ["1", "2", "3"];
const first = myArray.shift();
// myArray is now ["2", "3"], first is "1"


// unshift -
// Adds one or more elements to the front of an array and returns the new length of the array.
const myArray = ["1", "2", "3"];
myArray.unshift("4", "5");
// myArray becomes ["4", "5", "1", "2", "3"]


// slice -
// slice() 
// slice(start)
// slice(start, end)
// extracts a section of an array and returns a new array.
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
console.log(animals.slice(2));       // Array ["camel", "duck", "elephant"]
console.log(animals.slice(2, 4));    // Array ["camel", "duck"] // starts at index 2 and extracts all elements until index 4
console.log(animals.slice(1, 5));    // Array ["bison", "camel", "duck", "elephant"]
console.log(animals.slice(-2));      // Array ["duck", "elephant"]
console.log(animals.slice(2, -1));   // Array ["camel", "duck"]
console.log(animals.slice());       // Array ["ant", "bison", "camel", "duck", "elephant"]

// at -
// Returns the element at the specified index in the array, or undefined if the index is out of range.
// It's notably used for negative indices that access elements from the end of the array.
const myArray = ["a", "b", "c", "d", "e"];
myArray.at(-2); // "d", the second-last element of myArray


// reverse -
// reverse()
const reversed = array1.reverse();
console.log('reversed:', reversed);  // "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);  // "array1:" Array ["three", "two", "one"]


// sort -
// sort()
// sort(compareFn)
// The default sort order is ascending
// ((a, b) => a - b) sorts numbers in ascending order.
// parameter 'compareFn' can be a function that determines the order of the elements. The function is called with the (a,b) arguments.
// It should return a number where:
// A negative value indicates that `a` should come before `b`.
// A positive value indicates that `a` should come after `b`.

const stringArray = ["Blue", "Humpback", "Beluga"];
const numberArray = [40, 1, 5, 200];
const numericStringArray = ["80", "9", "700"];
const mixedNumericArray = ["80", "9", "700", 40, 1, 5, 200];

function compareNumbers(a, b) {
  return a - b;
}

stringArray.join(); // 'Blue,Humpback,Beluga'
stringArray.sort(); // ['Beluga', 'Blue', 'Humpback']

numberArray.join(); // '40,1,5,200'
numberArray.sort(); // [1, 200, 40, 5]
numberArray.sort(compareNumbers); // [1, 5, 40, 200]

numericStringArray.join(); // '80,9,700'
numericStringArray.sort(); // ['700', '80', '9']
numericStringArray.sort(compareNumbers); // ['9', '80', '700']

mixedNumericArray.join(); // '80,9,700,40,1,5,200'
mixedNumericArray.sort(); // [1, 200, 40, 5, '700', '80', '9']
mixedNumericArray.sort(compareNumbers); // [1, 5, '9', 40, '80', 200, '700']



// map -
// map() -
// Returns a new array of the return value from executing callback on every array item.
// map(callbackFn)
// map(callbackFn, thisArg)

const array1 = [1, 4, 9, 16];
// Pass a function to map
const map1 = array1.map((x) => x * 2);
console.log(map1);  // Array [2, 8, 18, 32]



// reduce -
// reduce(callbackFn)
// reduce(callbackFn, initialValue)
// Return the value that results from running the "reducer" callback function to completion over the entire array.
// Executes a user-supplied "reducer" callback function on each element of the array.
// The final result of running the reducer across all elements of the array is a single value.

const array1 = [1, 2, 3, 4];
// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (accumulator, currentValue) => accumulator + currentValue,    // callbackFn
  initialValue,                                                 // initialValue
);
console.log(sumWithInitial);  // 10



// concat -
// concat()
// concat(value1)
// concat(value1, value2)
// concat(value1, value2, /* …, */ valueN) // this parameter represent Arrays and/or values to concatenate into a new array.
// joins two or more arrays and returns a new array.

  const str1 = 'Hello';
  const str2 = 'World';
  console.log(str1.concat(' ', str2)); // "Hello World"
  console.log(str2.concat(', ', str1)); // "World, Hello"

  // another concat example
  const greetList = ["Hello", " ", "Venkat", "!"];
  "".concat(...greetList); // "Hello Venkat!"

  // concat is called on an empty string "" -> This method is used to combine one or more strings together.  
  // The spread operator ... effectively spreads the elements of the greetList array as individual arguments to the concat() method.
  // So, effectively, `concat(...greetList)` is equivalent to `concat("Hello", " ", "Venkat", "!")`.
  // When concat() is called with these arguments, it combine them together into a single string.





// filter -
// filter(callbackFn)
// filter(callbackFn, thisArg)
//  returns a new array containing the items for which callback returned true.

const a1 = ["a", 10, "b", 20, "c", 30];
const a2 = a1.filter((item) => typeof item === "number");
console.log(a2); // [10, 20, 30]




// includes -
// includes(searchElement)
// includes(searchElement, fromIndex)
// The includes() method of Array instances determines whether an array includes a certain value among its entries,
// returning true or false.

const array1 = [1, 2, 3];

console.log(array1.includes(2)); // true
const pets = ['cat', 'dog', 'bat'];
console.log(pets.includes('cat')); // true
console.log(pets.includes('at')); // false


// every -
// every(callbackFn)
// every(callbackFn, thisArg)
// Tests whether all elements in the array pass the test implemented by the provided function.
// Returns Boolean.

const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];
console.log(array1.every(isBelowThreshold)); // true



// some -
// some(callbackFn)
// some(callbackFn, thisArg)
// Tests whether at least *one element* in the array passes the test implemented by the provided function.
// Returns Boolean. It doesn't modify the array.

const array = [1, 2, 3, 4, 5];
// Checks whether an element is even
const even = (element) => element % 2 === 0;
console.log(array.some(even)); // true



// indexOf -
// indexOf(searchElement)
// indexOf(searchElement, fromIndex)
// Returns the *first index* at which a given element can be found in the array, or -1 if it is not present.

const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison')); // 1
console.log(beasts.indexOf('bison', 2)); // Start from index 2    // 4
console.log(beasts.indexOf('giraffe')); // -1

#### Example:
// Removes duplicates by checking if the current index of an item is the same as the first
// occurrence of that item. If they match, it means the item is unique, and it's kept in the filtered array.
function removeDuplicates(arr) {
    return arr.filter((item, index) => arr.indexOf(item) === index);
}
`arr = [1, 2, 2, 3, 4, 4, 5]`.
1. For the first occurrence of `2`, `arr.indexOf(2)` returns `1`, and its current index (`index`) is also `1`. So, we keep `2`.
2. For the second occurrence of `2`, `arr.indexOf(2)` still returns `1`, but its current index (`index`) is `2`. So, we filter it out.
3. Similarly, for `4`, we keep only the first occurrence.


// lastIndexOf -
// works like indexOf, but starts at the end and searches backwards.
const a = ["a", "b", "c", "d", "a", "b"];
console.log(a.lastIndexOf("b")); // 5

// Now try again, starting from before the last match
console.log(a.lastIndexOf("b", 4)); // 1
console.log(a.lastIndexOf("z")); // -1


// forEach -
// Executes callback on every array item and returns undefined.
const a = ["a", "b", "c"];
a.forEach((element) => {
  console.log(element);
});
// Logs:
// a
// b
// c



// find -
// Returns the first item for which callback returned true.

const a1 = ["a", 10, "b", 20, "c", 30];
const i = a1.find((item) => typeof item === "number");
console.log(i); // 10


// findLast -
// Returns the last item for which callback returned true.

const a1 = ["a", 10, "b", 20, "c", 30];
const i = a1.findLast((item) => typeof item === "number");
console.log(i); // 30


// findIndex -
// Returns the index of the first item for which callback returned true.

const a1 = ["a", 10, "b", 20, "c", 30];
const i = a1.findIndex((item) => typeof item === "number");
console.log(i); // 1

// findLastIndex - returns the index of the last item for which callback returned true.



```






### Multi-dimensional arrays
```javascript
const a = new Array(4);
for (let i = 0; i < 4; i++) {
  a[i] = new Array(4);
  for (let j = 0; j < 4; j++) {
    a[i][j] = `[${i}, ${j}]`;
  }
}

/*
Row 0: [0, 0] [0, 1] [0, 2] [0, 3]
Row 1: [1, 0] [1, 1] [1, 2] [1, 3]
Row 2: [2, 0] [2, 1] [2, 2] [2, 3]
Row 3: [3, 0] [3, 1] [3, 2] [3, 3]
*/
```







---
<br>


# 🚀 Number in javascript:
```javascript
function financial(x) {
  return Number.parseFloat(x).toFixed(2);
}

console.log(financial(123.456));
// Expected output: "123.46"

console.log(financial(0.004));
// Expected output: "0.00"

console.log(financial('1.23e+5'));
// Expected output: "123000.00"
```


---
<br>





# 🚀 Map in javascript:
The Map object holds key-value pairs and remembers the original insertion order of the keys.
Any value (both objects and primitive values) may be used as either a key or a value.

```javascript
const map1 = new Map();

map1.set('a', 1);
map1.set('b', 2);
map1.set('c', 3);

console.log(map1.get('a'));
// Expected output: 1

map1.set('a', 97);

console.log(map1.get('a'));
// Expected output: 97

console.log(map1.size);
// Expected output: 3

map1.delete('b');

console.log(map1.size);
// Expected output: 2
```


#### Creating a new Map
```javascript
const myMap = new Map([
  [1, "one"],
  [2, "two"],
  [3, "three"],
]);
```

Methods include: clear, delete, entries, forEach, get, has, groupBy, keys, set, values.




---
<br>


# 🚀 Set in javascript:
The Set object lets you store unique values of any type, whether primitive values or object references.

```javascript
const a = new Set([1, 2, 3]);
const b = new Map([
  [1, "one"],
  [2, "two"],
  [4, "four"],
]);
console.log(a.union(b)); // Set(4) {1, 2, 3, 4}
```














---
<br>




# 🚀 Regular_expressions -> Character classes in javascript:

Character classes distinguish kinds of characters such as, for example, distinguishing between letters and digits.

```javascript
const chessStory = 'He played the King in a8 and she moved her Queen in c2.';
const regexpCoordinates = /\w\d/g;
console.log(chessStory.match(regexpCoordinates));
// Expected output: Array [ 'a8', 'c2']

const moods = 'happy 🙂, confused 😕, sad 😢';
const regexpEmoticons = /[\u{1F600}-\u{1F64F}]/gu;
console.log(moods.match(regexpEmoticons));
// Expected output: Array ['🙂', '😕', '😢']
```

```javascript
  for (let char of str) {
  //checks if it is an alphabet (either lowercase or uppercase) using a regular expression 
   char.match(/[a-zA-Z]/)  
}
```












---
<br>


# 🏆 JavaScript Basics:


```javascript
document.querySelector("html").addEventListener("click", function () {
  alert("Ouch! Stop poking me!");
});
```


## JavaScript Objects:
In JavaScript, objects are a fundamental data type that allow you to store collections of `key-value` pairs. Each key in an object must be unique, and each key is associated with a value. Objects in JavaScript can hold `any type of values, including numbers, strings, arrays, or even other objects`.

### Object Properties and Methods

Objects in JavaScript can have properties and methods:

- **Properties**: These are variables that are attached to the object. They hold data values.
  
  ```javascript
  const person = {
      firstName: "John",
      lastName: "Doe",
      age: 30
  };
  ```

- **Methods**: These are functions that are attached to the object. They can perform actions on the object's data.

  ```javascript
  const person = {
      firstName: "John",
      lastName: "Doe",
      fullName: function() {
          return this.firstName + " " + this.lastName;
      }
  };
  
  console.log(person.fullName());  // Outputs: "John Doe"
  ```

### Object Constructor

You can also create objects using a constructor function and the `new` keyword:

```javascript
function Person(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
}

const john = new Person("John", "Doe", 30);
```

### Object Prototypes

JavaScript is prototype-based. Each object has a prototype, and the prototype itself is also an object. You can add properties and methods to an object's prototype to be shared across all instances of the object.

```javascript
Person.prototype.fullName = function() {
    return this.firstName + " " + this.lastName;
};
```

### Object Destructuring

Destructuring assignment allows you to extract values from arrays or properties from objects and assign them to variables in a more concise way.
##### Object Destructuring:
In the context of objects, you can destructure properties from an object and assign them to variables with the same names as the properties.

Here we using destructuring assignment to extract specific properties from the person object and assign them to variables `firstName` and `lastName`.

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

const { firstName, lastName } = person;
console.log(firstName);  // Outputs: "John"
console.log(lastName);   // Outputs: "Doe"
```
The destructuring assignment here does the following:
- firstName: It extracts the value of `firstName` property from the `person` object and assigns it to a variable named `firstName`.
- lastName: It extracts the value of `lastName` property from the `person` object and assigns it to a variable named `lastName`.
- After executing you'll have two new variables. This is a convenient way to quickly access and use specific properties from an object without having to access them through the object's name every time.



###  Access the properties of an object without restructuring:

### `.`:

You can access object properties using the dot notation by directly referencing the property names after the object name:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

console.log(person.firstName);  // Outputs: "John"
console.log(person.lastName);   // Outputs: "Doe"
```

### `[]`:

Alternatively, you can use bracket notation by passing the property name `as a string` inside square brackets:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

console.log(person['firstName']);  // Outputs: "John"
console.log(person['lastName']);   // Outputs: "Doe"
```

### Using Variables for Property Names

If you want to access object properties using variables, you can use bracket notation:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

const propertyName = "firstName";
console.log(person[propertyName]);  // Outputs: "John"
```

### Direct Access with Variables

If you have the property values stored in variables, you can also access object properties directly using those variables:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

const firstName = "firstName";
const lastName = "lastName";

console.log(person[firstName]);  // Outputs: "John"
console.log(person[lastName]);   // Outputs: "Doe"
```


### Object Spread and Rest

The spread operator (`...`) can be used to create a new object by copying properties from an existing object:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

const newPerson = { ...person, age: 40 };
```

The rest operator (`...`) can also be used to gather remaining properties into a new object:

```javascript
const { firstName, ...rest } = person;
console.log(rest);  // Outputs: { lastName: "Doe", age: 30 }
```

### Object Serialization and Deserialization

JavaScript objects can be serialized into JSON strings and parsed back into objects:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

const jsonStr = JSON.stringify(person);  // Serialize object to JSON string
const obj = JSON.parse(jsonStr);         // Parse JSON string back to object
```

### `Object.keys()`, `Object.values()`, `Object.entries()`

These methods provide ways to access the keys, values, and entries of an object respectively:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

console.log(Object.keys(person));    // Outputs: ["firstName", "lastName", "age"]
console.log(Object.values(person));  // Outputs: ["John", "Doe", 30]
console.log(Object.entries(person)); // Outputs: [["firstName", "John"], ["lastName", "Doe"], ["age", 30]]
```





### Count Characters
```javascript
function countCharacters(str) {
    const charCount = {};
    
    for (let char of str) {
        charCount[char] = (charCount[char] || 0) + 1;
    }
    
    return charCount;
}
```
### `const charCount = {};`

The line `const charCount = {};` declares a constant variable named `charCount` and initializes it as an `empty object`. This empty object can later be populated with `key-value pairs`, where the `keys are characters` from the string and the `values are the counts` of those characters.

### `charCount[char] = (charCount[char] || 0) + 1;`
- `charCount[char]`: This accesses the value associated with the key `char` in the `charCount` object. If the key `char` does not exist in `charCount`, it returns `undefined`.

- `(charCount[char] || 0)`: This is a way to ensure that if `charCount[char]` is `undefined` (or falsy), it defaults to `0`. This prevents `NaN` (Not a Number) from being added to the count.

- `(charCount[char] || 0) + 1`: This increments the count of the character `char` by 1.

- `charCount[char] = (charCount[char] || 0) + 1;`: This assigns the incremented count back to the key `char` in the `charCount` object.

### Example:

Let's say we have the string `"hello"` and we want to count the occurrences of each character using the `countCharacters` function:

1. For the first character `'h'`:
   - `charCount['h']` is `undefined`, so `(charCount['h'] || 0)` evaluates to `0`.
   - `charCount['h'] = 0 + 1` assigns `1` to `charCount['h']`.

2. For the second character `'e'`:
   - `charCount['e']` is `undefined`, so `(charCount['e'] || 0)` evaluates to `0`.
   - `charCount['e'] = 0 + 1` assigns `1` to `charCount['e']`.

3. For the third character `'l'`:
   - `charCount['l']` is `undefined`, so `(charCount['l'] || 0)` evaluates to `0`.
   - `charCount['l'] = 0 + 1` assigns `1` to `charCount['l']`.

...and so on for each character in the string.

By the end, `charCount` will look something like this:
```javascript
{
  h: 1,
  e: 1,
  l: 2,
  o: 1
}
```




```javascript
const person = {};

const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio: function () {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf: function () {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};


const person = {
  name: ["Bob", "Smith"],
};


const person = {
  name: {
    first: "Bob",
    last: "Smith",
  },
  // …
};
```


# 🚀 JavaScript strings:

Strings are a fundamental data type in JavaScript used to represent text. They are sequences of characters enclosed within single quotes (`'`) or double quotes (`"`). 
Strings are a versatile and essential part of JavaScript, used extensively in web development for tasks such as user input validation, dynamic content generation, and manipulation of text-based data. Understanding string manipulation techniques is crucial for writing efficient and readable JavaScript code.


#### String constructor and String function - 
String function and String constructor produce different results:
```javascript
const a = new String("Hello world"); // a === "Hello world" is false
const b = String("Hello world"); // b === "Hello world" is true
a instanceof String; // is true
b instanceof String; // is false
typeof a; // "object"
typeof b; // "string"
```      


1. **String Declaration**: Strings can be declared using single quotes, double quotes, or backticks (template literals). 
   ```javascript
   let str1 = 'Hello, world!';
   let str2 = "This is a string.";
   let str3 = `JavaScript is awesome!`;
   ```

2. **String Length**: You can get the length of a string using the `length` property:
   ```javascript
   let str = 'Hello, world!';
   console.log(str.length); // Output: 13 (include , and space)
   ```

3. **String Methods**: JavaScript provides a variety of methods to manipulate strings. Some common methods include:
   - `toUpperCase()`: Converts the string to uppercase.
   - `toLowerCase()`: Converts the string to lowercase.
   - `charAt(index)`: Returns the character at the specified index.
   - `indexOf(substring)`: Returns the index of the first occurrence of the specified substring.
   - `substring(startIndex, endIndex)`: Returns a new string containing characters from `startIndex` to `endIndex` (excluding `endIndex`).
   - `slice(startIndex, endIndex)`: Similar to `substring()`, but allows negative indices.
   - `concat(str1, str2, ...)`: Concatenates (שרשור) two or more strings.
   - `split(separator)`: Splits the string into an array of substrings based on the specified separator.
   - `replace(oldValue, newValue)`: Replaces occurrences of `oldValue` with `newValue` in the string.
   - `trim()`: Removes whitespace from both ends of the string.

4. **String Interpolation**: Template literals (introduced in ES6) allow for easy string interpolation and multiline strings. They are enclosed within backticks and can contain placeholders `${}` for dynamic values:
   ```javascript
   let name = 'Alice';
   let greeting = `Hello, ${name}!`;
   console.log(greeting); // Output: Hello, Alice!
   ```

5. **String Immutability**: Strings in JavaScript are immutable, meaning their values cannot be changed after creation. However, you can create new strings based on existing ones using string methods or concatenation.

6. **Escape Characters**: JavaScript supports escape characters to represent special characters within strings. Some common escape characters include `\n` (newline), `\t` (tab), `\\` (backslash), `\"` (double quote), and `\'` (single quote).


7. 🎯 **Destructuring assignment**:
 ```javascript
// takes a string representing a time in the format 'HH:MM:SSAM', removes the AM/PM indicator, splits the remaining string into hours, minutes, and seconds, converts each part to a number, and assigns them to the respective variables hours, minutes, and seconds.
let s = '07:05:45PM';
let [hours, minutes, seconds] = s.slice(0, -2).split(':').map(Number);  
// Destructuring assignment allows you to extract data from arrays or objects and assign it to variables in a single expression
 ```     




## String usages and manipulations in JavaScript:

1. **Basic String Operations**:
   ```javascript
   // Declaration
   let str1 = 'Hello';
   let str2 = "world";
   let str3 = `!`;

   // Concatenation
   let greeting = str1 + ', ' + str2 + str3;
   console.log(greeting); // Output: Hello, world!

   // String Length
   console.log(greeting.length); // Output: 13

   // Accessing Characters
   console.log(greeting[0]); // Output: H
   console.log(greeting.charAt(7)); // Output: w

   // Substring
   console.log(greeting.substring(7, 12)); // Output: world

   // Uppercase and Lowercase
   console.log(greeting.toUpperCase()); // Output: HELLO, WORLD!
   console.log(greeting.toLowerCase()); // Output: hello, world!
   ```


2. **String Interpolation**:
   ```javascript
   let name = 'Alice';
   let age = 30;
   let message = `Hello, my name is ${name} and I am ${age} years old.`;
   console.log(message); // Output: Hello, my name is Alice and I am 30 years old.
   ```


  

5. **Checking for Substrings:**
   ```javascript
   let sentence = 'JavaScript is a powerful programming language.';
   let keyword = 'JavaScript';

   // Check if the sentence contains the keyword
   console.log(sentence.includes(keyword)); // Output: true

   // Check if the sentence starts/ends with specific strings
   console.log(sentence.startsWith('Java')); // Output: true
   console.log(sentence.endsWith('language')); // Output: true
   ```

6. **Unicode Support**:
   ```javascript
   let emoji = '😊';
   console.log(emoji); // Output: 😊

   // Accessing Unicode code point
   console.log(emoji.codePointAt(0).toString(16)); // Output: 1f60a
   ```

7. **Multiline Strings** (using template literals):
   ```javascript
   let multilineString = `
   This is a multiline string.
   It spans across multiple lines.
   `;
   console.log(multilineString);
   ```

8. **Reversing a String**:
   ```javascript
   function reverseString(str) {
     return str.split('').reverse().join('');
   }

   let reversed = reverseString('hello');
   console.log(reversed); // Output: olleh
   ```

9. **Generating Random Strings**:
   ```javascript
   function generateRandomString(length) {
     let result = '';
     const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
     for (let i = 0; i < length; i++) {
       result += characters.charAt(Math.floor(Math.random() * characters.length));
     }
     return result;
   }

   let randomString = generateRandomString(8);
   console.log(randomString);
   ```



10. **Common way to convert non-string values into strings**
```javascript
function splitIntoDigits(a) {
    const string = a + '';  // Convert to string (This method effectively converts the number a into a string)
    const strings = string.split(''); // Split into individual characters
    return strings.map(digit => Number(digit))    // Convert each character back to a number. The result is an array of numbers representing the digits of the original number a.
   // same as the previous line; Convert 'a' to string (For example, if a=123, String(a) will result the string '123')
   // Array.from: creates a new array from an array-like or iterable object. In this case, the array-like object is the string representation of a generated in the previous step.
   // Number: This is a callback function passed to Array.from which specifies how each element of the resulting array should be processed. Here, it's converting each character in the string back into a number. When Array.from iterates over       // each character in the string, it applies the Number function to convert it into a number. For example, '1', '2', and '3' will be converted to 1, 2, and 3 respectively.
    return Array.from(String(a), Number);   
}
```


 








---
<br>


1. **JavaScript Basics**:
   - סוגי נתונים ב-JavaScript: JavaScript מכיל מספר רב של סוגי נתונים, כולל מחרוזות, מספרים, בוליאניים, undefined, null, מערכים ואובייקטים.
     ```javascript
     let name = "John";
     let age = 30;
     let isStudent = true;
     let myArray = [1, 2, 3];
     let person = { name: "Alice", age: 25 };
     ```

2. **ES6+ Features**:
   - Arrow functions: דרך קצרה ונוחה להגדרת פונקציות.
     ```javascript
     const multiply = (a, b) => a * b;
     ```
   - Destructuring ו-Rest/Spread: קיצוץ ופישוט של משתנים במערכים ובאובייקטים.
     ```javascript
     const numbers = [1, 2, 3];
     const [first, ...rest] = numbers;
     console.log(first); // 1
     console.log(rest); // [2, 3]
     ```
   - Template literals ו-Tagged template literals: השתמשות בתבניות טקסט רבות שורות ותווי סוגריים אחוריים, ושימוש בתגי תבניות לעיבוד עיקרי לפני הצגת התוצאה.
     ```javascript
     const name = "Alice";
     const greeting = `Hello, ${name}!`;
     ```
   - Classes ו-Modules: הגדרת קלאסים ויבוא ויצוא של מודולים.
     ```javascript
     // Module.js
     export class MyClass {
       constructor(name) {
         this.name = name;
       }
     }

     // main.js
     import { MyClass } from './Module.js';
     const myObject = new MyClass('Alice');
     ```

3. **Asynchronous JavaScript**:
   - Callback functions: השתמשות בפונקציות הקוראות לאחר הסיום של פעולה אסינכרונית.
     ```javascript
     function fetchData(callback) {
       setTimeout(() => {
         callback("Data fetched!");
       }, 2000);
     }

     fetchData((data) => {
       console.log(data); // "Data fetched!"
     });
     ```
   - Promises והשימוש ב-Promise chaining: שימוש ב- Promises כדי לנהל קריאות כמו- async/await, עם ניהול שגיאות מובנה.
     ```javascript
     function fetchData() {
       return new Promise((resolve, reject) => {
         setTimeout(() => {
           resolve("Data fetched!");
         }, 2000);
       });
     }

     fetchData().then((data) => {
       console.log(data); // "Data fetched!"
     });
     ```
   - Async/Await: שימוש במילת המפתח async וawait ליצירת קוד כתוב בצורה סינכרונית נראית, בלי רכיבים בצד של ה- Promise.
     ```javascript
     async function fetchData() {
       const data = await fetch('https://api.example.com/data');
       const jsonData = await data.json();
       return jsonData;
     }
     ```

4. **DOM Manipulation**:
   - ניהול אירועים ב-HTML וב-JavaScript: הגדרת מטרות לאירועים כגון לחיצה, קליק, והשימוש ב-EventListener.
     ```javascript
     document.getElementById('myButton').addEventListener('click', () => {
       console.log('Button clicked!');
     });
     ```
   - CRUD ב-DOM: יצירה, קריאה, עדכון ומחיקה של רכיבי DOM.
     ```javascript
     const newElement = document.createElement('div');
     newElement.textContent = 'New Element';
     document.body.appendChild(newElement);
     ```
   - שימוש ב-DOM APIs כמו Fetch API לביצוע קריאות לשרת: השימוש ב-APIs מובנים בדפדפן לביצוע קריאות אסינכרוניות לשרת ולקבלת מידע.
     ```javascript
     fetch('https://api.example.com/data')
       .then(response => response.json())
       .then(data => console.log(data));
     ```




---
<br>


# שאלות פיתוח באקאנד - 

## API Design and Asynchronous Programming:

### API Design

#### Question 1: 
Design an API endpoint to create a new user with `name`, `email`, and `password` fields. Ensure that the email is unique and the password is hashed before saving to the database.

#### Solution:

```javascript
const bcrypt = require('bcrypt');
const users = [];  // Simulated database

app.post('/users', async (req, res) => {
    const { name, email, password } = req.body;

    // Check if email already exists
    if (users.some(user => user.email === email)) {
        return res.status(400).json({ error: 'Email already exists' });
    }

    // Hash password
    const hashedPassword = await bcrypt.hash(password, 10);

    // Create new user
    const newUser = {
        id: users.length + 1,
        name,
        email,
        password: hashedPassword,
        createdAt: new Date()
    };

    // Save user to database (in this example, we're just pushing to an array)
    users.push(newUser);

    res.status(201).json(newUser);
});
```

#### Question 2:
Design an API endpoint to update a user's `name` and `email` by `userId`.

#### Solution:

```javascript
app.put('/users/:userId', (req, res) => {
    const userId = parseInt(req.params.userId);
    const { name, email } = req.body;

    const userIndex = users.findIndex(user => user.id === userId);

    if (userIndex === -1) {
        return res.status(404).json({ error: 'User not found' });
    }

    // Update user details
    users[userIndex].name = name;
    users[userIndex].email = email;

    res.json(users[userIndex]);
});
```

### Asynchronous Programming

#### Question 1:
Write a function to fetch data from two different APIs (`api1` and `api2`) asynchronously and combine the results into a single object.

#### Solution:

```javascript
const axios = require('axios');

async function fetchDataFromApis() {
    try {
        const [data1, data2] = await Promise.all([
            axios.get('https://api1.example.com/data'),
            axios.get('https://api2.example.com/data')
        ]);

        return {
            api1Data: data1.data,
            api2Data: data2.data
        };
    } catch (error) {
        console.error('Error fetching data:', error);
        throw error;
    }
}
```

#### Question 2:
Write a function to fetch data from an API (`api1`) asynchronously. If the response contains a `nextPage` URL, fetch the next page recursively until all pages are fetched and combined into a single array.

#### Solution:

```javascript
const axios = require('axios');

async function fetchAllPages(url) {
    try {
        let allData = [];
        let nextPage = url;

        while (nextPage) {
            const response = await axios.get(nextPage);
            allData = [...allData, ...response.data.results];
            nextPage = response.data.nextPage;  // Assume nextPage is a URL or null
        }

        return allData;
    } catch (error) {
        console.error('Error fetching data:', error);
        throw error;
    }
}
```







More Backend-related questions:

### 1. API Design

**Question**: 
Design an API endpoint to retrieve a list of users with their details. Each user should have an `id`, `name`, `email`, and `createdAt` timestamp.

```javascript
// Express.js route to retrieve list of users
app.get('/users', (req, res) => {
    const users = [
        { id: 1, name: 'John', email: 'john@example.com', createdAt: new Date() },
        // ... other users
    ];
    res.json(users);
});
```

### 2. Database Query

**Question**: 
Write a SQL query to retrieve all orders placed by a specific user with the `userId` of 5 from an `orders` table.

```javascript
SELECT * FROM orders WHERE userId = 5;
```

### 3. Error Handling

**Question**: 
Implement error handling for a RESTful API endpoint that fetches user details by `userId`. Handle cases where the user doesn't exist or the database query fails.
```javascript
app.get('/user/:userId', (req, res) => {
    const userId = req.params.userId;
    const user = getUserById(userId);
    
    if (!user) {
        res.status(404).json({ error: 'User not found' });
        return;
    }
    
    res.json(user);
});
```

### 4. Authentication

**Question**: 
Implement JWT (JSON Web Token) authentication for an API endpoint. Create a function to generate a token when a user logs in and verify the token when accessing protected routes.

```javascript
const jwt = require('jsonwebtoken');

// Generate JWT token
function generateToken(user) {
    return jwt.sign({ userId: user.id }, 'secretKey', { expiresIn: '1h' });
}

// Verify JWT token
function verifyToken(token) {
    return jwt.verify(token, 'secretKey');
}
```

### 5. Data Validation

**Question**: 
Write a function to validate the format of an email address before saving it to the database. Ensure it follows the standard email format (`username@example.com`).

```javascript
function validateEmail(email) {
    const regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    return regex.test(email);
}
```

### 6. Caching

**Question**: 
Implement caching to improve the performance of an API endpoint that retrieves product details. Cache the results for 5 minutes and invalidate the cache when a product is updated.

```javascript
const NodeCache = require('node-cache');
const cache = new NodeCache({ stdTTL: 300 });

app.get('/products', async (req, res) => {
    let products = cache.get('products');
    
    if (!products) {
        products = await fetchProductsFromDatabase();
        cache.set('products', products);
    }
    
    res.json(products);
});
```

### 7. Rate Limiting

**Question**: 
Implement rate limiting for an API endpoint to allow only 100 requests per hour per user. Return an error message if the limit is exceeded.

```javascript
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
    windowMs: 60 * 60 * 1000, // 1 hour
    max: 100
});

app.use('/api/', limiter);

app.get('/api/data', (req, res) => {
    res.json({ message: 'Data fetched successfully' });
});
```

### 8. Asynchronous Programming

**Question**: 
Write a function to fetch data from an external API asynchronously using promises or async/await and handle any errors that may occur during the fetch operation.

```javascript
const axios = require('axios');

async function fetchData() {
    try {
        const response = await axios.get('https://api.example.com/data');
        return response.data;
    } catch (error) {
        console.error('Error fetching data:', error);
        throw error;
    }
}
```

### 9. Middleware

**Question**: 
Create a middleware function to log the request method, URL, and timestamp for every incoming request to an Express.js server.

```javascript
app.use((req, res, next) => {
    console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);
    next();
});
```

### 10. Data Transformation

**Question**: 
Write a function to transform the data retrieved from the database into a specific format required by the frontend. For example, convert date strings to JavaScript `Date` objects.

```javascript
function transformData(data) {
    return data.map(item => ({
        ...item,
        createdAt: new Date(item.createdAt)
    }));
}
```
