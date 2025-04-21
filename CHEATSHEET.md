# Yiye's Cheatsheet on Leetcode programming problems



# Data structure

## Binary Tree Traverse

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

### Binary Search Tree

Property: 

- In-order traverse gives a monotonically increasing array.



## Priority Queue





# Algorithms

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



- 



## BackTrack v.s. Greedy v.s. Dynamic Programming

- **Backtrack** is just simply brutal force - where all choices are tried - that is implementable.
  
  - It is a **depth-first search tree**
  - 适用的问题可以抽象成：**给定action sequence, 问所有可能的state sequences**。
  - backtrack模板(**recursive探索解决问题步骤 + iteration尝试所有actions**)：
  
    - ```python
      def main_function()
      	backtracking(起始位置)
      
      def backtracking(参数) {
          if (终止条件) {
              存放结果;
              return;
          }
      
          for (当前位置的action candidates（树中当前节点的children）) {
              执行action，或者处理节点;
              backtracking(下一个位置); // 递归
              回溯，撤销处理结果
          }
      }
      ```
      
    - 函数参数帮助（1）选择当前action; （2）遍历当前action的outcomes; （3）存储最终results和当前的intermediate results
  
    - 注意**回溯：撤销处理结果**：防止intermediate results互相干扰
  
  - 可能可以剪枝提高效率
- **Dynamic Programming**
  
  - Suitable problems: 
    - **overlapping subproblems**: 需要重复解决一个子问题。e.g. Fabonacci
    -  **optimal substructure**: 全局最优解决可以由子问题最优解构成。e.g. Shortest path
  
- Backtrack complexity is exponential. The other two can be logarithmic or polynomial.





# 值得回顾

- [310M: Minimum Height Tree](https://leetcode.com/problems/minimum-height-trees/description/)
  - Check if there is a loop in the graph
  - Similar problems:
    - [207: Course Schedule](https://leetcode.com/problems/course-schedule/description/?envType=company&envId=tiktok&favoriteSlug=tiktok-thirty-days)
- [542M: 01 Matrix](https://leetcode.com/problems/01-matrix/description/)
  - Multi-source BFS
  - Similar problems:
    - [1765: Map of Highest Peak](https://leetcode.com/problems/map-of-highest-peak/)



## 巧思

- [300M. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
  - A smart DP approach that enables binary search, reducing complexity from $O(N^2)$ to $O(NlogN)$

- [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
  - 用数组翻转解决数组的移动
  - 注意移动长度小于数组长度的特殊情况



# 没完全理解

- [1382 balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/description/)
  - InOrder traverse + reconstruct能理解，但是rotation方法最后一步里如何决定left rotate次数没有理解

