# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

Imagine you are giving a brief lesson on Recursion to a relatively new programmer. In your lesson make sure to include the following:

- A formal definition of recursion (feel free to quote an official source like MDN)
- An example in code.
- An explanation of the code example.
- An explanation of the kinds of functions that are best solved using recursion.

### Response 1

#### What is Recursion?

_MDN Web Docs_ states that **recursion** is, "The act of a function calling itself, **recursion** is used to solve problems that contain smaller **sub-problems**. A **recursive function** can receive two inputs: a **base case (ends recursion)** or a **recursive case (resumes recursion)**." In simple terms **recursion** is when a function calls itself until it reaches a **base case** (a condition).

```js
let count = 0;
const hi = () => {
  count++; // count Increments by 1 each time its called
  console.log(count); // logs current number

  //Checks if count is greater than 2 (BASE CASE)
  if (count > 2) {
    return; // Stops the function if it is
  } else {
    hi(); // If count <= 2, it calls itself (This is the RECURSION)
  }
};
```

- The `hi` function increments the `count` variable by 1 and logs the current value each time it's called.
- The **base case** for the recursion is when **`count` > 2**. If this is true, the function stops calling itself and returns the desired output
- If **`count` <= 2**, the function will call itself and continue the process.

You would use recursion for **Tree Traversal**, **Fibonacci Sequence**, and **Factorial Calculation**.

## Prompt 2

Imagine you are giving a brief lesson on the Tree data structure to a relatively new programmer. In your lesson make sure to include the following:

- A formal definition of a Tree (feel free to quote an official source like MDN)
- Definitions for key terms like **root**, **leaf**, **depth**, and **height** as they relate to Trees
- An example in code.
- An explanation of the code example.

### Response 2

#### What is a Tree?

A `Tree` is a **data structure** that arranges data in a **hierarchical** manner, resembling an upside-down tree. They are a type of graph and are **naturally directional and acyclic**. `Trees` are comprised of **nodes/entities** lined through edges, to form branches. In simple terms, a `Tree` is like a family tree or file system. It starts with the main item, and branches off into smaller items.

**Key terms for `Trees`:**

- **Root:** The top node of a tree, it has no parent.
- **Edge:** Arrows/Lines that connect nodes in a tree.
- **Children:** Nodes linked by a parent node.
- **Parent:** A node that links to another node.
- **Sibling:** Nodes that share the same parent.
- **Leaf Nodes:** Nodes at the end of branches with no children.
- **Internal Nodes:** Nodes that have at least one child.
- **Depth:** The distance between the root node and a given node.
- **Height:** The length of the longest path from a node to a leaf node; maximum depth.

Here's a simple example of `Trees` in Javascript:

```js
// Create Tree
class TreeNode {
  constructor(data) {
    this.data = data;
    this.leftChild = null;
    this.rightChild = null;
  }
}

// Create Nodes
const root = new TreeNode("Root");
const left = new TreeNode("Left Child");
const right = new TreeNode("Right Child");

// Add Nodes to form the Tree
root.leftChild = left;
root.rightChild = right;
```

1. The `TreeNode` class is created with:

   - `data` which is the value stored in the node.
   - `leftChild` and `rightChild` are pointers to its **child nodes**.

2. Created the root node and two child nodes.
3. Then linked the child nodes to the root with `root.leftChild` and `root.rightChild`, to form this structure:

```
        Root
       /    \
     Left  Right
```

- The root node is "Root".
- The leaf nodes are "Left" and "Right".
- The depth of "Left" is 1 because there isn't any data after it.
- The height of the tree is 1.

## Prompt 3

Any iterative function can be written recursively. Provide an example of an iterative function and the same function written recursively. Then, explain the benefits and/or drawbacks of each approach.

### Response 3

Heres an iterative function using a standard for loop:

```js
function factorialIterative(n) {
  let result = 1;
  for (let i = 2; i <= n; i++) {
    result *= i;
  }
  return result;
}

console.log(factorialIterative(5)); // Output: 120
```

now lets see the same function written recursively:

```js
function factorialRecursive(n) {
  if (n === 0 || n === 1) {
    return 1;
  }
  return n * factorialRecursive(n - 1);
}

console.log(factorialRecursive(5)); // Output: 120
```

In this example both functions have the same time complexity, but the recursive approach has a space complexity of O(n) due to the call stack. In terms of readability using a recursive approach is less explicit and more elegant for mathematical problems. Deciding whether to use an iterative or recursive approach comes down to the nature of the problem. Things such as tree traversal, or backtracking can be efficiently/readable when done recursively, but overall an iterative approach is often better for performance and avoiding stack issues.

## Prompt 4

Depth-first-search is an algorithm of traversing through a tree that explores as far as possible along a single branch before backtracking and exploring other branches. The three approaches for depth-first-search are "inorder", "preorder", and "postorder".

Using this tree as an example, explain the differences between these three approaches, providing implementations of each (recursive or iterative, its up to you but one of them is definitely cleaner).

```
    A
   / \
  B   C
 / \   \
D   E   F
```

### Response 4

The first approach (Inorder Traversal) starts on the left subtree and then makes its way to the root node after exploring all the left subtrees then once at the root it visits the right subtree. Something like: D-B-E-A-C-F
The second approach (preorder) starts at the root node, visits the left subtree from left to right, then visits the right subtree: A-B-D-E-C-F
Finally the postorder approach. The order starts from the left subtree to the right subtree, and then finally, it goes to the root node. Here's an example of the preorder recursively:

```js
function preorderTraversal(node) {
  if (!node) return;
  console.log(node.value);
  preorderTraversal(node.left);
  preorderTraversal(node.right);
}

preorderTraversal(tree); // Output: A B D E C F
```
