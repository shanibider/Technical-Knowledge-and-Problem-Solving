# 🏆 Logical Exercises (`Leetcode`) -




```javascript
// Split Into Digits -
//Split a into its individual digits and return them in an array.
function splitIntoDigits(a) {
    const string = a + '';  // Convert to string (This method effectively converts the number a into a string)
    const strings = string.split(''); // Split into individual characters! because (''). If it was (' ') it split into strings.
    return strings.map(digit => Number(digit))    // Convert each character back to a number. The result is an array of numbers representing the digits of the original number a.
    // return Array.from(String(a), Number);
}
```


**Find the Largest Number**:
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

**Calculate Factorial**:

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

**Check Prime Number**:

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

**Find Sum of Digits**:

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


**Merge and Sort Two Arrays**:
```javascript
function mergeSortedArrays(arr1, arr2) {
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




**Find Missing Number**:

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



**Problem Statement: Two Sum**
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
```javascript
var twoSum = function(nums, target) {
    const numMap = {}; // Create an empty object to store numbers and their indices
    
    for (let i = 0; i < nums.length; i++) {
        const complement = target - nums[i]; // Calculate the complement needed for the current number
        
        if (numMap.hasOwnProperty(complement)) {
            // If the complement exists in the map, return its index and the current index
            return [numMap[complement], i];
        }
        
        // Store the current number and its index in the map
        numMap[nums[i]] = i;
    }
    
    return []; // Return an empty array if no solution is found
};

// Test cases
console.log(twoSum([2, 7, 11, 15], 9)); // Output: [0, 1]
console.log(twoSum([3, 2, 4], 6)); // Output: [1, 2]
console.log(twoSum([3, 3], 6)); // Output: [0, 1]
```



```javascript
// 1. **Reverse a String:**
   function reverseString(str) {
       // Split the string into an array of characters, reverse the array, then join the characters back into a string
       return str.split('').reverse().join('');
   }
```

```javascript
// 2. **Palindrome Checker:**
   function isPalindrome(str) {
       // Reverse the string and compare it with the original string to check if they are equal
       const reversedStr = str.split('').reverse().join('');
       return str === reversedStr;
   }
```

```javascript
// 3. **Fibonacci Sequence:**
   function fibonacci(n) {
       // Initialize the Fibonacci sequence array with the first two numbers
       const sequence = [0, 1];
       // Generate the Fibonacci sequence up to the specified number of terms
       for (let i = 2; i < n; i++) {
           sequence.push(sequence[i - 1] + sequence[i - 2]);
       }
       return sequence;
   }
```   

```javascript
// 4. **Factorial Calculation:**
   function factorial(n) {
       // Initialize the result to 1
       let result = 1;
       // Multiply the result by each integer from 2 to n
       for (let i = 2; i <= n; i++) {
           result *= i;
       }
       return result;
   }
```

```javascript
// 5. **Anagram Detection:**
   function isAnagram(str1, str2) {
       // Sort the characters in each string and compare the sorted strings
       const sortedStr1 = str1.split('').sort().join('');
       const sortedStr2 = str2.split('').sort().join('');
       return sortedStr1 === sortedStr2;
   }


```javascript
// 6. **Find the Largest Number:**
   function findLargestNumber(arr) {
       // Use the spread operator to pass the array elements as arguments to Math.max
       return Math.max(...arr);
   }
```

```javascript
// 7. **Sum of Array Elements:**
   function sumArray(arr) {
       // Use the reduce method to sum up all elements in the array
       return arr.reduce((acc, curr) => acc + curr, 0);
   }
```

```javascript
// 8. **Counting Characters:**
   function countCharacters(str) {
       // Initialize an empty object to store the character counts
       const charCount = {};
       // Iterate through each character in the string
       for (let char of str) {
           // Increment the count for each character
           charCount[char] = charCount[char] + 1 || 1;
       }
       return charCount;
   }
```


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
// Return the longest binary gap in integer `N`.
//A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

//- Consider using a flag to indicate when you're inside a potential gap and when you're not. This can help you keep track of the length of each gap.

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
/*
21. Merge Two Sorted Lists
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
// 206. Reverse Linked List
// Given the head of a singly linked list, reverse the list, and return the reversed list.

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

// Iterative approach
// Initialize two pointers, prev as null and current as head.
// Iterate through the list, reversing the links between nodes.
// At each step, update the pointers to move to the next nodes.
// Return the new head of the reversed list.
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
/* 226. Invert Binary Tree
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






















<br>

---
<br>



# 🏆 How-to Approach logic Challengaes:

1. **Problem Classification:**
   - Categorize the problem based on its characteristics, such as: 
     - `array manipulation, string manipulation, dynamic programming, graph algorithms, etc`. Knowing the category of the problem can guide you towards suitable approaches and algorithms commonly used for that category.

2. **Brainstorm Solutions + Choose an Approach:**
   - Think about different approaches or algorithms that could solve the problem. Consider whether any known techniques or data structures could be useful.
   - Based on your brainstorming and understanding of the problem, select an approach that seems most suitable. Consider factors such as simplicity, efficiency, and ease of implementation.


3. **Use Known Algorithms and Techniques:**
   - Leverage your knowledge of common algorithms and data structures. For example, if the problem involves searching, consider binary search for sorted arrays. If it involves dynamic programming, think about ways to break down the problem into smaller subproblems.

4. **Review Similar Problems:**
   - Search for similar problems on LeetCode that can give you insights into effective approaches and techniques that can be applied to the current problem.

5. **Follow Problem-Solving Patterns:**
   - Familiarize yourself with `common problem-solving patterns and techniques`, such as `two-pointer technique`, `sliding window`, `backtracking`, `divide and conquer`, etc. Recognizing patterns in the problem statement can help you choose appropriate strategies.

6. **Draw Diagrams and Visualize:**
   - Sometimes, drawing diagrams or visualizing the problem can help you understand its structure and relationships better. For example, for graph problems, drawing the graph can make it easier to identify paths, cycles, or connectivity.


7. **Break Down the Problem:**
   - If the problem seems complex, try breaking it down into smaller subproblems. Solve each subproblem individually and then combine the solutions to solve the main problem. 

8. **Write Pseudocode:**
   - Before writing actual code, outline the steps of your chosen approach in pseudocode. This helps clarify your thought process and serves as a roadmap for implementing the solution.


---
