# Yiye's Cheatsheet on Leetcode programming problems



## Two Pointers

- Termination criteria (in general): ```while left <= right```

- Skip a block of repeating numbers in a sorted array for de-duplication (e.g. [LC15: 3sum](https://leetcode.com/problems/3sum/submissions/1492068257/)):

  ```python
  i = 0
  while i < len(nums):
    # skip repeated values by continue the iteration
    # NOTE: condition i>0 to avoid
    # skipping the first repeating number block
    if i > 0 and nums[i] == nums[i-1]:
      i += 1
      continue
    # do whatever in the iteration
    print(i)
    # NOTE: still need to increment the pointer here
    # to get out of the first element of each block
    i += 1
  ```

  



## Binary Tree

- **Depth-first search** (pre-order, in-order, post-order)

  - *Recursive method*: simple.
  - *Iterative Method*:
    - *Difficulty*: the visiting order and processing order is different.
    - *Solution*: Label when a node should be processed, by appending a NULL in the front!

- **Breadth-first search**

  - Iterative method via queue
    - If need to keep track of **levels**, create a separate queue for the levels.

- **Essential properties / definitions (Enabling recursive)**

  - The outcomes of the depth-first search algorithms are recursive. (E.g. [LC106: Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)) :

    ```
    preorder(root) = [root, preorder(root.left), preorder(root.right)]
    inorder(root) = [inorder(root.left), root, inorder(root.right)]
    postorder(root) = [postorder(root.left), postorder(root.right), root]
    ```

  - 