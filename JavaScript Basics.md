# JavaScript Basics 🏆:


```javascript
document.querySelector("html").addEventListener("click", function () {
  alert("Ouch! Stop poking me!");
});
```


# JavaScript objects
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


# JavaScript strings:

Strings are a fundamental data type in JavaScript used to represent text. They are sequences of characters enclosed within single quotes (`'`) or double quotes (`"`). 
Strings are a versatile and essential part of JavaScript, used extensively in web development for tasks such as user input validation, dynamic content generation, and manipulation of text-based data. Understanding string manipulation techniques is crucial for writing efficient and readable JavaScript code.

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
   - `concat(str1, str2, ...)`: Concatenates two or more strings.
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

3. **String Manipulation Methods**:
   ```javascript
   let text = '  JavaScript is awesome!  ';

   // Trim whitespace
   console.log(text.trim()); // Output: JavaScript is awesome!

   // Replace
   console.log(text.replace('awesome', 'amazing')); // Output: JavaScript is amazing!

   // Split
   // takes a pattern and divides this string into an ordered list of substrings by searching for the pattern, puts these substrings into an array, and returns the array.
   let words = text.split(' '); 
   console.log(words); // Output: ['JavaScript', 'is', 'awesome!']

   const str = 'The quick brown fox jumps over the lazy dog.';
   const words = str.split(' ');
   console.log(words[3]);
   // Expected output: "fox"
   
   const chars = str.split('');
   console.log(chars[8]);
   // Expected output: "k"
   
   const strCopy = str.split();
   console.log(strCopy);
   // Expected output: Array ["The quick brown fox jumps over the lazy dog."]


   // join
   // join() method of Array instances creates and returns a new string by concatenating all of the elements in this array, separated by commas or a specified separator string.
   const elements = ['Fire', 'Air', 'Water'];
   console.log(elements.join());
   // Expected output: "Fire,Air,Water"
   
   console.log(elements.join(''));
   // Expected output: "FireAirWater"
   
   console.log(elements.join('-'));
   // Expected output: "Fire-Air-Water"




   
   ```

4. **Checking for Substrings**:
   ```javascript
   let sentence = 'JavaScript is a powerful programming language.';
   let keyword = 'JavaScript';

   // Check if the sentence contains the keyword
   console.log(sentence.includes(keyword)); // Output: true

   // Check if the sentence starts/ends with specific strings
   console.log(sentence.startsWith('Java')); // Output: true
   console.log(sentence.endsWith('language')); // Output: true
   ```

5. **Unicode Support**:
   ```javascript
   let emoji = '😊';
   console.log(emoji); // Output: 😊

   // Accessing Unicode code point
   console.log(emoji.codePointAt(0).toString(16)); // Output: 1f60a
   ```

6. **Multiline Strings** (using template literals):
   ```javascript
   let multilineString = `
   This is a multiline string.
   It spans across multiple lines.
   `;
   console.log(multilineString);
   ```

7. **Reversing a String**:
   ```javascript
   function reverseString(str) {
     return str.split('').reverse().join('');
   }

   let reversed = reverseString('hello');
   console.log(reversed); // Output: olleh
   ```

8. **Generating Random Strings**:
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



9. **Common way to convert non-string values into strings**

function splitIntoDigits(a) {
    const string = a + '';  // Convert to string (This method effectively converts the number a into a string)
    const strings = string.split(''); // Split into individual characters
    return strings.map(digit => Number(digit))    // Convert each character back to a number. The result is an array of numbers representing the digits of the original number a.
   // same as the previous line; Convert 'a' to string (For example, if a=123, String(a) will result the string '123')
   // Array.from: creates a new array from an array-like or iterable object. In this case, the array-like object is the string representation of a generated in the previous step.
   // Number: This is a callback function passed to Array.from which specifies how each element of the resulting array should be processed. Here, it's converting each character in the string back into a number. When Array.from iterates over       // each character in the string, it applies the Number function to convert it into a number. For example, '1', '2', and '3' will be converted to 1, 2, and 3 respectively.
    return Array.from(String(a), Number);   
}







# Javascript arrays:
```javascipt
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// Expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// Expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// Expected output: "array1:" Array ["three", "two", "one"]
```


---


# Regular_expressions -> Character classes in javascript:

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


# 🏆 Javascript Practice:

// https://www.jschallenger.com/javascript-practice/

```javascript
// There's another way to create functions which is called function expression.
// Here, we create a function and assign it to the variable logMessage.
// Notice that we omit the name of the function after the function keyword.
function logMessageOne() {
    console.log('How are you?');
  }
   
  const logMessageTwo = function() {
    console.log('Great, thanks!');
  }   
  logMessageOne();   
  logMessageTwo();




// Write a function that takes a string (a) and a number (n) as argument.
// Return the nth character of 'a'.
function myFunction(a, n){
    return a.charAt(n - 1);
}
console.log(myFunction('abcd',1));



// Write a function that takes a string (a) as argument.
// Remove the first 3 characters of a. Return the result
function myFunction(a){
    return a.slice(3);
}
console.log(myFunction('1234'));



// Write a function that takes a string as argument. Extract the last 3 characters from the string. Return the result
function myFunction(a) {
    return a.slice(-3);
}
console.log(myFunction('abcdefgh')); // Output: 'fgh'



// Write a function that takes a string (a) as argument. Get the first 3 characters of a. Return the result
function myFunction(a) {
    return a.slice(0, 3);
}
console.log(myFunction('abcdefgh')); // Output: 'abc'



// Write a function that takes a string as argument. The string contains the substring 'is'. Return the index of 'is'.
function findIndexOfIs(a) {
    return a.indexOf('is');
}
console.log(findIndexOfIs('This is a sample string.')); // Output: 2


// Write a function that extract the first half a. 
function extractFirstHalf(a) {
    const halfLength = Math.ceil(a.length / 2); //rounds a number up
    return a.slice(0, halfLength);
}

console.log(extractFirstHalf('abcdefgh')); // Output: 'abcd'



// Remove the last 3 characters of a. Return the result.
function removeLastThreeCharacters(a) {
    return a.slice(0, -3);
}
console.log(removeLastThreeCharacters('abcdefgh')); // Output: 'abc'



// Return b percent of a
function percentage(a, b) {
    return (b / 100) * a;
}
console.log(percentage(100, 50)); // Output: 50



// Sum a and b. Then substract by c. Then multiply by d and divide by e.
// Finally raise to the power of f and return the result.
function complexCalculation(a, b, c, d, e, f) {
    let result = a + b;
    result -= c;
    result *= d;
    result /= e;
    result = Math.pow(result, f);     // Raise to the power of f
    return result;

   // return (((a + b - c) * d) / e) ** f;
}
const a = 5, b = 10, c = 3, d = 2, e = 4, f = 2;
const result = complexCalculation(a, b, c, d, e, f);
console.log(result);




// If a contains b, append b to the beginning of a.
// If not, append it to the end.
function appendBasedOnContainment(a, b) {
    if (a.includes(b)) {
        return b + a;  // Append b to the beginning of a
    } else {
        return a + b;  // Append b to the end of a
    }
}
const x = 'hello', y = 'world';
const result2 = appendBasedOnContainment(x, y);
console.log(result);




//  If the number is even, return true. Otherwise, return false
function isEven(n) {
    return n % 2 === 0;
}
console.log(isEven(10));





// Return the number of times a occurs in b.
function countOccurrences(a, b) {
    // a regular expression with the 'g' flag is used to find all occurrences of a in b. 
    const regex = new RegExp(a, 'g');
    const matches = b.match(regex);

    // Return the count of occurrences
    return matches ? matches.length : 0;
}
const w = 'ab', z = 'abababcab';
const occurrences = countOccurrences(w,z);
console.log(occurrences);  // Output: 4

/*
Regular expressions:
1. Literal Characters:
   - Regular expressions can match literal characters. For example, `/hello/` will match the word "hello" in a text.

2. Metacharacters:
   - `.` (dot): Matches any single character. `/a.b/` will match "aab", "axb", etc.
   - `*`: Matches 0 or more occurrences of the preceding character. `/ab*c/` will match "ac", "abc", "abbc", etc.
   - `+`: Matches 1 or more occurrences of the preceding character. `/ab+c/` will match "abc", "abbc", "abbbc", etc.
   - `?`: Matches 0 or 1 occurrence of the preceding character. `/ab?c/` will match "ac" and "abc".
   - `^`: Anchors the regex at the beginning of the string. `/^abc/` will match "abc" only if it's at the beginning.
   - `$`: Anchors the regex at the end of the string. `/abc$/` will match "abc" only if it's at the end.

3. Character Classes:
   - Square brackets `[ ]` define a character class. `/[aeiou]/` will match any vowel.
   - Ranges can be used. `/[0-9]/` will match any digit.

4. Quantifiers:
   - Specify the number of occurrences. `/a{2,4}/` matches 2 to 4 consecutive 'a' characters.

5. Groups:
   - Parentheses `( )` create groups. `/(\d{3})-\d{3}-\d{4}/` matches a phone number pattern like "555-123-4567" and captures the area code (the digits within the parentheses).

6. Escape Character:
   - The backslash `\` is used to match a literal metacharacter. `/a\*b/` matches "a*b".


Now, let's revisit the examples with simpler explanations:
const text = 'The quick brown fox jumps over the lazy dog';

// Example 1: Matching the word 'quick'
const wordRegex = /quick/;
console.log(text.match(wordRegex));  // Output: [ 'quick' ]

// Example 2: Matching any digit
const digitRegex = /\d/;
console.log(text.match(digitRegex));  // Output: null (no digit found)

// Example 3: Matching words starting with 'b'
const startsWithBRegex = /\bb\w+/g;
console.log(text.match(startsWithBRegex));  // Output: [ 'brown' ]

// Example 4: Matching a phone number pattern and capturing the area code
const phoneRegex = /(\d{3})-\d{3}-\d{4}/;
const phoneNumber = '555-123-4567';
console.log(phoneNumber.match(phoneRegex));  // Output: [ '555-123-4567', '555' ]
*/




//If a is a whole number (has no decimal place), return true. Otherwise, return false.
function isWholeNumber(a) {
    return Number.isInteger(a);
    // return a - Math.floor(a) === 0
}
console.log(isWholeNumber(5));     // Output: true
console.log(isWholeNumber(7.42));  // Output: false




// Write a function that takes two numbers (a and b) as arguments.
// If a is smaller than b, divide a by b. Otherwise, multiply both numbers. Return the resulting value
function dividedOrMultiply(a,b){
   return a < b ? a/b : a*b;
}



//Round a to the 2nd digit after the decimal point. 
function roundToTwoDecimalPlaces(a) {
    return Math.round(a * 100) / 100;
}

//Split a into its individual digits and return them in an array.
function splitIntoDigits(a) {
    const string = a + '';  // Convert to string (This method effectively converts the number a into a string)
    const strings = string.split(''); // Split into individual characters
    return strings.map(digit => Number(digit))    // Convert each character back to a number
    // return Array.from(String(a), Number);
}
```
