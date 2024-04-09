# 🎯🏆 Technical Exercises and knowledge


# 🏆 Logical Exercise (`Leetcode`) -

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
```



```javascript   
/* 206. Reverse Linked List
Given the head of a singly linked list, reverse the list, and return the reversed list.
*/

// Recursive approach 
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










<br>
---
<br>



# 🏆 Technical Knowledge

## **HTTP Requests and Responses:**
The process of an HTTP request and response cycle: 
When a client sends an HTTP request to a server, it includes a request method (GET, POST, etc.), headers, and optional data.
The server processes the request and generates an HTTP response, including a status code, headers, and optional data.
The response is sent back to the client, indicating success or failure of the request.

- [x] **GET Request:**
   - Used to `request data from a server`, data is sent `in the URL`, typically used `for retrieving data`, data is visible in the URL.

- [x] **POST Request:**
   - Used to `submit data to a server`, `data is sent in the request body`, typically used `for submitting data`, data is not visible in the URL.


#### How to make GET and POST requests using the Fetch API in JavaScript. 

- [ ] The `GET request retrieves data from a specified URL`, while the `POST request submits form data to a specified endpoint`.
- [ ] `'https://api.example.com'` is the API endpoint you want to interact with.
      
1. **GET Request:**
   - Example URL: `https://api.example.com/products?category=electronics`
   - Purpose: Retrieve a list of electronics products from the server.
   - Parameters: `category=electronics` is included in the URL query string to specify the category of products to retrieve.
   - Usage: Used when fetching data from the server, such as retrieving information from a database or accessing a web page.

```javascript
// Example of a GET request using Fetch API
fetch('https://api.example.com/products?category=electronics')
  .then(response => {
    return response.json();
  })
  .then(data => {
    // Process the retrieved data
    console.log('Products:', data);
  })
```

2. **POST Request:**
   - Example URL: `https://api.example.com/login`
   - Purpose: Submit user credentials (username and password) to the server for authentication.
   - Data Format: The username and password are sent in the request body as form data or JSON.
   - Usage: Used when submitting sensitive information or performing actions that modify server state, such as submitting a login form, uploading a file, or creating a new resource on the server.

```javascript
// Example of a POST request using Fetch API
const formData = new FormData();
formData.append('username', 'exampleuser');
formData.append('password', 'secretpassword');

fetch('https://api.example.com/login', {
  method: 'POST',
  body: formData
})
  .then(response => {
    return response.json();
  })
  .then(data => {
    // Handle successful login response
    console.log('Login successful:', data);
  })
```




## **Technical Concepts:**
   - **HTML vs. XHTML:** HTML (Hypertext Markup Language) and XHTML (Extensible Hypertext Markup Language) are both markup languages used to structure content on web pages. XHTML is a stricter and more XML-based version of HTML. It requires well-formed syntax and uses XML rules, while HTML has more lenient syntax rules.
   - **CSS Specificity:** CSS specificity determines which CSS rule is applied to an element when multiple rules conflict. Specificity is based on selectors' complexity and order, where inline styles have the highest specificity, followed by IDs, classes, and elements.
   - **DOM (Document Object Model):** The DOM is a programming interface for web documents. It represents the structure of HTML/XML documents as a tree-like structure, with each node representing an element, attribute, or piece of text. JavaScript interacts with the DOM to dynamically update content and styles on web pages.




## 🏆 Client-Server Architecture 
- [ ] Both the server-side and client-side have implementations for handling `both POST and GET requests`.
- [ ] The `server-side` code processes `incoming requests` and `generates responses`,
- [ ] while the `client-side` `sends requests to the server` and `updates the user interface based on the responses received`.

1. **Server-Side:**
   - [ ] Server `handles incoming requests from clients`, processes them, and returns responses.
   - [ ] It will have endpoints or routes defined to handle specific types of requests, such as GET requests for retrieving data and POST requests for submitting data.
   - [ ] In a web server environment, these endpoints are often implemented using server-side technologies like `Node.js`.
   - [ ] The server-side code will include `logic to process incoming requests, interact with databases or other resources, and generate appropriate responses`.

2. **Client-Side:**
   - [ ] Client `interacts with users and sends requests to the server` to `fetch/pull or submit data`.
   - [ ] It will include code to send HTTP requests, such as GET requests to retrieve data from the server or POST requests to submit data to the server.
   - [ ] Written in JavaScript, which can use APIs like Fetch or XMLHttpRequest to send requests to the server.
   - [ ] The client-side code `handle user interactions, send requests to the server, and update the user interface based on the server's responses`.


## Server-side and Client-side code for handling POST and GET requests:
Node.js server handles GET and POST requests using Express.js, and a client-side web page interacts with the server using Fetch API to retrieve and submit data

1. **Server-Side (Using Node.js with Express.js):**

```javascript
// Server-side code (app.js)
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
const PORT = 3000;

app.use(bodyParser.json());// Middleware to parse JSON bodies

// GET endpoint to retrieve data
app.get('/api/data', (req, res) => {
  // Assuming data is stored in a variable or fetched from a database
  const data = { message: 'Hello from the server!' };
  res.json(data);
});

// POST endpoint to submit data
app.post('/api/submit', (req, res) => {
  const { name, email } = req.body;
  // Process the submitted data (e.g., save to a database)
  console.log('Received data:', name, email);
  res.sendStatus(200);
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```

2. **Client-Side (Using JavaScript in a web browser):**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Client-Side Example</title>
</head>
<body>
  <h1>Client-Side Example</h1>

  <!-- Form for submitting data -->
  <form id="submitForm">
    <input type="text" name="name" placeholder="Name">
    <input type="email" name="email" placeholder="Email">
    <button type="submit">Submit</button>
  </form>

  <!-- Container for displaying data -->
  <div id="dataContainer"></div>

  <script>
    // Function to send a GET request to retrieve data
    function fetchData() {
      fetch('/api/data')
        .then(response => response.json())
        .then(data => {
          const dataContainer = document.getElementById('dataContainer');
          dataContainer.innerHTML = `<p>${data.message}</p>`;
        })
        .catch(error => console.error('Error fetching data:', error));
    }

    // Function to handle form submission and send a POST request
    function submitData(event) {
      event.preventDefault();
      const formData = new FormData(event.target);
      
      fetch('/api/submit', {
        method: 'POST',
        body: formData
      })
        .then(() => {
          console.log('Data submitted successfully');
          // Optionally, fetch updated data after submission
          fetchData();
        })
        .catch(error => console.error('Error submitting data:', error));
    }

    // Attach event listener to form submission
    const submitForm = document.getElementById('submitForm');
    submitForm.addEventListener('submit', submitData);

    // Fetch initial data when the page loads
    fetchData();
  </script>
</body>
</html>
```







<br>

---
<br>



# 🏆 Data Structure:
Used to organize and manipulate data efficiently, allowing for optimal storage, retrieval, and manipulation of information.

-[x] Arrays: Ordered collection of elements with constant-time access to individual elements.
-[x] Linked Lists: Collection of nodes where each node points to the next node in the sequence.
-[x] Stacks: LIFO (Last In, First Out) data structure (push and pop).
-[x] Queues: FIFO (First In, First Out) data structure (enqueue and dequeue).
-[x] Trees: Hierarchical data structure consisting of nodes connected by edges, with a root node at the top.
-[x] Graphs: Non-linear data structure consisting of nodes (vertices) and edges connecting them.


1. **Arrays:**
   - Collection of elements, can be accessed using an index, with constant-time access to individual elements.
   - Have a fixed size, meaning their size is determined at the time of declaration.
   - Common operations include accessing, inserting, deleting, and searching for elements.

2. **Linked Lists:**
   - Linear data structure consisting of nodes, where each node contains a data element and a reference (pointer) to the next node in the sequence.
   - Can be singly linked (each node points to the next node) or doubly linked (each node points to both the next and previous nodes).
   - Insertion and deletion operations are efficient (O(1)) when performed at the beginning or end of the list but require traversal (O(n)) for operations in the middle.

3. **Stacks:**
   - Linear data structure that follows the Last In, First Out (LIFO) principle.
   - Elements are inserted (pushed) and removed (popped) from the top of the stack.
   - Common operations include push (add an element to the top), pop (remove the top element), and peek (retrieve the top element without removing it).

4. **Queues:**
   - Linear data structure that follows the First In, First Out (FIFO) principle.
   - Elements are inserted (enqueued) at the rear and removed (dequeued) from the front of the queue.
   - Common operations include enqueue (add an element to the back), dequeue (remove the front element), and peek (retrieve the front element without removing it).

5. **Trees:**
   - Hierarchical data structure consisting of nodes connected by edges (Special case of graphs, and specific constraints (no cycles, single root).
   - Trees have a root node at the top, with child nodes branching out from the root.
   - Common types of trees include `binary trees` (each node has at most two children), binary search trees (left child < parent < right child), and balanced trees (maintain balance for efficient operations).

   - [x] **Binary Trees:**
      - Like a family tree where each person can have up to two children.
      - Used for organizing data and representing hierarchical relationships.
   
   - [x] **Binary Search Trees (BSTs):**
      - Special binary tree where each node has a value, and the left child's value is less than the parent's, while the right child's value is greater.
      - Efficient for searching, inserting, and deleting elements due to its ordered structure.
   
   - [x] **Balanced Trees:**
      -Type of binary tree where the heights of the left and right subtrees of any node differ by at most one.


7. **Graphs:**
   -  Wider concept that can represent any connected set of nodes and edges (Non-linear data structure).
   - Graphs can be directed (edges have a direction) or undirected (edges do not have a direction).
   - Common operations include adding or removing vertices and edges, crossing the graph (e.g., depth-first search, breadth-first search), and finding shortest paths.



1. **Arrays:**
   - Time Complexities:
     - Access: O(1)
     - Search (unsorted): O(n)
     - Search (sorted, binary search): O(log n)
     - Insertion (at the end): O(1) amortized, O(n) worst-case
     - Deletion (at the end): O(1)
   - Important Methods:
     - `push(element)`: Adds an element to the end of the array.
     - `pop()`: Removes and returns the last element of the array.
     - `shift()`: Removes and returns the first element of the array.
     - `unshift(element)`: Adds an element to the beginning of the array.

2. **Linked Lists:**
   - Time Complexities:
     - Access: O(n)
     - Search: O(n)
     - Insertion (at the beginning): O(1)
     - Insertion (at the end, with tail pointer): O(1)
     - Deletion (at the beginning): O(1)
   - Important Methods:
     - `insertFirst(element)`: Inserts an element at the beginning of the linked list.
     - `insertLast(element)`: Inserts an element at the end of the linked list.
     - `deleteFirst()`: Deletes the first element of the linked list.
     - `deleteLast()`: Deletes the last element of the linked list.

3. **Stacks:**
   - Time Complexities:
     - Push: O(1)
     - Pop: O(1)
     - Peek: O(1)
   - Important Methods:
     - `push(element)`: Adds an element to the top of the stack.
     - `pop()`: Removes and returns the top element of the stack.
     - `peek()`: Returns the top element of the stack without removing it.

4. **Queues:**
   - Time Complexities:
     - Enqueue: O(1)
     - Dequeue: O(1)
     - Peek: O(1)
   - Important Methods:
     - `enqueue(element)`: Adds an element to the rear of the queue.
     - `dequeue()`: Removes and returns the front element of the queue.
     - `peek()`: Returns the front element of the queue without removing it.

5. **Trees:**
   - Time Complexities (for binary search trees):
     - Search: O(log n) average, O(n) worst-case (unbalanced)
     - Insertion: O(log n) average, O(n) worst-case (unbalanced)
     - Deletion: O(log n) average, O(n) worst-case (unbalanced)
   - Important Methods:
     - `insert(value)`: Inserts a value into the binary search tree.
     - `search(value)`: Searches for a value in the binary search tree.
     - `delete(value)`: Deletes a value from the binary search tree.

6. **Graphs:**
   - Time Complexities (for adjacency list representation):
     - Accessing neighbors: O(1) on average (using hash table or array)
     - Insertion of vertices and edges: O(1)
     - Deletion of vertices and edges: O(|E|) where |E| is the number of edges
   - Important Methods:
     - `addVertex(vertex)`: Adds a vertex to the graph.
     - `addEdge(vertex1, vertex2)`: Adds an edge between two vertices.
     - `removeVertex(vertex)`: Removes a vertex from the graph.
     - `removeEdge(vertex1, vertex2)`: Removes an edge between two vertices.



<br>

---
<br>




# 🏆 Recursion

Each recursive call works on a smaller part of the problem until the base case is reached, and then combining the results to solve the original problem. 


**1. Understanding Recursion:**
Recursion is a programming technique where a function calls itself to solve smaller instances of the same problem. Each recursive call works on a smaller part of the problem until a base case is reached.

**2. Backtracking in Recursion:**
In recursive algorithms, backtracking occurs when a function returns from a recursive call without finding a solution. When this happens, the algorithm needs to backtrack to the previous level of recursion and try a different option.

**3. Step-by-Step Explanation:**

Let's illustrate backtracking in recursion with an example of finding all permutations of a string.

- **Example Problem:** Given a string, find all possible permutations of its characters.

- **Algorithm:**
  1. Start with an empty prefix and the entire string as the remaining characters.
  2. For each character in the remaining string:
     - Add the character to the prefix.
     - Recursively find permutations of the remaining characters.
     - Backtrack by removing the added character from the prefix.

- **Illustration:**
  - Suppose we have the string "ABC".
  - We start with an empty prefix and "ABC" as the remaining characters.
  - We choose 'A' as the first character and recursively find permutations of "BC".
  - We choose 'B' as the second character and recursively find permutations of "C".
  - We choose 'C' as the third character and reach the base case (when there are no more characters left).
  - We backtrack to the previous level of recursion and try the next option ('B').
  - We continue this process until we exhaust all options.

**4. Building Up the Solution:**
As the recursion progresses, each recursive call contributes to building up the solution. The solution is gradually constructed as the recursion unwinds and returns from each call.

**5. Combining Results:**
In problems where multiple recursive calls are made (e.g., finding all permutations), the results from each call need to be combined to form the final solution. This is typically done by appending or merging the results from each recursive call.




## The concept of building up the solution in recursion:

**Example: Summing Numbers** - a recursive function to calculate the sum of the first N positive integers.

Building up the solution by adding the current value of N to the sum as we return from each recursive call. This process continues until we reach the base case, resulting in the final solution.

Here's how the function would work:

1. **Base Case:** 
   - If N is 0, the sum is 0.
   - This is our base case, as it represents the simplest instance of the problem.

2. **Recursive Step:**
   - If N is greater than 0, we recursively call the function with N-1.
   - Each recursive call works on a smaller instance of the problem.

3. **Building Up the Solution:**
   - As we return from each recursive call, we add the current value of N to the sum.
   - This adds up all the positive integers from N to 1.

**Illustration:**

Let's find the sum of the first 3 positive integers: 1 + 2 + 3.

1. **Initial Call:** `sum(3)`

2. **Recursive Calls:**
   - `sum(3)` calls `sum(2)`
   - `sum(2)` calls `sum(1)`
   - `sum(1)` calls `sum(0)`

3. **Base Case (sum(0)):**
   - Since N is 0, the function returns 0.

4. **Backtracking:**
   - As we return from each recursive call, we add the current value of N to the sum.
   - `sum(1)` returns 1, `sum(2)` returns 3, and `sum(3)` returns 6.

5. **Final Result:**
   - The final result is 6, which is the sum of the first 3 positive integers.

**Code:**
Here's the JavaScript code for the recursive function:

```javascript
function sum(N) {
    // Base case: if N is 0, return 0
    if (N === 0) {
        return 0;
    }
    // Recursive step: call sum with N-1
    return N + sum(N - 1);
}

// Test the function
console.log(sum(3)); // Output: 6
```










## 🎯 Recursive Approach for reverse `Linked List`:
```javascript
var reverseList = function(head) {
    // Base case: if head is null or there's only one node
    if (head == null || head.next == null) return head;
    
    // Recursive call to reverse the rest of the list
    var res = reverseList(head.next);
    
    // Reverse the link between head and head.next
    head.next.next = head;
    
    // Set head's next to null to mark the end of the reversed list
    head.next = null;
    
    // Return the new head of the reversed list
    return res;
};
```

This approach uses recursion to reverse the linked list.
It starts by checking for a special case where the head is null or there is only one node (base case).
If the base case is not met, it recursively calls the function on the next node, effectively traversing to the end of the list.
Once the end of the list is reached, it starts reversing the links by setting the next node's next pointer to the current node (essentially reversing the direction of the pointer).
Finally, it sets the current node's next pointer to null to mark the end of the reversed list and returns the new head of the reversed list.
This approach has a time complexity of O(n) and a space complexity of O(n) due to the recursive calls on the stack.


1. **Base Case:** 
   - We first handle the simplest cases:
     - If the list is empty (`head` is null), or
     - If there's only one node in the list.
   - In these cases, there's nothing to reverse, so we just return the `head` as it is.

2. **Recursion:**
   - If the base case is not met (meaning there are at least two nodes in the list), we call the `reverseList` function recursively on the next node.
   - This recursive call continues until it reaches the end of the original list.

3. **Reverse Links:**
   - Once we reach the end of the list, we start reversing the links between nodes.
   - For each node:
     - We make its next pointer point to the previous node, effectively reversing the direction of the link.
     - Then, we move to the next node and repeat this process until we reach the end of the original list.

4. **Returning the New Head:**
   - After all nodes are reversed, the last node of the original list becomes the new head of the reversed list.
   - So, we return this new head to indicate the start of the reversed list.

The recursive approach breaks down the problem by handling the simplest cases first, then using recursion to reverse the remaining nodes. Finally, it reverses the links between nodes and returns the new head of the reversed list.


### A simpler explanation:

1. **Base Case:**
   - Recursion involves breaking a problem down into smaller, more manageable pieces.
   - The base case is like a stopping point. It's the simplest version of the problem that doesn't need further breaking down.
   - Once we reach the base case, we stop breaking the problem into smaller pieces and start solving it.

2. **Recursive Call:**
   - We call the same function from within itself but with a smaller input.
   - Each recursive call works on a smaller part of the original problem.
   - This continues until we reach the base case.

3. **Backtracking:**
   - Once the base case is reached, the function starts returning values.
   - As the function returns from each recursive call, it combines the results to solve the original problem.

In the case of reversing a linked list:

- The base case is when we reach the end of the list (head is null or there's only one node).
- The recursive call works on the rest of the list (head.next).
- We keep reversing links and returning the new head of the reversed list until we reach the base case.

The order of iterations in the example provided is:

1. Recursive call with `reverseList(1)`
2. Recursive call with `reverseList(2)`
3. Recursive call with `reverseList(3)`
4. Backtracking from `reverseList(2)`
5. Backtracking from `reverseList(1)`
6. Recursive call with `reverseList(3)`



### Step-by-step breakdown of how `reverseList` recursion unfolds:

1. **Initial Call:** 
   - We start with the initial call `reverseList(1)`.

2. **First Recursive Call:** 
   - Within `reverseList(1)`, there's a recursive call `reverseList(2)`. This call dives deeper into the linked list, working on the rest of the list beyond the current node.

3. **Second Recursive Call:** 
   - Within `reverseList(2)`, there's another recursive call `reverseList(3)`. This call dives even deeper into the list, working on the next node.

4. **Base Case Reached:** 
   - Eventually, we reach a point where `head` becomes null (indicating the end of the list) or there's only one node left.
   - At this point, we reach the base case, and the recursion starts to unwind (backtrack).

5. **Backtracking:** 
   - As the recursion unwinds, each recursive call returns a value or a reference to a node.
   - We use these returned values to construct the reversed list step by step.

So, the order of iterations (calls and backtracking) in the example would be:

1. Recursive call `reverseList(1)`
2. Within `reverseList(1)`, recursive call `reverseList(2)`
3. Within `reverseList(2)`, recursive call `reverseList(3)`
4. Backtracking from `reverseList(3)` (once the base case is reached)
5. Backtracking from `reverseList(2)`
6. Backtracking from `reverseList(1)` (final result obtained)



## Backtracking
Backtracking is the process of unwinding recursive calls and returning to previous levels of the recursion stack once the base case is reached or when a solution is found. It allows the algorithm to explore all possible solutions to a problem by systematically trying different options and then undoing those choices if they don't lead to a solution.

In the case of the `reverseList` function, once the base case is reached (i.e., when `head` is null or there's only one node), the recursion starts to unwind or backtrack. During this process:

- Each recursive call returns a value or reference that contributes to solving the original problem.
- As we return from each recursive call, we gradually build up the solution or perform necessary operations.
- The algorithm goes back to the previous level of recursion, where it continues execution and may perform additional operations or computations.

In the context of reversing a linked list, backtracking involves returning from each recursive call, reversing the links between nodes, and eventually constructing the reversed list step by step.










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







