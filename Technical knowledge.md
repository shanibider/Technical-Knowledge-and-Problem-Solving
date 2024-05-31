# 🎯 Technical Exercises and knowledge


### 🏆 Technical Knowledge -

# 🏆 React -

## 🏆 Axios 
Axios is a popular `JavaScript library` used for `making HTTP requests from both the browser and Node.js` environments. It provides a simple and intuitive API for performing asynchronous operations, such as fetching data from a remote server or posting data to an API endpoint.


```javascript
const axios = require('axios');

// Making a POST request to an external API with data
axios.post('https://api.example.com/posts', {
    title: 'foo',
    body: 'bar',
    userId: 1
  })
  .then(response => {
    console.log('Post created:', response.data);
  })
  .catch(error => {
    console.error('Error creating post:', error);
  });
```

```javascript
// Making a POST request using Fetch API with data
fetch('https://api.example.com/posts', {
    method: 'POST',
    body: JSON.stringify({
      title: 'foo',
      body: 'bar',
      userId: 1
    }),
    headers: {
      'Content-type': 'application/json; charset=UTF-8',
    },
  })
  .then(response => response.json())
  .then(data => {
    console.log('Post created:', data);
  })
  .catch(error => {
    console.error('Error creating post:', error);
  });
```



## 🏆 AJAX
Ajax stands for `Asynchronous JavaScript and XML`. It's a set of web development techniques used to create asynchronous web applications. With Ajax, `web pages can send and receive data from a server` asynchronously without interfering with the display and behavior of the existing page.


```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ajax Example</title>
</head>
<body>
  <div id="data-container">
    <!-- Data will be displayed here -->
  </div>
  <button id="load-data">Load Data</button>

  <script src="script.js"></script>
</body>
</html>
```



```javascript
document.getElementById('load-data').addEventListener('click', loadData);

function loadData() {
  // Make a GET request to a JSON API
  fetch('https://jsonplaceholder.typicode.com/posts')
    .then(response => {
      // Check if response is OK (status code 200)
      if (!response.ok) {
        throw new Error('Network response was not ok');
      }
      // Parse JSON data
      return response.json();
    })
    .then(data => {
      // Display data on the page
      const dataContainer = document.getElementById('data-container');
      dataContainer.innerHTML = '';
      data.forEach(post => {
        const postElement = document.createElement('div');
        postElement.innerHTML = `<h3>${post.title}</h3><p>${post.body}</p>`;
        dataContainer.appendChild(postElement);
      });
    })
    .catch(error => {
      // Handle errors
      console.error('There was a problem fetching the data:', error);
    });
}
```


## Axios vs Fetch API 
Both examples demonstrate making a `POST` request to an external API endpoint `(https://api.example.com/posts)` with data. The Axios example uses `Axios library`, while the Fetch API example utilizes the `built-in Fetch API`. They both handle the response and error in a similar way, showcasing the flexibility of both approaches in handling HTTP requests.

```javascript
const axios = require('axios');

// Making a POST request to an external API with data
axios.post('https://api.example.com/posts', {
    title: 'foo',
    body: 'bar',
    userId: 1
  })
  .then(response => {
    console.log('Post created:', response.data);
  })
  .catch(error => {
    console.error('Error creating post:', error);
  });
```

```javascript
// Making a POST request using Fetch API with data
fetch('https://api.example.com/posts', {
    method: 'POST',
    body: JSON.stringify({
      title: 'foo',
      body: 'bar',
      userId: 1
    }),
    headers: {
      'Content-type': 'application/json; charset=UTF-8',
    },
  })
  .then(response => response.json())
  .then(data => {
    console.log('Post created:', data);
  })
  .catch(error => {
    console.error('Error creating post:', error);
  });
```





## 🏆 Context API 
Provides a way to pass data through the component tree without having to pass props down manually at every level. It's commonly used for sharing global state or configuration settings between components.
```javascript
import React, { createContext, useContext, useState } from 'react';

// Step 1: Create a context
const ThemeContext = createContext();

// Step 2: Create a provider component
const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

// Step 3: Create a custom hook to consume the context
const useTheme = () => {
  return useContext(ThemeContext);
};

// Step 4: Use the provider in your app
const App = () => {
  return (
    <ThemeProvider>
      <Toolbar />
    </ThemeProvider>
  );
};

// Step 5: Use the custom hook to access the context in child components
const Toolbar = () => {
  const { theme, setTheme } = useTheme();

  return (
    <div>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Toggle Theme
      </button>
      <p>Current Theme: {theme}</p>
    </div>
  );
};

export default App;
```

In this example:
- We create a context using createContext().
- We create a provider component (ThemeProvider) to wrap the part of the component tree where we want to share the context.
- We define a custom hook (useTheme) to consume the context.
- We use the provider (ThemeProvider) in our app and wrap the Toolbar component with it.
- Inside the Toolbar component, we use the custom hook (useTheme) to access the context values and update the theme state.







## 🏆 Redux
Redux is a predictable state container for JavaScript apps, most commonly used with React. It helps you manage the state of your application in a centralized store, making it easier to maintain and debug your application as it grows.

### Example:
```javascript
// Step 1: Install Redux and React-Redux (for integrating Redux with React)
// npm install redux react-redux

// Step 2: Create Redux actions, reducers, and store

// actions.js
export const increment = () => {
  return {
    type: 'INCREMENT'
  };
};

export const decrement = () => {
  return {
    type: 'DECREMENT'
  };
};

// reducers.js
const counterReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
};

export default counterReducer;

// store.js
import { createStore } from 'redux';
import counterReducer from './reducers';

const store = createStore(counterReducer);

export default store;

// Step 3: Provide the Redux store to your React app

// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import App from './App';
import store from './store';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);

// Step 4: Use Redux in your React components

// App.js
import React from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { increment, decrement } from './actions';

const App = () => {
  const count = useSelector(state => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
};

export default App;
```

In this example:
1. We define Redux actions (`increment` and `decrement`) in `actions.js`.
2. We define a Redux reducer (`counterReducer`) in `reducers.js` to handle state updates.
3. We create a Redux store in `store.js` using `createStore` from Redux, and pass the reducer to it.
4. We provide the Redux store to our React app using the `Provider` component from `react-redux` in `index.js`.
5. Inside our React components, we use hooks like `useSelector` and `useDispatch` from `react-redux` to access the Redux store and dispatch actions.
6. In the `App` component, we display the current count from the Redux store and provide buttons to increment and decrement the count, which dispatch the corresponding actions.




<br>

---
<br>





## 🏆 Client-Server Architecture 
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


## 🎯 Server and Client code for handling POST and GET requests:
`Node.js server` handles `GET and POST` requests using `Express.js`, 
and a `client-side` web page interacts with the server using `Fetch API` to `retrieve and submit data`.

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







## 🎯 Server Side: HTTP Requests and Responses:
The process of an HTTP request and response cycle: 
When a client sends an HTTP request to a server, it includes a request method (GET, POST, etc.), headers, and optional data.
The server processes the request and generates an HTTP response, including a status code, headers, and optional data.
The response is sent back to the client, indicating success or failure of the request.

- [x] **GET Request:**
   - Used to `request data from a server`, data is sent `in the URL`, typically used `for retrieving data`, data is visible in the URL.
   - 
```javascript     
router.get("/", async (req, res) => {
  let collection = await db.collection("records");
  let results = await collection.find({}).toArray();
  res.send(results).status(200);
});
```

- [x] **POST Request:**
   - Used to `submit data to a server`, `data is sent in the request body`, typically used `for submitting data`, data is not visible in the URL.

```javascript
router.post("/", async (req, res) => {
  try {
    let newDocument = {
      name: req.body.name,
      position: req.body.position,
      level: req.body.level,
    };
    let collection = await db.collection("records");
    let result = await collection.insertOne(newDocument);
    res.send(result).status(204);
  } catch (err) {
    console.error(err);
    res.status(500).send("Error adding record");
  }
});
```

## 🎯 Client Side: GET and POST requests using the Fetch API (JavaScript):

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















<br>

---
<br>



# 🏆 Data Structure:
Used to organize and manipulate data efficiently, allowing for optimal storage, retrieval, and manipulation of information.

- [x] Arrays: Ordered collection of elements with constant-time access to individual elements.
- [x] Linked Lists: Collection of nodes where each node points to the next node in the sequence.
- [x] Stacks: LIFO (Last In, First Out) data structure (push and pop).
- [x] Queues: FIFO (First In, First Out) data structure (enqueue and dequeue).
- [x] Trees: Hierarchical data structure consisting of nodes connected by edges, with a root node at the top.
- [x] Graphs: Non-linear data structure consisting of nodes (vertices) and edges connecting them.


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



---



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


<br>

---
<br>





# 🏆 שאלות פיתוח באקאנד - 

## 🎯 API Design and Asynchronous Programming:
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

### 🎯 Asynchronous Programming

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


<br>

---
<br>






# 🏆 Common SQL queries
1. **SELECT statement**: Basic query to retrieve data from a database table.
   ```sql
   SELECT column1, column2 FROM table_name;
   ```

2. **WHERE clause**: Used to filter records based on a specified condition.
   ```sql
   SELECT column1, column2 FROM table_name WHERE condition;
   ```

3. **ORDER BY clause**: Used to sort the result set in ascending or descending order.
   ```sql
   SELECT column1, column2 FROM table_name ORDER BY column1 DESC;
   ```

4. **GROUP BY clause**: Groups rows that have the same values into summary rows, like "find total sales by each product".
   ```sql
   SELECT column1, SUM(column2) FROM table_name GROUP BY column1;
   ```

5. **HAVING clause**: Similar to the WHERE clause, but used with aggregate functions because WHERE cannot be used with aggregate functions.
   ```sql
   SELECT column1, SUM(column2) FROM table_name GROUP BY column1 HAVING SUM(column2) > 1000;
   ```

6. **JOIN**: Used to combine rows from two or more tables based on a related column between them.
   ```sql
   SELECT table1.column1, table2.column2 FROM table1 JOIN table2 ON table1.related_column = table2.related_column;
   ```

7. **INNER JOIN**: Returns rows when there is a match in both tables.
   ```sql
   SELECT table1.column1, table2.column2 FROM table1 INNER JOIN table2 ON table1.related_column = table2.related_column;
   ```

8. **LEFT JOIN**: Returns all rows from the left table and matching rows from the right table.
   ```sql
   SELECT table1.column1, table2.column2 FROM table1 LEFT JOIN table2 ON table1.related_column = table2.related_column;
   ```

9. **RIGHT JOIN**: Returns all rows from the right table and matching rows from the left table.
   ```sql
   SELECT table1.column1, table2.column2 FROM table1 RIGHT JOIN table2 ON table1.related_column = table2.related_column;
   ```

10. **UNION**: Combines the result of two or more SELECT statements, removing duplicate rows.
   ```sql
   SELECT column1 FROM table1
   UNION
   SELECT column1 FROM table2;
   ```


# 🏆 Runtime -
Runtime is a measure of how the time required by an algorithm grows as the size of the input grows.
Some common complexities and what they mean:

1. **O(1) - Constant Time Complexity**:
   - The runtime of the algorithm remains constant regardless of the size of the input.
   - Examples include `accessing a specific element` in an array or performing a `basic arithmetic operation`.

2. **O(log n) - Logarithmic Time Complexity**:
   - The runtime grows `logarithmically` as the size of the input increases.
   - Examples include `binary search` algorithms or certain `tree operations` where the data is repeatedly divided in half.

3. **O(n) - Linear Time Complexity**:
   - The runtime increases `linearly` with the size of the input.
   - Examples include `iterating` through an array or a list.

4. **O(nlogn) - Linearithmic Time Complexity**:
   - The runtime grows in proportion to `n times the logarithm of n`.
   - Examples include some efficient sorting algorithms like `Merge Sort and Quick Sort`.

5. **O(n^2) - Quadratic Time Complexity**:
   - The runtime is `proportional to the square of the size of the input`.
   - Examples include `nested loops` where every element of a collection is compared to every other element.

6. **O(n^k) - Polynomial Time Complexity**:
   - The runtime is proportional to the `input size raised to some constant power`.
   - Examples include algorithms with `nested loops` where the `number of nested loops determines the value of k`.

7. **O(2^n) - Exponential Time Complexity**:
   - The runtime `doubles with each additional input`.
   - Examples include exhaustive search algorithms like the brute-force solution for the `Traveling Salesman Problem`.

8. **O(n!) - Factorial Time Complexity**:
   - The runtime` grows extremely fast` as the factorial of the input size.
   - Examples include brute-force algorithms that generate all permutations or combinations of a set.

When comparing different complexities, such as O(m) and O(m*n), it's essential to consider how each component grows with the input size. In O(m), the runtime grows linearly with the size of `m`, whereas in O(m*n), it grows linearly with both `m` and `n`. So, if `m` and `n` are independent of each other, the overall complexity would be O(m * n). However, if one is much larger or smaller than the other, we may only consider the dominant term.
