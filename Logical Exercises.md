# 🏆 Logical Exercises (`Leetcode`) -


```javascript   
/*
Input an array full of numbers and zeros,
the array must be sorted so that the numbers are at the beginning and the zeros after
without sorting within the numbers.
*/

// takes an array as input, filters out the numbers and zeros into separate arrays,
// and then concatenates them back together with the numbers appearing first. 
function sortByNumbers(arr) {
    // Helper function to check if a value is a number
    function isNumber(value) {
        return typeof value === 'number' && !isNaN(value);
    }

    // Partition the array into two parts: numbers and zeros
    let numbers = arr.filter(isNumber);
    let zeros = arr.filter(item => !isNumber(item));

    // Concatenate the numbers array with the zeros array
    return numbers.concat(zeros);
}
// Example usage:
const inputArray = [4, 0, 1, 0, 3, 0, 5, 2, 0];
const sortedArray = sortByNumbers(inputArray);
console.log(sortedArray); // Output: [4, 1, 3, 5, 2, 0, 0, 0, 0]
```




```javascript   
/* 704. Binary Search
Given an array of integers nums which is sorted in ascending order,
and an integer target, write a function to search target in nums.
If target exists, then return its index. Otherwise, return -1.
You must write an algorithm with O(log n) runtime complexity. */

var search = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);   // rounds down 
        
        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;
};
```




```javascript
/* Longest binary gap in integer `N` -
A binary gap within a positive integer N is any maximal sequence of consecutive zeros
that is surrounded by ones at both ends in the binary representation of N.
Consider using a flag to indicate when you're inside a potential gap and when you're not.
This can help you keep track of the length of each gap. */

function longestBinaryGap(N) {
    // Step 1: Convert to Binary
    const binaryRep = N.toString(2); // Convert the integer N to its binary representation
    
    // Step 2-3: Identify Gaps and Find Longest Gap
    let maxGapLength = 0; // Variable to store the length of the longest gap
    let currentGapLength = 0; // Variable to track the length of the current gap
    let inGap = false; // Flag to indicate whether currently inside a gap
    
    // Iterate through each bit in the binary representation
    for (let bit of binaryRep) {
        if (bit === '1') { // If the current bit is '1'
            if (inGap) { // If already inside a gap
                // Update maxGapLength with the maximum of currentGapLength and maxGapLength
                maxGapLength = Math.max(maxGapLength, currentGapLength);
                currentGapLength = 0; // Reset currentGapLength
            }
            inGap = true; // Set inGap flag to true since encountered a '1'
        } else if (bit === '0' && inGap) { // If the current bit is '0' and already inside a gap
            currentGapLength++; // Increment the length of the current gap
        }
    }    
    // Step 4: Return Result
    return maxGapLength; // Return the length of the longest binary gap
}
// Example usage:
const N = 1041;
console.log(longestBinaryGap(N)); // Output: 5
```




```javascript
/* 21. Merge Two Sorted Lists -
You are given the heads of two sorted linked lists list1 and list2.
Merge the two lists into one sorted list.
The list should be made by splicing together the nodes of the first two lists.
Return the head of the merged linked list.
input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
*/
function mergeTwoLists(list1, list2) {
    // Initialize dummy node, head of the merged list.
    let dummy = new ListNode();
    let current = dummy;
    
    // Pointers for list1 and list2, to iterate through list1 and list2, respectively.
    let ptr1 = list1;
    let ptr2 = list2;
    
    // Cross both lists simultaneously:
    // Compare the values of ptr1 and ptr2.
    // Append the node with the smaller value to the merged list.
    // Move the respective pointer (ptr1 or ptr2) to the next node.

    // Merge lists
    while (ptr1 !== null && ptr2 !== null) {
        if (ptr1.val < ptr2.val) {
            current.next = ptr1;
            ptr1 = ptr1.next;
        } else {
            current.next = ptr2;
            ptr2 = ptr2.next;
        }
        current = current.next;
    }
    
    // Append remaining nodes
    if (ptr1 !== null) {
        current.next = ptr1;
    }
    if (ptr2 !== null) {
        current.next = ptr2;
    }
    
    // Return head of merged list
    return dummy.next;
}
//Recursive Approach
var mergeTwoLists = function(l1, l2) {
    if (!l1) return l2;
    if (!l2) return l1;
    if (l1.val < l2.val) {
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else {
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
};
```



```javascript
// 206. Reverse Linked List -
/* Given the head of a singly linked list, reverse the list, and return the reversed list.

Recursive approach -
Base Case: empty or one node - return head.
Recursive Case: reverse the rest of the list and set the next node's next pointer to the current node
(essentially reversing the direction of the pointer).
Once the end of the list is reached, it starts reversing the links by setting the next node's next pointer
to the current node.
Set head's next to null to mark the end of the reversed list.
*/
var reverseList = function(head) {
    // Base case: if head is null or there's only one node
    if (head == null || head.next == null) return head;
    // Create a new node to call the function recursively, effectively cross to the end of the list,
    // and get the reverse linked list
    // Once the end of the list is reached,
    // it starts reversing the links by setting the next node's next pointer to the current node
    // (essentially reversing the direction of the pointer).
    var res = reverseList(head.next);
    // Reverse the link between head and head.next
    head.next.next = head;
    // Set head's next to null to mark the end of the reversed list
    head.next = null;
    return res;         // Return the new head of the reversed list
};

// ES6 Destructuring
var reverseList = function(head) {
// uses array destructuring to assign values from an array to variables prev and current.
// equivalent to 'let prev = null;' 'let current = head;.'
    let [prev, current] = [null, head]
    while(current) {
        // uses array destructuring to assign values from an array to variables
        [current.next, prev, current] = [prev, current, current.next]  // a way to swap the values of these variables in one line.
    }
    return prev
}

/* Iterative approach
Initialize two pointers, prev as null and current as head.
Iterate through the list, reversing the links between nodes.
At each step, update the pointers to move to the next nodes.
Return the new head of the reversed list.
*/
var reverseList = function(head) {
let prev = null;
let current = head;
let next = null;

while (current != null) {
    // there is a diffrent between assign value to node, and assign node to another node (current.next = prev).
    next = current.next;
    current.next = prev;
    prev = current;
    current = next;
}
}
```





```javasceipt
/* 226. Invert Binary Tree -
Given the root of a binary tree, invert (reverse) the tree, and return its root.*/

var invertTree = function(root) {
    // Base case...
    if(root == null){
        return root
    }
    // Call the function recursively for the left subtree...
    invertTree(root.left)
    // Call the function recursively for the right subtree...
    invertTree(root.right)
    // swapping process...
    const curr = root.left
    root.left = root.right
    root.right = curr
    return root         // Return the root...   
};



```javasceipt
/* 704. Binary Search -
Given an array of integers nums which is sorted in ascending order,
and an integer target, write a function to search target in nums.
If target exists, then return its index. Otherwise, return -1.
You must write an algorithm with O(log n) runtime complexity. */

var search = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);   // rounds down 
        
        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;
};
```








<br>

---
<br>


## 🚀 Basic String and array manipulations:

### Count Characters
```javascript
// Write a function that counts the occurrences of each character in a string and returns an object with character counts.

function countCharacters(str) {
    const charCount = {};
    
    for (let char of str) {
        charCount[char] = (charCount[char] || 0) + 1;
    }    
    return charCount;
}

const inputString = "hello world";
const result = countCharacters(inputString);
console.log(result);

/* Output:
{
  h: 1,
  e: 1,
  l: 3,
  o: 2,
  ' ': 1,
  w: 1,
  r: 1,
  d: 1
} */
```



### Remove Duplicates from Array
```javascript
function removeDuplicates(arr) {
    return [...new Set(arr)];
}
```
```javascript
function removeDuplicates(arr) {
    return arr.filter((item, index) => arr.indexOf(item) === index);
}
// arr.indexOf(item) always return the first index on the item, but if the item occurs again, index return different number
```

### Find Common Elements
```javascript
function findCommonElements(arr1, arr2) {
    return arr2.filter(item => arr1.includes(item));
}
```

```javascript
function findCommonElements(arr1, arr2) {
    const set1 = new Set(arr1);
    const commonElements = arr2.filter(item => set1.has(item));
    
    return commonElements;
}


1. **`const set1 = new Set(arr1);`**: 
   - It creates a new `Set` from `arr1`, which automatically removes duplicate values from `arr1`.

2. **`const commonElements = arr2.filter(item => set1.has(item));`**: 
   - It filters `arr2` to keep only the elements that exist in `set1`, which means they are also present in `arr1`.

3. **`return commonElements;`**: 
   - It returns the filtered array containing the common elements.
```

```javascript
// Simpler Version:
function findCommonElements(arr1, arr2) {
    return arr2.filter(item => new Set(arr1).has(item));
}

1. **`new Set(arr1)`**: 
   - Creates a `Set` from `arr1`, removing duplicates.

2. **`new Set(arr1).has(item)`**: 
   - Checks if `item` from `arr2` exists in the `Set` created from `arr1`.

3. **`arr2.filter(item => new Set(arr1).has(item))`**: 
   - Filters `arr2` to keep only the items that are also found in `arr1`.

4. **`return arr2.filter(item => new Set(arr1).has(item));`**: 
   - Returns the filtered array containing the common elements.

This simplified version achieves the same result but in a more concise manner by directly using `new Set(arr1).has(item)` within the `filter` method.
```


### Rotate Array
Write a function that rotates an array to the right by a given number of steps.

```javascript
function rotateArray(arr, steps) {
    const n = arr.length;    // the rotation index
    const rotated = [];    // empty array for rotated elements

// calculates the new index for each element after rotation
// and assigns the rotated element to that index in the rotated array.
    for (let i = 0; i < n; i++) {
// Calculates the new index by adding the steps to the current index i and taking the remainder % with n.
// ensures that the index wraps around to the start of the array if it goes beyond the length of the array.
        rotated[(i + steps) % n] = arr[i];
    }    
    return rotated;
}


/* Example:
Let's say we have an array `arr = [1, 2, 3, 4, 5]` and `steps = 2`.
1. **Iteration 1**:
   - `i = 0`, `arr[0] = 1`, new index = `(0 + 2) % 5 = 2`, `rotated[2] = 1`
2. **Iteration 2**:
   - `i = 1`, `arr[1] = 2`, new index = `(1 + 2) % 5 = 3`, `rotated[3] = 2`
3. **Iteration 3**:
   - `i = 2`, `arr[2] = 3`, new index = `(2 + 2) % 5 = 4`, `rotated[4] = 3`
... */
```


### Removes duplicates
```javascript
// Removes duplicates by checking if the current index of an item is the same as the first
// occurrence of that item. If they match, it means the item is unique, and it's kept in the filtered array.
function removeDuplicates(arr) {
    return arr.filter((item, index) => arr.indexOf(item) === index);
}

`arr = [1, 2, 2, 3, 4, 4, 5]`.

1. For the first occurrence of `2`, `arr.indexOf(2)` returns `1`, and its current index (`index`) is also `1`. So, we keep `2`.

2. For the second occurrence of `2`, `arr.indexOf(2)` still returns `1`, but its current index (`index`) is `2`. So, we filter it out.

3. Similarly, for `4`, we keep only the first occurrence.
```

### Sort the array by the last letter of a string
```javascript
const sortFn = (a, b) => {
  if (a[a.length - 1] < b[b.length - 1]) {
    return -1; // Negative number => a < b, a comes before b
  } else if (a[a.length - 1] > b[b.length - 1]) {
    return 1; // Positive number => a > b, a comes after b
  }
  return 0; // Zero => a = b, a and b keep their original order
};
myArray.sort(sortFn);    // sorts the array so that myArray = ["Wind","Fire","Rain"]
```




### Find the Largest Number:
```javascript
function findLargestNumber(arr) {
  let largest = arr[0]; // Initialize largest to the first element of the array
  // Iterate through the array starting from the second element
  for (let i = 1; i < arr.length; i++) {
    // If the current element is greater than the current largest, update largest
    if (arr[i] > largest) {
      largest = arr[i];
    }
  }
  return largest; // Return the largest number found
}

// Example usage:
const numbers = [10, 5, 20, 15];
console.log(findLargestNumber(numbers)); // Output: 20
```

### Calculate Factorial:

```javascript
function factorial(n) {
  // Base case: If n is 0 or 1, return 1
  if (n === 0 || n === 1) {
    return 1;
  }
  // Recursive case: Multiply n by factorial of (n - 1)
  return n * factorial(n - 1);
}

// Example usage:
const num = 5;
console.log(factorial(num)); // Output: 120
```

### Check Palindrome:

```javascript
function isPalindrome(str) {
  const reversedStr = str.split('').reverse().join(''); // Reverse the string
  // Check if the original string is equal to the reversed string
  return str === reversedStr;
}

// Example usage:
const word = 'radar';
console.log(isPalindrome(word)); // Output: true
```

### Fibonacci Sequence:

```javascript
function fibonacci(n) {
  const sequence = [0, 1]; // Initialize sequence with first two Fibonacci numbers
  // Generate Fibonacci sequence up to the given number of terms
  for (let i = 2; i < n; i++) {
    sequence.push(sequence[i - 1] + sequence[i - 2]); // Add the next Fibonacci number to the sequence
  }
  return sequence; // Return the Fibonacci sequence
}

// Example usage:
const terms = 8;
console.log(fibonacci(terms)); // Output: [0, 1, 1, 2, 3, 5, 8, 13]
```


### Reverse a String:

```javascript
function reverseString(str) {
  return str.split('').reverse().join(''); // Split, reverse, and join the string
}

// Example usage:
const text = 'hello';
console.log(reverseString(text)); // Output: olleh
```

### Check Prime Number:

```javascript
function isPrime(n) {
  // Prime numbers are greater than 1 and divisible only by 1 and themselves
  if (n <= 1) {
    return false;
  }
  for (let i = 2; i <= Math.sqrt(n); i++) {
    if (n % i === 0) {
      return false; // If n is divisible by any number other than 1 and itself, it's not prime
    }
  }
  return true; // If no divisor is found, n is prime
}

// Example usage:
const number = 13;
console.log(isPrime(number)); // Output: true
```

### Find Sum of Digits:

```javascript
function sumOfDigits(n) {
  let sum = 0;
  // Iterate until n becomes 0
  while (n > 0) {
    sum += n % 10; // Add the last digit to sum
    n = Math.floor(n / 10); // Remove the last digit from n
  }
  return sum; // Return the sum of digits
}

// Example usage:
const num = 123;
console.log(sumOfDigits(num)); // Output: 6
```

### Count Vowels and Consonants:

```javascript
function countVowelsAndConsonants(str) {
  const vowels = 'aeiouAEIOU';
  let vowelCount = 0;
  let consonantCount = 0;
  // Iterate through each character of the string
  for (let char of str) {
    //For each character, it checks if it belongs to the set of vowels defined in the vowels 
    if (vowels.includes(char)) {
      vowelCount++; // Increment vowel count if the character is a vowel
    // If the character is not a vowel, it checks if it is an alphabet (either lowercase or uppercase) using a regular expression (/[a-zA-Z]/).
    } else if (char.match(/[a-zA-Z]/)) {
      consonantCount++; // Increment consonant count if the character is an alphabet
    }
  }
  return { vowels: vowelCount, consonants: consonantCount }; // Return counts as an object
}

// Example usage:
const text = 'hello world';
console.log(countVowelsAndConsonants(text)); // Output: { vowels: 3, consonants: 7 }
```

### Merge and Sort Two Arrays:
```javascript
function mergeSortedArrays(arr1, arr2) {
// שימוש באופרטור ה-(...) לאיחוד שני מערכים, למערך חדש, המכיל את כל האיברים משני המערכים המקוריים.
  return [...arr1,...arr2].sort((a, b) => a - b); // Concatenate (שרשור) arrays and sort the resulting array
}
// Example usage:
const array1 = [1, 3, 5];
const array2 = [2, 4, 6];
console.log(mergeSortedArrays(array1, array2)); // Output: [1, 2, 3, 4, 5, 6]

// another option with concat() -
function mergeSortedArrays(arr1, arr2) {
    let mergedArray = arr1.concat(arr2);    //concatenate
    meegedArray.sort((a,b) => a-b);    // default sort in ascending order
    return meegedArray;
}
```


### Find Missing Number:
```javascript
function findMissingNumber(arr) {
  const n = arr.length + 1; // Number of elements if the missing number is included
  const totalSum = (n * (n + 1)) / 2; // Sum of all numbers from 1 to n
  const currentSum = arr.reduce((acc, cur) => acc + cur, 0); // Sum of elements in the array
  return totalSum - currentSum; // Difference gives the missing number
}

// Example usage:
const numbers = [1, 2, 3, 5];
console.log(findMissingNumber(numbers)); // Output: 4
```


