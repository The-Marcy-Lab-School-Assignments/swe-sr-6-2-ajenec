# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

Imagine you are giving a brief lesson on Recursion to a relatively new programmer. In your lesson make sure to include the following:

- A formal definition of recursion (feel free to quote an official source like MDN)
- An example in code.
- An explanation of the code example.
- An explanation of the kinds of functions that are best solved using recursion.

### Response 1

## Prompt 2

Imagine you are giving a brief lesson on the Tree data structure to a relatively new programmer. In your lesson make sure to include the following:

- A formal definition of a Tree (feel free to quote an official source like MDN)
- Definitions for key terms like **root**, **leaf**, **depth**, and **height** as they relate to Trees
- An example in code.
- An explanation of the code example.

### Response 2

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

now lets see the same function written recursivly:

```js
function factorialRecursive(n) {
	if (n === 0 || n === 1) {
		return 1;
	}
	return n * factorialRecursive(n - 1);
}

console.log(factorialRecursive(5)); // Output: 120
```

In this example both functions have the same time complexity, but the recursive approach has a space complexity of O(n) due to the call stack. In terms of readability using a recursive approach is less explicit and more elegant for mathematical problems. Deciding whether to use an iterative or recursive approach comes down to the nature of the problem. Things such as tree traversal, or backtracking can be efficiently/readable when done recursivly, but overall an iterative approach is often better for performance and avoiding stack issues.

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

The first approach (Inorder Traversal) starts on the left subtree then makes its way to the root node after exploring all the left subtrees then once at the root it visits the right subtree. something like : D-B-E-A-C-F
The second approach (preorder) starts at the root node, visits the left subtree from left to right, then visits the right subtree: A-B-D-E-C-F
Finally the postorder approach. It order starts goes from the left subtree to the right subtree then finally to the root node. Heres an example of the preorder recursivly:

```js
function preorderTraversal(node) {
	if (!node) return;
	console.log(node.value);
	preorderTraversal(node.left);
	preorderTraversal(node.right);
}

preorderTraversal(tree); // Output: A B D E C F
```

typically recursive solutions are cleaner and easier to understand as mentioned before for tree traversal because they follow the tree structure. doing this iteravly is possible but more complex.
