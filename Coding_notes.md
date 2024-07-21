# Coding Notes
> Author : Aaron Augustine 

## Table of Contents : 
1. [Data Structures Leetcode](#dsa-questions)
2. [Python Study course](#python-study-course)
4. [Pandas 15Q's Course](https://leetcode.com/studyplan/introduction-to-pandas/)
5. [Java Functions](#java-functions)
6. [Python Functions](#python-functions)


# DSA Questions

## Table of Contents DSA
1. [BST to Greater Sum Tree](#bst-to-greater-sum-tree )
2. [Balanced Binary Search Tree](#balanced-binary-search-tree)
3. [Two Sum problem](#two-sum)
4. [Center of Star Graph](#center-of-star-graph)
5. [Longest Substring](#longest-substring)
	-	[Sliding Window Technique](#sliding-window-technique)
6. [Median of two sorted arrays](#median-of-two-sorted-arrays)
7. [All Ancestors of a Node in a Directed Acyclic Graph](#all-ancestors-of-a-node-in-a-directed-acyclic-graph)
8. [Remove Max Number of Edges to Keep Graph Fully Traversable](#remove-max-number-of-edges-to-keep-graph-fully-traversable)
9. [Longest Palindromic Substring](#longest-palindromic-substring)
10. [Three Consecutive Odds](#three-consecutive-odds) 
11. [Zigzag Conversion](#zigzag-conversion) 
12. [Intersection of Two Arrays 2](#intersection-of-two-arrays-2) 
13. [Score of a string](#score-of-a-string) 
	- [Math.abs() & charAt() functions](#new-things-learnt)
14. [No repetitions](#no-repetitions)
15. [Minimum Difference Between Largest and Smallest Value in Three Moves](#minimum-difference-between-largest-and-smallest-value-in-three-moves)
16. [Reverse Integer](#reverse-integer)
17. [Merge Nodes in Between Zeros](#merge-nodes-in-between-zeros)
18. [Find the Minimum and Maximum Number of Nodes Between Critical Points](#find-the-minimum-and-maximum-number-of-nodes-between-critical-points)
19. [Pass the Pillow](#pass-the-pillow)
20. [Water Bottles](#water-bottles)
21. [String to Integer](#string-to-integer)
22. [Find the Winner of the circular game](#find-the-winner-of-the-circular-game)
23. [Richest Customer Wealth](#richest-customer-wealth)
24. [Fizz Buzz](#fizz-buzz)
25. [Palindrome Number](#palindrome-number)
26. [Average Waiting Time](#average-waiting-time)
27. [Crawler Log Folder](#crawler-log-folder)
28. [Reverse Substrings between each pair of Parentheses](#reverse-substrings-between-each-pair-of-parentheses)
29. [Maximum Score from Removing substrings](#maximum-score-from-removing-substrings)
30. [Robot Collisions](#robot-collisions)
31. [Roman to Integer](#roman-to-integer)
32. [Integer to Roman](#integer-to-roman)
33. [Regular Expression Matching](#regular-expression-matching)
34. :red_circle:[Container with Most Water](#container-with-most-water)
35. [Longest Common Prefix](#longest-common-prefix)
36. :red_circle:[Smallest Missing Integer Greater Than Sequential Prefix Sum](#smallest-missing-integer-greater-than-sequential-prefix-sum)
37. [Number of Atoms](#number-of-atoms)
38. [Create Binary Tree From Descriptions](#create-binary-tree-from-descriptions)
39. [Step-By-Step Directions From a Binary Tree Node to Another](#step-by-step-directions-from-a-binary-tree-node-to-another)
40. [3Sum](#three-sum)
41. [Letter Combinations of a Phone Number](#letter-combinations-of-a-phone-number)
42. [Valid Parenthesis](#valid-parenthesis)
	-	[if condition writing](#if-condition-writing)
	-	[New shortcut for **bold** and *italicized* text](#new-shortcut-discovered)
43. :rocket: [Set Matrix Zeroes](#set-matrix-zeroes)
44. [Delete Nodes And Return Forest](#delete-nodes-and-return-forest)
45. :red_circle:[Number of Good Leaf Nodes](#number-of-good-leaf-nodes)
46. :star: [Lucky Numbers in a Matrix](#lucky-numbers-in-a-matrix)
47. :rocket:[Pascals Triangle](#pascals-triangle)
48. :rocket::red_circle:[Next Permutation](#next-permutation)
49. :red_circle:[Find Valid Matrix Given Row and Column Sums](#find-valid-matrix-given-row-and-column-sums)
50. [Template for solving](#template-for-solving)


<hr>

> Day : Tuesday, 25th June 2024

## BST to Greater Sum Tree

> Tags : Binary Search Tree, Greater Tree, Tree Nodes.

[**Question**](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/?envType=daily-question&envId=2024-06-25) : 

Given the  `root`  of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.

As a reminder, a  _binary search tree_  is a tree that satisfies these constraints:

-   The left subtree of a node contains only nodes with keys  **less than**  the node's key.
-   The right subtree of a node contains only nodes with keys  **greater than**  the node's key.
-   Both the left and right subtrees must also be binary search trees.

[**Solution**](https://chatgpt.com/share/b88a1a8a-d231-4faa-bd9f-7ff105bd0595)

The thought process here is  : 
- I undertsood what to do. Each key has to be replace with the sum of the keys greater than it and then it has to be made into the new tree.

### Algorithm : 
1. Define a new array to store the output values of the greater keys.
2. Create a for loop to iterate through the nodes
3. Then create a second for loop to iterate through that same array with an additional *If* statement.
4. The if condition within that will use the value of *i* to check for values greater than *i* [ Current key ]
5. Sum them up and then outside the for loop you will put the value into the new array
6. Additionally for null values you need to make sure they are transplanted into the new array as is so create the if condition for that first, to prevent checking of values.

### Things to figure out : 
```python 
# Definition for a binary tree node.
# class TreeNode:
# def __init__(self, val=0, left=None, right=None):
# self.val = val
# self.left = left
# self.right = right
class  Solution:
	def  bstToGst(self, root: TreeNode) -> TreeNode:

```

1. How to accept the values passed in the function ?
2. Since it is inorder form of traversing we need to work on that too and figure out how it is to be done

### Python Code : 
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def bstToGst(self, root: TreeNode) -> TreeNode:
        self.cumulative_sum = 0  # Initialize the cumulative sum to 0

        # Helper function for reverse in-order traversal
        def reverse_in_order_traversal(node):
            if not node:
                return
            reverse_in_order_traversal(node.right)
            self.cumulative_sum += node.val
            node.val = self.cumulative_sum
            reverse_in_order_traversal(node.left)
        
        # Start the traversal from the root
        reverse_in_order_traversal(root)
        
        # Helper function to print the tree in level order
        def print_tree_level_order(root):
            if not root:
                return
            from collections import deque
            q = deque([root])
            while q:
                node = q.popleft()
                if node:
                    print(node.val, end=" ")
                    q.append(node.left)
                    q.append(node.right)
                else:
                    print("null", end=" ")
            print()

        # Print the tree for verification
        print_tree_level_order(root)
        
        return root
```
- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Wednesday, 26th June 2024

## Balanced Binary Search Tree

> Tags : Binary Search Tree, 
[**Question**](https://leetcode.com/problems/balance-a-binary-search-tree/?envType=daily-question&envId=2024-06-26) :
Given the  `root`  of a binary search tree, return  _a  **balanced**  binary search tree with the same node values_. If there is more than one answer, return  **any of them**.

A binary search tree is  **balanced**  if the depth of the two subtrees of every node never differs by more than  `1`.

[**Solution**](https://chatgpt.com/share/c2955429-d2fa-49ca-b968-82559bfda610) : 
So since the depth of the two subtrees can't differ by more than one, that means it has to be wide and can't be going down in a single file like it was initially

![](https://assets.leetcode.com/uploads/2021/08/10/balance1-tree.jpg)

**Input:** root = [1,null,2,null,3,null,4,null,null]
**Output:** [2,1,3,null,null,null,4]
**Explanation:** This is not the only correct answer, [3,1,4,null,2] is also correct.

### Algorithm 
1. The idea of a BST is that the number to the left of the root/node is lesser than the node and the number to the right is greater.
2. So to solve this we will perform an inorder traversal of the BST and get a sorted list
	-	Over here we check if the node exists, else we return an empty list.
	-	Then we traverse the left node and append it's value ( left, root, right )
	-	We recursively solve this and then we 
3. Then we will use the sorted list to build a BST
4. Finally we will create a function for BFS traversal

### Things to figure out
1. How to balance it after the inorder traversal
2. How to perform inorder traversal ( recursively

### Python Code : 
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def balanceBST(self, root: TreeNode) -> TreeNode:
        def in_order_traversal(node):
            # Perform in-order traversal to collect the node values in sorted order
            if not node:
                return []
            return in_order_traversal(node.left) + [node.val] + in_order_traversal(node.right)

        def sorted_array_to_bst(arr, start, end):
            # Convert sorted array to balanced BST
            if start > end:
                return None
            mid = (start + end) // 2
            node = TreeNode(arr[mid])
            node.left = sorted_array_to_bst(arr, start, mid - 1)
            node.right = sorted_array_to_bst(arr, mid + 1, end)
            return node

        # Step 1: Get sorted array from BST
        sorted_values = in_order_traversal(root)
        
        # Step 2: Convert sorted array to balanced BST
        return sorted_array_to_bst(sorted_values, 0, len(sorted_values) - 1)

    def bfs_traversal(self, root):
        if not root:
            return []
        result, queue = [], [root]
        while queue:
            node = queue.pop(0)
            if node:
                result.append(node.val)
                queue.append(node.left)
                queue.append(node.right)
            else:
                result.append('null')
        # Remove trailing 'null's to match the expected output format
        while result and result[-1] == 'null':
            result.pop()
        return result
```
### Python code ( recoded by me )
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def balanceBST(self, root: TreeNode) -> TreeNode:
        def inorder_traversal(node):
            result = []

            def traverse(node):
                if not node : 
                    return 
                # in Inorder traversal we travel to the left most node and then the root and then right
                traverse(node.left)
                result.append(node.val)
                traverse(node.right)
            traverse(node)
            return result
        
        def sorted_array(arr, start, end):
            if start > end :
                return None
            mid_val = (start + end) // 2
            node = TreeNode(arr[mid_val])
            #because in Inorder the middle value is always the root node
            node.left = sorted_array(arr, start, mid_val-1)
            node.right = sorted_array(arr, mid_val + 1, end)
            return node

        sorted_values = inorder_traversal(root)
        return sorted_array(sorted_values, 0, len(sorted_values)-1)

        def bfs_traversal(self, root):
            if not root:
                return []
            result, queue = [], [root]
            while queue : 
                node = queue.pop(0)
                if node : 
                    result.append(node.val)
                    queue.append(node.left)
                    queue.append(node.right)
                else : 
                    result.append('null')
            
            #this statement is to remove the trailing nulls to bring it to the required format.
            while result and result[-1] == 'null':
                result.pop()
            return result

```

### Output 
```
root  = [1,null,2,null,3,null,4]
Output = [2,1,3,null,null,null,4]
```
- [Return to TOC](#table-of-contents-dsa)

<hr>

## Solving Binary Tree Problems with recursion

[Solve any binary tree coding problem](https://www.youtube.com/watch?v=s2Yyk3qdy3o&ab_channel=Insidecode) 

## Two-Sum

[**Question**](https://leetcode.com/problems/two-sum/) : 
Given an array of integers  `nums` and an integer  `target`, return  _indices of the two numbers such that they add up to  `target`_.

You may assume that each input would have  **_exactly_  one solution**, and you may not use the  _same_  element twice.

You can return the answer in any order.
**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

[**Solution**](https://chatgpt.com/share/16662c91-43ac-4b4d-b965-9529e4c19ea8):
The idea here is to check for which two values can add up to the given target variable

### Algorithm : 
1. First we iterate through the list
2. Along with that we make a sub iteration ( for loop ) to check if the addition of the current variable with the subsequent ones will provide the required answer 

### Python Code ( Coded by me ) :kissing_heart:
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # The information writte after the ':' defines what the value is expected to be
        result = []

        for i in range(0, len(nums)) :
            for j in range (i+1,len(nums)):
                if nums[i]+nums[j] == target :
                    result.append(i)
                    result.append(j)
                
        return result
```

### Python Code ( by chatgpt ) :unamused:
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        complement_map = {}

        for i, num in enumerate(nums):
            complement = target - num

            if complement in complement_map:
                return [complement_map[complement], i]
            complement_map[num] = i

        return []
```


- [Return to TOC](#table-of-contents-dsa)

<hr>

## Two Link Lists 

[**Question**](https://leetcode.com/problems/add-two-numbers/) : 
You are given two  **non-empty**  linked lists representing two non-negative integers. The digits are stored in  **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

![](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)

**Input:** l1 = [2,4,3], l2 = [5,6,4]
**Output:** [7,0,8]
**Explanation:** 342 + 465 = 807.

[**Solution**]() : 
The idea ( which I miunderstood ) is that we can simply just add the current elements of the two linked lists while iterating and make sure we keep track of the carry over : 

### Python Code :unamused:
```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        carry = 0
        dummy = ListNode()
        current = dummy

        while l1 or l2 or carry:
            sum = (l1.val if l1 else 0) + (l2.val if l2 else 0) + carry
            carry = sum // 10
            current.next = ListNode(sum % 10)
            current = current.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None

        return dummy.next

```

### Output 
```
Input
l1 =[2,4,3]
l2 = [5,6,4]
Output [7,0,8]
Expected [7,0,8]
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Thursday, 27th June 2024

## Center of Star Graph

[**Question**](https://leetcode.com/problems/find-center-of-star-graph/?envType=daily-question&envId=2024-06-27):
There is an undirected  **star**  graph consisting of  `n`  nodes labeled from  `1`  to  `n`. A star graph is a graph where there is one  **center**  node and  **exactly**  `n - 1`  edges that connect the center node with every other node.

You are given a 2D integer array  `edges`  where each  `edges[i] = [ui, vi]`  indicates that there is an edge between the nodes  `ui`  and  `vi`. Return the center of the given star graph.

Input: edges = [[1,2],[2,3],[4,2]]
Output: 2
Explanation: As shown in the figure above, node 2 is connected to every other node, so 2 is the center.

[**Solution**](https://chatgpt.com/share/8442c8b5-b264-49d3-9a9c-a27ab7063a94):
The main idea here is that one edge will be linked to almost every other edge so we just need to check for that common edge

### Algorithm 
1. First we take the list of lists ( or basically a 2 dimensional array ) and then we check the first two edges
2. An if conition should suffice where  we check if in [a,b] & [c,a] : `a == c` or `a == a`.
3. In the else condition we can pass b if the above condition isn't met

### Python Code :heart_eyes:
```python
class Solution:
    def findCenter(self, edges: List[List[int]]) -> int:
        # Check the first two edges
        if edges[0][0] == edges[1][0] or edges[0][0] == edges[1][1]:
            return edges[0][0]
        else:
            return edges[0][1]


```

### Output 
```
Input edges = [[1,2],[2,3],[4,2]]
Output 
2
Expected
2
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## 
Longest Substring

[***Question**](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/) : 
Given a string  `s`, find the length of the  **longest substring** without repeating characters.

> Example 1

**Input:** s = "abcabcbb"
**Output:** 3
**Explanation:** The answer is "abc", with the length of 3.

> Example 2 

**Input:** s = "pwwkew"
**Output:** 3
**Explanation:** The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

[**Solution**]()
How do we figure out the longest ? By checking for repetition. So as long as unique characters are found we can add the count to the integer variable and then return the int value the moment a string has been repeated.

> This problem has to be solved using the [Sliding Window](https://www.youtube.com/watch?v=jhW7VwP2Djw&ab_channel=TAPACADEMY) technique. 

### Sliding Window Technique
1. When the size isn't defined or when it is defined we can use this technique. 

### Python Code 
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        char_set = set()
        left = 0
        max_length = 0
        
        for right in range(len(s)):
            while s[right] in char_set:
                char_set.remove(s[left])
                left += 1
            char_set.add(s[right])
            max_length = max(max_length, right - left + 1)
        
        return max_length

```

### Output 
```
Input s = "abcabcbb"
Output
3
Expected
3

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Friday, 28th June 2024

## Median of two sorted arrays

[**Question**](https://leetcode.com/problems/median-of-two-sorted-arrays/description/) : 
Given two sorted arrays  `nums1`  and  `nums2`  of size  `m`  and  `n`  respectively, return  **the median**  of the two sorted arrays.

The overall run time complexity should be  `O(log (m+n))`.

**Example 1:**

**Input:** nums1 = [1,3], nums2 = [2]
**Output:** 2.00000
**Explanation:** merged array = [1,2,3] and median is 2.

[**Solution**](https://chatgpt.com/share/83b3f39d-4a06-4737-9ca8-b6a9b24b5e17) : 
For this solution we can actually calculate the individual medians of the two, then use weighted mean concept to caculate it for the two combined arrays.

### Algortihm : 
1. First we combine the two arrays and then we sort them 
2. 

### Python Code 
```python 
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        merged = sorted(nums1 + nums2)
        length = len(merged)

        if length % 2 == 1 :
            return merged[length // 2]
        else : 
            mid1 =  length // 2
            mid2 = mid1 - 1
            return( merged[mid1] + merged[mid2])/2


```

### Output 
```
nums1 = [1,3]
nums2 = [2]
Output
2.00000
Expected
2.00000
```

- [Return to TOC](#table-of-contents-dsa)

<hr>


## Maximum total importance of Roads

[**Question**](https://leetcode.com/problems/maximum-total-importance-of-roads/?envType=daily-question&envId=2024-06-28) : 
You are given an integer  `n`  denoting the number of cities in a country. The cities are numbered from  `0`  to  `n - 1`.

You are also given a 2D integer array  `roads`  where  `roads[i] = [ai, bi]`  denotes that there exists a  **bidirectional**  road connecting cities  `ai`  and  `bi`.

You need to assign each city with an integer value from  `1`  to  `n`, where each value can only be used  **once**. The  **importance**  of a road is then defined as the  **sum**  of the values of the two cities it connects.

Return  _the  **maximum total importance**  of all roads possible after assigning the values optimally._

**Input:** n = 5, roads = [[0,1],[1,2],[2,3],[0,2],[1,3],[2,4]]
**Output:** 43
**Explanation:** The figure above shows the country and the assigned values of [2,4,5,3,1].
- The road (0,1) has an importance of 2 + 4 = 6.
- The road (1,2) has an importance of 4 + 5 = 9.
- The road (2,3) has an importance of 5 + 3 = 8.
- The road (0,2) has an importance of 2 + 5 = 7.
- The road (1,3) has an importance of 4 + 3 = 7.
- The road (2,4) has an importance of 5 + 1 = 6.
The total importance of all roads is 6 + 9 + 8 + 7 + 7 + 6 = 43.
It can be shown that we cannot obtain a greater total importance than 43.

[**Solution**](https://chatgpt.com/share/95d1b2c2-0d65-4ef1-9952-43aca4991d6f) : 

### Python Code : 
```python 
class Solution:
    def maximumImportance(self, n: int, roads: List[List[int]]) -> int:
        # Step 1: Calculate the degree of each city
        degree = [0] * n
        for a, b in roads:
            degree[a] += 1
            degree[b] += 1
        
        # Step 2: Sort cities by degree in descending order
        sorted_cities = sorted(range(n), key=lambda x: degree[x], reverse=True)
        
        # Step 3: Assign values from n to 1 based on sorted degrees
        values = [0] * n
        for i in range(n):
            values[sorted_cities[i]] = n - i
        
        # Step 4: Calculate the total importance of all roads
        total_importance = 0
        for a, b in roads:
            total_importance += values[a] + values[b]
        
        return total_importance


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Saturday, 29th June 2024

## All Ancestors of a Node in a Directed Acyclic Graph

[**Question**](https://leetcode.com/problems/all-ancestors-of-a-node-in-a-directed-acyclic-graph/description/?envType=daily-question&envId=2024-06-29) : 
You are given a positive integer  `n`  representing the number of nodes of a  **Directed Acyclic Graph**  (DAG). The nodes are numbered from  `0`  to  `n - 1`  (**inclusive**).

You are also given a 2D integer array  `edges`, where  `edges[i] = [fromi, toi]`  denotes that there is a  **unidirectional**  edge from  `fromi`  to  `toi`  in the graph.

Return  _a list_  `answer`_, where_ `answer[i]` _is the  **list of ancestors**  of the_  `ith`  _node, sorted in  **ascending order**_.

A node  `u`  is an  **ancestor**  of another node  `v`  if  `u`  can reach  `v`  via a set of edges.

**Input:** n = 8, edgeList = [[0,3],[0,4],[1,3],[2,4],[2,7],[3,5],[3,6],[3,7],[4,6]]
**Output:** [[],[],[],[0,1],[0,2],[0,1,3],[0,1,2,3,4],[0,1,2,3]]
**Explanation:**
The above diagram represents the input graph.
- Nodes 0, 1, and 2 do not have any ancestors.
- Node 3 has two ancestors 0 and 1.
- Node 4 has two ancestors 0 and 2.
- Node 5 has three ancestors 0, 1, and 3.
- Node 6 has five ancestors 0, 1, 2, 3, and 4.
- Node 7 has four ancestors 0, 1, 2, and 3.

[**Solution**](https://chatgpt.com/share/ed9fb49e-4dcd-4ba4-bc35-66ba6e9aa34a) : 

### Python Code
```python 
from collections import defaultdict, deque

class Solution:
    def getAncestors(self, n: int, edges: List[List[int]]) -> List[List[int]]:
        # Step 1: Represent the graph using adjacency lists
        graph = defaultdict(list)
        in_degree = [0] * n
        
        for u, v in edges:
            graph[u].append(v)
            in_degree[v] += 1
        
        # Step 2: Topological sort using Kahn's algorithm
        topo_sort = []
        queue = deque([i for i in range(n) if in_degree[i] == 0])
        
        while queue:
            node = queue.popleft()
            topo_sort.append(node)
            for neighbor in graph[node]:
                in_degree[neighbor] -= 1
                if in_degree[neighbor] == 0:
                    queue.append(neighbor)
        
        # Step 3: Find ancestors
        ancestors = [set() for _ in range(n)]
        
        for node in topo_sort:
            for neighbor in graph[node]:
                ancestors[neighbor].add(node)
                ancestors[neighbor].update(ancestors[node])
        
        # Step 4: Convert sets to sorted lists
        result = [sorted(list(ancestor_set)) for ancestor_set in ancestors]
        
        return result

# Example usage:
n = 8
edges = [[0, 3], [0, 4], [1, 3], [2, 4], [2, 7], [3, 5], [3, 6], [3, 7], [4, 6]]
solution = Solution()
print(solution.getAncestors(n, edges))


```

### Output
```
Input
n = 8
edges = [[0,3],[0,4],[1,3],[2,4],[2,7],[3,5],[3,6],[3,7],[4,6]]
Output
[[],[],[],[0,1],[0,2],[0,1,3],[0,1,2,3,4],[0,1,2,3]]
Expected
[[],[],[],[0,1],[0,2],[0,1,3],[0,1,2,3,4],[0,1,2,3]]
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Sunday, 30th June 2024

## Remove Max Number of Edges to Keep Graph Fully Traversable

[**Question**](https://leetcode.com/problems/remove-max-number-of-edges-to-keep-graph-fully-traversable/description/?envType=daily-question&envId=2024-06-30):

Alice and Bob have an undirected graph of  `n`  nodes and three types of edges:

-   Type 1: Can be traversed by Alice only.
-   Type 2: Can be traversed by Bob only.
-   Type 3: Can be traversed by both Alice and Bob.

Given an array  `edges`  where  `edges[i] = [typei, ui, vi]`  represents a bidirectional edge of type  `typei`  between nodes  `ui`  and  `vi`, find the maximum number of edges you can remove so that after removing the edges, the graph can still be fully traversed by both Alice and Bob. The graph is fully traversed by Alice and Bob if starting from any node, they can reach all other nodes.

Return  _the maximum number of edges you can remove, or return_  `-1`  _if Alice and Bob cannot fully traverse the graph._

![](https://assets.leetcode.com/uploads/2020/08/19/ex1.png)

**Input:** n = 4, edges = [[3,1,2],[3,2,3],[1,1,3],[1,2,4],[1,1,2],[2,3,4]]
**Output:** 2
**Explanation:** If we remove the 2 edges [1,1,2] and [1,1,3]. The graph will still be fully traversable by Alice and Bob. Removing any additional edge will not make it so. So the maximum number of edges we can remove is 2.

[**Solution**](https://chatgpt.com/share/d5c70285-3c5c-4e3c-bb76-a492f099128e) : 
The idea here is to remove n number of edges so that the edge type where both Alice and Bob can traverse is connecting all possible edges

The idea is that we check for any edge which has the type 3 connecting 2 vertices, and if the same combination of edges has any other type, it can be removed. Similarly if any edge doesn't have a type 3 then it must have both a type 1 and 2 connecting it or else it'll be non traversable.

### Things to know
**Union Find**



### Java Code 
```java

class Solution {
    public int maxNumEdgesToRemove(int n, int[][] edges) {
        UnionFind aliceUnionFind = new UnionFind(n);
        UnionFind bobUnionFind = new UnionFind(n);
        int removedEdges = 0;

        // Step 1: Process type 3 edges first
        for (int[] edge : edges) {
            if (edge[0] == 3) {
                boolean aliceMerged = aliceUnionFind.union(edge[1], edge[2]);
                boolean bobMerged = bobUnionFind.union(edge[1], edge[2]);
                if (!aliceMerged && !bobMerged) {
                    removedEdges++;
                }
            }
        }

        // Step 2: Process type 1 edges (Alice only)
        for (int[] edge : edges) {
            if (edge[0] == 1) {
                boolean merged = aliceUnionFind.union(edge[1], edge[2]);
                if (!merged) {
                    removedEdges++;
                }
            }
        }

        // Step 3: Process type 2 edges (Bob only)
        for (int[] edge : edges) {
            if (edge[0] == 2) {
                boolean merged = bobUnionFind.union(edge[1], edge[2]);
                if (!merged) {
                    removedEdges++;
                }
            }
        }

        // Step 4: Check if both Alice and Bob can fully traverse the graph
        if (aliceUnionFind.isFullyConnected() && bobUnionFind.isFullyConnected()) {
            return removedEdges;
        } else {
            return -1;
        }
    }
}

class UnionFind {
    private int[] parent;
    private int[] rank;
    private int componentCount;

    public UnionFind(int n) {
        parent = new int[n + 1];
        rank = new int[n + 1];
        componentCount = n;
        for (int i = 1; i <= n; i++) {
            parent[i] = i;
            rank[i] = 1;
        }
    }

    public int find(int x) {
        if (parent[x] != x) {
            parent[x] = find(parent[x]);
        }
        return parent[x];
    }

    public boolean union(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);

        if (rootX == rootY) {
            return false;
        }

        if (rank[rootX] > rank[rootY]) {
            parent[rootY] = rootX;
        } else if (rank[rootX] < rank[rootY]) {
            parent[rootX] = rootY;
        } else {
            parent[rootY] = rootX;
            rank[rootX]++;
        }

        componentCount--;
        return true;
    }

    public boolean isFullyConnected() {
        return componentCount == 1;
    }
}


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Longest Palindromic Substring

[**Question**](https://leetcode.com/problems/longest-palindromic-substring/description/) : 
Given a string  `s`, return  _the longest palindromic substring_ in  `s`.

**Example 1:**

**Input:** s = "babad"
**Output:** "bab"
**Explanation:** "aba" is also a valid answer.

**Example 2:**

**Input:** s = "cbbd"
**Output:** "bb"Given a string  `s`

[**Solution**]() :
How to detect a Palindrome.... period.

In this we create a for loop and we pass the string with two variables to a function that will check each indivudal string and keep it as the center for the palindrome.

The function will be called 'palindromedetektor' and we pass the string along with a _left_ and _right_ variable to it.

### Java Code : 
```java
class Solution {
    public String longestPalindrome(String s) {
        if (s == null || s.length() < 1) return "";
        
        int start = 0, end = 0;
        for (int i = 0; i < s.length(); i++) {
            int len1 = expandAroundCenter(s, i, i); // Assume odd length palindrome
            int len2 = expandAroundCenter(s, i, i + 1); // Assume even length palindrome
            int len = Math.max(len1, len2);
            if (len > end - start) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }
        return s.substring(start, end + 1);
    }
    
    private int expandAroundCenter(String s, int left, int right) {
        int L = left, R = right;
        while (L >= 0 && R < s.length() && s.charAt(L) == s.charAt(R)) {
            L--;
            R++;
        }
        return R - L - 1;
    }
}


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

>Day : Monday, 1st July 2024

## Three Consecutive Odds

[**Question**](https://leetcode.com/problems/three-consecutive-odds/description/?envType=daily-question&envId=2024-07-01):
Given an integer array `arr`, return `true` if there are three consecutive odd numbers in the array. Otherwise, return `false`.

**Example 1:**

**Input:** arr = [2,6,4,1]
**Output:** false
**Explanation:** There are no three consecutive odds.

**Example 2:**

**Input:** arr = [1,2,34,3,4,5,7,23,12]
**Output:** true
**Explanation:** [5,7,23] are three consecutive odds.

[**Solution**](https://chatgpt.com/share/880b8cfb-0216-48e4-ac69-125d1b6bab5f):
Simple solution ( But I messed up the resetting of the counter )

### Algorithm
1. Just maintain the count for the odd values in the first if condition in the for loop. 
2. Then additionally nest another if condition that checks if the count has reached 3 in that same if and return true if it has.
3. Create the else for the first if and then reset count to 0 from there.
4. return false outside the loop, since if true hasn't been sent then false will be automatically returned




### Java Code
```java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
        int count = 0;

        for(int i = 0; i < arr.length;i++){
            if (arr[i] % 2 == 1){
                count ++;
                    if (count == 3)
                        return true;
            }
            else  
                count = 0;
        }
        return false;
    }
}

```


- [Return to TOC](#table-of-contents-dsa)

<hr>

## Zigzag Conversion

[**Question**](https://leetcode.com/problems/zigzag-conversion/description/):
The string  `"PAYPALISHIRING"`  is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)


| P | | A | | H | | N | 
|--|--|--|--|--|--| --|
|A|P|L|S|I|I|G|
|Y| | I | | R |

And then read line by line:  `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

**Example 1:**

**Input:** s = "PAYPALISHIRING", numRows = 3
**Output:** "PAHNAPLSIIGYIR"

**Example 2:**

**Input:** s = "PAYPALISHIRING", numRows = 4
**Output:** "PINALSIGYAHRPI"
**Explanation:**
|P|||I ||| N|
|--|--|--|--|--|--|--|
|A||L|S||I|G|
|Y|A||H|R|
|P|||I|

[**Solution**]() : 
To solve this problem we need to figure out how to split them to create a zig zag pattern.

## Issues to solve : 



### Java Code 
```java


```

- [Return to TOC](#table-of-contents-dsa)
<hr>

> Day : Tuesday, 2nd July 2024

## Intersection of Two Arrays 2

[**Question**](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/?envType=daily-question&envId=2024-07-02):
Given two integer arrays  `nums1`  and  `nums2`, return  _an array of their intersection_. Each element in the result must appear as many times as it shows in both arrays and you may return the result in  **any order**.

**Example 1:**

**Input:** nums1 = [1,2,2,1], nums2 = [2,2]
**Output:** [2,2]

**Example 2:**

**Input:** nums1 = [4,9,5], nums2 = [9,4,9,8,4]
**Output:** [4,9]
**Explanation:** [9,4] is also accepted.

[**Solution**](https://chatgpt.com/share/d1b55f9f-688d-478a-832b-8e0f80b4fd30):
To get the solution of this we need to first sort the two arrays in ascending order and then check for common values

### Algorithm
1. First we set length variables for both arrays
2. Then we use _"Arrays.sort(array-to-be-sorted)"_ function to sort both the arrays
3. Then we start a while loop based on two pointers _i_ and _j_
4. If element nums1[i] < nums2[j] then we increment i
5. if element nums1[i] > nums2[j] then we increment j
6. Else they will both be equal and then we can copy the value at the i'th position into k ( initially 0 ) of the smaller array _( nums1 )_
7. Then we will return _Arrays.copOfrange(nums1, 0, k)_ so only the values we have changed from the range 0 to k are returned


### Java Code 
```Java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        int l1 =  nums1.length;
        int l2 =  nums2.length;
        int i = 0, j = 0, k = 0;

        // We will define the sort function later on
        Arrays.sort(nums1);
        Arrays.sort(nums2);

        // Here let us declare the while loop which is dependent on the two pointers
        while( i < l1 && j < l2 ){
            if(nums1[i] < nums2[j]){
                i++;
            }
            else if(nums1[i] > nums2[j]){
                j++;
            }
            else{
                nums1[k++] = nums1[i++];
                j++;
            }
        }
        return Arrays.copyOfRange(nums1, 0, k);
    }
}
```

- [Return to TOC](#table-of-contents-dsa)
<hr>

## Score of a string

[**Question**](https://leetcode.com/problems/score-of-a-string/description/?envType=daily-question&envId=2024-06-01) : 
You are given a string  `s`. The  **score**  of a string is defined as the sum of the absolute difference between the  **ASCII**  values of adjacent characters.

Return the  **score**  of  `s`.

**Example 1:**

**Input:**  s = "hello"

**Output:**  13

**Explanation:**

The  **ASCII**  values of the characters in  `s`  are:  `'h' = 104`,  `'e' = 101`,  `'l' = 108`,  `'o' = 111`. So, the score of  `s`  would be  `|104 - 101| + |101 - 108| + |108 - 108| + |108 - 111| = 3 + 7 + 0 + 3 = 13`.

[**Solution**]() : 
To solve this we need to use the function that will convert respective letters in the string into an array ( I think the split function should work )

This can be done by creating a simple for loop that will get the absolute diff of the current element to the next ( typecast to int to get the ascii value ) and then we can add them to the total sum

### New things learnt
1. The _"Math.abs( int a - int b)"_ function accepts two int values and then will proceed to give the absolute difference between them
2. The _"string.charAt(index)"_ function will give the character present at the indicated index of the string.	

### Java Code 
```Java
class Solution {
    public int scoreOfString(String s) {
        int tsum = 0;
        int cdiff = 0;

        for(int i = 0; i < s.length()-1; i++){
            int a = s.charAt(i);
            int b = s.charAt(i+1);
            cdiff = Math.abs(a - b);
            tsum += cdiff;
        }
        return tsum;
    }
}

```

- [Return to TOC](#table-of-contents-dsa)
<hr>

## No repetitions

**Question** : 
You are giving an array of characters and you must return an array of only unique characters from the initial array.

`Restrictions` : Do not use set() function to filter the characters or any other higher order functions .


[**Solution**](https://chatgpt.com/share/d1b55f9f-688d-478a-832b-8e0f80b4fd30) : 
The idea here is we create a new character array and then we add the new non existent variable to it everytime increment j index.

### Java Code - Approach 1 
```java
import java.util.Arrays;

public class UniqueCharacters {

    // Method to accept an array of characters and return an array of unique characters
    public char[] getUniqueCharacters(char[] inputArray) {
        int l = inputArray.length;
        char[] output = new char[l];
        int k = 0;
        
        for (int i = 0; i < l; i++) {
            boolean isUnique = true;
            for (int j = 0; j < k; j++) {
                if (inputArray[i] == output[j]) {
                    isUnique = false;
                    break;
                }
            }
            if (isUnique) {
                output[k++] = inputArray[i];
            }
        }
        
        return Arrays.copyOfRange(output, 0, k);
    }

    // Main method for testing the getUniqueCharacters method
    public static void main(String[] args) {
        // Create an instance of the UniqueCharacters class
        UniqueCharacters uniqueChars = new UniqueCharacters();

        // Example input array
        char[] inputArray = {'a', 'b', 'a', 'c', 'b', 'd', 'e', 'j', 'j', 'l'};

        // Call the getUniqueCharacters method
        char[] uniqueArray = uniqueChars.getUniqueCharacters(inputArray);

        // Print the result
        for (char c : uniqueArray) {
            System.out.print(c + " ");
        }
    }
}

```

### Java Code - Approach 2
```java
import java.util.Arrays;

public class UniqueCharacters {

    // Method to accept an array of characters and return an array of unique characters
    public char[] getUniqueCharacters(char[] inputArray) {
        int l = inputArray.length;
        char[] output = new char[l];
        int i = 0; // Index for output array
        int k = 0; // Index for inputArray
        while (k < l) { // Iterate through inputArray
            int j = 0;
            // Check if inputArray[k] already exists in output array
            while (j < i) {
                if (inputArray[k] == output[j]) {
                    break; // Skip adding if already exists
                }
                j++;
            }
            // If inputArray[k] is unique, add it to output array
            if (j == i) {
                output[i++] = inputArray[k];
            }
            k++;
        }
        return Arrays.copyOfRange(output, 0, i); // Return only the portion of output array with unique characters
    }

    // Main method for testing the getUniqueCharacters method
    public static void main(String[] args) {
        // Create an instance of the UniqueCharacters class
        UniqueCharacters uniqueChars = new UniqueCharacters();

        // Example input array
        char[] inputArray = {'a', 'b', 'a', 'c', 'b', 'd', 'e', 'j', 'j', 'l'};

        // Call the getUniqueCharacters method
        char[] uniqueArray = uniqueChars.getUniqueCharacters(inputArray);

        // Print the result
        for (char c : uniqueArray) {
            System.out.print(c + " ");
        }
    }
}


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Wednesday, 3rd July 2024

## Minimum Difference Between Largest and Smallest Value in Three Moves

[**Question**](https://leetcode.com/problems/minimum-difference-between-largest-and-smallest-value-in-three-moves/?envType=daily-question&envId=2024-07-03) : 
You are given an integer array  `nums`.

In one move, you can choose one element of  `nums`  and change it to  **any value**.

Return  _the minimum difference between the largest and smallest value of  `nums`  **after performing at most three moves**_.

**Example 1:**

**Input:** nums = [5,3,2,4]
**Output:** 0
**Explanation:** We can make at most 3 moves.
In the first move, change 2 to 3. nums becomes [5,3,3,4].
In the second move, change 4 to 3. nums becomes [5,3,3,3].
In the third move, change 5 to 3. nums becomes [3,3,3,3].
After performing 3 moves, the difference between the minimum and maximum is 3 - 3 = 0.

[**Solution**](https://chatgpt.com/share/51a39bb8-3e02-4eb0-b977-c1e210a7859e):
I misunderstood the way to solve the problem and just thought to reduce certain elements to the minimum value ( set to 0 ).

I need to think of the cases for a sorted array : 

### Algorithm
1. These cases could be 
	- Changing the last 3 elements, i.e., the biggest elements in the array
	- Changing the first 3 elements, i.e., the smallest elements.
	- Change the first element and last 2 elments
	- Change first two elements and the last elements.
2. The goal is to calculate the minimum difference for each of these and then get the least value as compared to the 
3. Every time while changing, we won't actually change the elements ( it'll be too lengthy) 
4. We will actually just compare the elements that will become the minimum and maximum after the change

### Java Code
```java
class Solution {
    public int minDifference(int[] nums) {
        int n = nums.length;
        if(n <= 4){
            return 0;
        }
        // Now we have a sorted array
        Arrays.sort(nums);

        // Possible Cases
        // Changing last 3 elements
        int mindiff = nums[n - 4] - nums[0];

        //Changing the first 3 elements
        mindiff = Math.min(mindiff, nums[n-1] - nums[3]);

        // Changing the first two and then the last element
        mindiff = Math.min(mindiff, nums[n-2] - nums[2]);

        //Changing the first element and the last two elements
        mindiff = Math.min(mindiff, nums[n-3] - nums[1]);

        return mindiff;
    }
}

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Reverse Integer

[**Question**](https://leetcode.com/problems/reverse-integer/description/): 
Given a signed 32-bit integer  `x`, return  `x` _with its digits reversed_. If reversing  `x`  causes the value to go outside the signed 32-bit integer range  `[-231, 231 - 1]`, then return  `0`.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**

**Example 1:**

**Input:** x = 123
**Output:** 321

[**Solution**]() : 



### New concepts learned
1. **Calculating the length of a number**
```java
int number = 12345;
int length = (int) Math.log10(number) + 1;
System.out.println("Length of number " + number + " is: " + length);
```
- By using the log function and adding 1 we can calculate the size of the integer.


### Java Code 
```java
class Solution {
    public int reverse(int x) {
        int n = (int) Math.log10(Math.abs(x)) + 1;
        int reversenum = 0, digit = 0;

        while ( x != 0){
            digit = x%10;
            if (reversenum > Integer.MAX_VALUE / 10 || (reversenum == Integer.MAX_VALUE / 10 && digit > 7)) return 0;
            if (reversenum < Integer.MIN_VALUE / 10 || (reversenum == Integer.MIN_VALUE / 10 && digit < -8)) return 0;
            reversenum = reversenum*10 + digit; 
            x /= 10;
        }
        return reversenum;
    }
}

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Thursday, 4th July 2024

## Merge Nodes in Between Zeros

[**Question**](https://leetcode.com/problems/merge-nodes-in-between-zeros/description/?envType=daily-question&envId=2024-07-04): 
You are given the  `head`  of a linked list, which contains a series of integers  **separated**  by  `0`'s. The  **beginning**  and  **end**  of the linked list will have  `Node.val == 0`.

For  **every** two consecutive  `0`'s,  **merge**  all the nodes lying in between them into a single node whose value is the  **sum**  of all the merged nodes. The modified list should not contain any  `0`'s.

Return  _the_  `head`  _of the modified linked list_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2022/02/02/ex1-1.png)

**Input:** head = [0,3,1,0,4,5,2,0]
**Output:** [4,11]
**Explanation:** 
The above figure represents the given linked list. The modified list contains
- The sum of the nodes marked in green: 3 + 1 = 4.
- The sum of the nodes marked in red: 4 + 5 + 2 = 11.


[**Solution**]() : 


### Algorithm


### Python Code 
```python
# Definition for singly-linked list.
#class ListNode(object):
#    def __init__(self, val=0, next=None):
#        self.val = val
#        self.next = next

class Solution(object):
    def mergeNodes(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        dummy = ListNode(0)  # Dummy node to ease list construction
        current = dummy      # Pointer to construct the new list
        sum_val = 0          # To store the sum of nodes between zeros
        head = head.next     # Skip the first zero
        
        while head:
            if head.val == 0:
                # When we hit a zero, we need to record the sum if it's not zero
                if sum_val != 0:
                    current.next = ListNode(sum_val)
                    current = current.next
                    sum_val = 0
            else:
                # Accumulate the sum of values between zeros
                sum_val += head.val
            head = head.next
        
        return dummy.next  # Return the new list skipping the dummy node


```

### Output 
```
head = [0,3,1,0,4,5,2,0]
Output
[4,11]
Expected
[4,11]
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Friday, 5th July 2024

##  Find the Minimum and Maximum Number of Nodes Between Critical Points

[**Question**](https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/description/?envType=daily-question&envId=2024-07-05): 
A  **critical point**  in a linked list is defined as  **either**  a  **local maxima**  or a  **local minima**.

A node is a  **local maxima**  if the current node has a value  **strictly greater**  than the previous node and the next node.

A node is a  **local minima**  if the current node has a value  **strictly smaller**  than the previous node and the next node.

Note that a node can only be a local maxima/minima if there exists  **both**  a previous node and a next node.

Given a linked list  `head`, return  _an array of length 2 containing_ `[minDistance, maxDistance]` _where_ `minDistance` _is the  **minimum distance**  between  **any two distinct**  critical points and_ `maxDistance` _is the  **maximum distance**  between  **any two distinct**  critical points. If there are  **fewer**  than two critical points, return_ `[-1, -1]`.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/10/13/a1.png)

**Input:** head = [3,1]
**Output:** [-1,-1]
**Explanation:** There are no critical points in [3,1].

[**Solution**]() : 



### Things to learn
1. Figure out this list declaration that accepts integer values only.
```java
List<Integer> criticalPoints = new  ArrayList<>();

```

### Java Code 
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public int[] nodesBetweenCriticalPoints(ListNode head) {
        if (head == null || head.next == null || head.next.next == null) {
            return new int[]{-1, -1};
        }
        
        List<Integer> criticalPoints = new ArrayList<>();
        ListNode prev = head;
        ListNode curr = head.next;
        int index = 1;
        
        while (curr.next != null) {
            if ((curr.val > prev.val && curr.val > curr.next.val) || 
                (curr.val < prev.val && curr.val < curr.next.val)) {
                criticalPoints.add(index);
            }
            prev = curr;
            curr = curr.next;
            index++;
        }
        
        if (criticalPoints.size() < 2) {
            return new int[]{-1, -1};
        }
        
        int minDistance = Integer.MAX_VALUE;
        int maxDistance = criticalPoints.get(criticalPoints.size() - 1) - criticalPoints.get(0);
        
        for (int i = 1; i < criticalPoints.size(); i++) {
            minDistance = Math.min(minDistance, criticalPoints.get(i) - criticalPoints.get(i - 1));
        }
        
        return new int[]{minDistance, maxDistance};
    }
}


```

### Output
```
head = [3,1]
Output
[-1,-1]
Expected
[-1,-1]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Saturday, 6th July 2024

## Pass the Pillow

[**Question**](https://leetcode.com/problems/pass-the-pillow/description/?envType=daily-question&envId=2024-07-06): 
There are  `n`  people standing in a line labeled from  `1`  to  `n`. The first person in the line is holding a pillow initially. Every second, the person holding the pillow passes it to the next person standing in the line. Once the pillow reaches the end of the line, the direction changes, and people continue passing the pillow in the opposite direction.

-   For example, once the pillow reaches the  `nth`  person they pass it to the  `n - 1th`  person, then to the  `n - 2th`  person and so on.

Given the two positive integers  `n`  and  `time`, return  _the index of the person holding the pillow after_ `time` _seconds_.

**Example 1:**

**Input:** n = 4, time = 5
**Output:** 2
**Explanation:** People pass the pillow in the following way: 1 -> 2 -> 3 -> 4 -> 3 -> 2.
After five seconds, the 2nd person is holding the pillow.

[**Solution**](https://chatgpt.com/share/b9243709-b524-45ab-b1ab-c0eb6a541fa7) : 
First I figured out how to switch on the end cases. Made it unecessarily complicated initially but in the end you have to switch when the value of i is one of the extremes and then create a bool variable that controls if the variable will increment or decrement.
Then we just have to create the while loop ke conditions so that we control when it stays in the loop and when it exits

### Python Code 
```python

class Solution:
    def passThePillow(self, n: int, time: int) -> int:
        i, t = 1,0
        flip = True
    
        while i >=1 and i <= n and t != time : 
            # First I figure out the edge cases
            if i == n:
                i -= 1
                t += 1
                flip = False
            elif i == 1:
                i += 1
                t += 1
                flip = True
            else : 
                if flip : 
                    i += 1
                    t += 1
                else :
                    i -= 1
                    t += 1
        
        return i
```

### Output 
```
Input
n = 4
time = 5
Output
2
Expected
2
```

### Python Code ( Chatgpt's )
```python
class Solution:
    def passThePillow(self, n: int, time: int) -> int:
        cycle_length = 2 * (n - 1)
        remainder_time = time % cycle_length
        if remainder_time < n:
            return 1 + remainder_time
        else:
            return 2 * n - 1 - remainder_time
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Sunday, 7th July 2024

## Water Bottles

[**Question**](https://leetcode.com/problems/water-bottles/description/?envType=daily-question&envId=2024-07-07): 
There are  `numBottles`  water bottles that are initially full of water. You can exchange  `numExchange`  empty water bottles from the market with one full water bottle.

The operation of drinking a full water bottle turns it into an empty bottle.

Given the two integers  `numBottles`  and  `numExchange`, return  _the  **maximum**  number of water bottles you can drink_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/07/01/sample_1_1875.png)

**Input:** numBottles = 9, numExchange = 3
**Output:** 13
**Explanation:** You can exchange 3 empty bottles to get 1 full water bottle.
Number of water bottles you can drink: 9 + 3 + 1 = 13.

[**Solution**](https://chatgpt.com/share/79f98a2c-500a-4ea7-b8cf-104256fcf5dd) : 
Now for this I need to calculate the maximum possible number of bottles that we can drink. This will simply be the sum of the number of bottles + the quotient when we divide the empty bottles by min required exchange for 1 fresh bottle.
Additionally if this quantity generates any new empty bottles we need to check again, so we will create an empty bottle counter as well.

### Algorithm


### Python Code 
```python
class Solution(object):
    def numWaterBottles(self, numBottles, numExchange):
        empty= totBot = numBottles
        while True :
            # This will be the case to return the bottles back
            if empty < numExchange :
                return totBot
            else : 
                totBot = totBot + empty//numExchange 
                empty = empty//numExchange + empty%numExchange
        

```

### Output
```
Input
numBottles = 15
numExchange = 4
Output
19
Expected
19

```

### Python Code ( Chatgpt )
```python
class Solution(object):
    def numWaterBottles(self, numBottles, numExchange):
        total_drunk = numBottles
        empty_bottles = numBottles
        
        while empty_bottles >= numExchange:
            new_bottles = empty_bottles // numExchange
            total_drunk += new_bottles
            empty_bottles = empty_bottles % numExchange + new_bottles
        
        return total_drunk

```

### Mistakes made 
1. Chatgpt's solution was some 18 ms faster than I was and also it removed the redundant if else statement within the while loop. It just took the case in the while loop and then had it exit when it didn't work. ( Makes sense, idk why I went in such a roundabout way for this )

- [Return to TOC](#table-of-contents-dsa)

<hr>

## String to Integer

[**Question**](https://leetcode.com/problems/string-to-integer-atoi/): 
Implement the  `myAtoi(string s)`  function, which converts a string to a 32-bit signed integer.

The algorithm for  `myAtoi(string s)`  is as follows:

1.  **Whitespace**: Ignore any leading whitespace (`" "`).
2.  **Signedness**: Determine the sign by checking if the next character is  `'-'`  or  `'+'`, assuming positivity is neither present.
3.  **Conversion**: Read the integer by skipping leading zeros until a non-digit character is encountered or the end of the string is reached. If no digits were read, then the result is 0.
4.  **Rounding**: If the integer is out of the 32-bit signed integer range  `[-231, 231 - 1]`, then round the integer to remain in the range. Specifically, integers less than  `-231`  should be rounded to  `-231`, and integers greater than  `231 - 1`  should be rounded to  `231 - 1`.

Return the integer as the final result.

**Example 1:**

**Input:**  s = "42"

**Output:**  42

**Explanation:**

The underlined characters are what is read in and the caret is the current reader position.
Step 1: "42" (no characters read because there is no leading whitespace)
         ^
Step 2: "42" (no characters read because there is neither a '-' nor '+')
         ^
Step 3: "42" ("42" is read in)

[**Solution**]() : 


### Algorithm


### Python Code 
```python
class Solution(object):
    def myAtoi(self, s):
        """
        :type s: str
        :rtype: int
        """
        # First case is whitespace which is cleared by this
        s = s.strip()
        negative = False
        if not s : 
            return 0
        
        # This will decide where to start
        start = 0
        # Next is sign check 
        if s[0] == '-'or s[0] == '+':
            if s[0] == '-':
                negative = True
            start += 1
        
        result = 0
        # We will convert and add the values to the result 
        for i in range (start, len(s)):
            if s[i].isdigit():
                result = result*10 + int(s[i])
            else : 
                break
            
        if negative :
            result = -result
            
        int_max = 2**31 - 1
        int_min = -2**31
        if(result < int_min):
            return int_min
        if( result > int_max): 
            return int_max
        else : 
            return result

            

```

### Output
```
Input
s = "   -042"
Output
-42
Expected
-42

Input
s = "1337c0d3"
Output
1337
Expected
1337
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Monday, 8th July 2024

## Find the Winner of the circular game	

[**Question**](https://leetcode.com/problems/find-the-winner-of-the-circular-game/description/?envType=daily-question&envId=2024-07-08): 
There are  `n`  friends that are playing a game. The friends are sitting in a circle and are numbered from  `1`  to  `n`  in  **clockwise order**. More formally, moving clockwise from the  `ith`  friend brings you to the  `(i+1)th`  friend for  `1 <= i < n`, and moving clockwise from the  `nth`  friend brings you to the  `1st`  friend.

The rules of the game are as follows:

1.  **Start**  at the  `1st`  friend.
2.  Count the next  `k`  friends in the clockwise direction  **including**  the friend you started at. The counting wraps around the circle and may count some friends more than once.
3.  The last friend you counted leaves the circle and loses the game.
4.  If there is still more than one friend in the circle, go back to step  `2`  **starting**  from the friend  **immediately clockwise**  of the friend who just lost and repeat.
5.  Else, the last friend in the circle wins the game.

Given the number of friends,  `n`, and an integer  `k`, return  _the winner of the game_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/03/25/ic234-q2-ex11.png)

**Input:** n = 5, k = 2
**Output:** 3
**Explanation:** Here are the steps of the game:
1) Start at friend 1.
2) Count 2 friends clockwise, which are friends 1 and 2.
3) Friend 2 leaves the circle. Next start is friend 3.
4) Count 2 friends clockwise, which are friends 3 and 4.
5) Friend 4 leaves the circle. Next start is friend 5.
6) Count 2 friends clockwise, which are friends 5 and 1.
7) Friend 1 leaves the circle. Next start is friend 3.
8) Count 2 friends clockwise, which are friends 3 and 5.
9) Friend 5 leaves the circle. Only friend 3 is left, so they are the winner.

[**Solution**](https://chatgpt.com/share/d8c4e3be-81ad-47c4-846e-b3262b8ececd) : 
I was thinking of converting it into a linked list / initializing a linked list and then we can go ahead and set up the condition where it increments by k every-time. Oh also there is a circular linked list so I guess using that would be the best thing where we create a for loop within a while loop ( ik O (n2) complexity ) and then we can have that for loop execute head.next for those k times, while loop ka ending condition is once there is no next value left


### Java Code 
```java
class Solution {
    public int findTheWinner(int n, int k) {
        // Create a list of friends numbered from 1 to n
        ArrayList<Integer> friends = new ArrayList<>();
        for (int i = 1; i <= n; i++) {
            friends.add(i);
        }

        // Start at the first friend (index 0)
        int currentIndex = 0;

        // Continue until only one friend remains
        while (friends.size() > 1) {
            // Calculate the index of the friend to be removed
            currentIndex = (currentIndex + k - 1) % friends.size();
            // Remove the friend
            friends.remove(currentIndex);
        }

        // The last remaining friend is the winner
        return friends.get(0);
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int n = 5;
        int k = 2;
        System.out.println("The winner is: " + solution.findTheWinner(n, k)); // Output: 3
    }
}


```

### Output
```
Input 
n = 5
k = 2
Output
3
Expected
3

```

### Code Logic 
Over here there is a simple concept that I need to learn. In an ArryaList, then when an element is deleted the subsequent elements are shifted one to the left which automatically puts the next element to be check onto the current index value ( say 'i' )

### Java Code ( My code )
```java
class Solution {
    public int findTheWinner(int n, int k) {
        LinkedList<Integer> linkedlist = initializeLinkedList(n)
    }
    public LinkedList<Integer> initializLinkedList(int n){
        LinkedList<Integer> linkedlist = new LinkedList<>()
        for(int i = 1; i <= n;i++ ){
            linkedlist.add(i);
        }
        return linkedlist;
    }
}

```

### Python Code to declare a linked list
```python
class Node:
    def __init__(self, value=None):
        self.value = value
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, value):
        new_node = Node(value)
        if self.head is None:
            self.head = new_node
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = new_node

    def display(self):
        current = self.head
        while current:
            print(current.value, end=' ')
            current = current.next
        print()

# Function to initialize the linked list with values from 1 to n
def initialize_linked_list(n):
    linked_list = LinkedList()
    for i in range(1, n + 1):
        linked_list.append(i)
    return linked_list

# Example usage
n = 10
linked_list = initialize_linked_list(n)
linked_list.display()

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Richest Customer Wealth

[**Question**](https://leetcode.com/problems/richest-customer-wealth/description/): 
You are given an  `m x n`  integer grid  `accounts`  where  `accounts[i][j]`  is the amount of money the  `i​​​​​​​​​​​th​​​​`  customer has in the  `j​​​​​​​​​​​th`​​​​ bank. Return _the  **wealth**  that the richest customer has._

A customer's  **wealth**  is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum  **wealth**.

**Example 1:**

**Input:** accounts = [[1,2,3],[3,2,1]]
**Output:** 6
**Explanation****:**
`1st customer has wealth = 1 + 2 + 3 = 6` `2nd customer has wealth = 3 + 2 + 1 = 6` Both customers are considered the richest with a wealth of 6 each, so return 6.

[**Solution**]() : 
I want to iterate through the 2D array using two for loops in python. I don't need to use them as indices now, but just as the variables I have given them

It has a time complexity of $O(n\times m)$
It has a space compleity of $O(1)$


### Python Code 
```python
class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        result = cust_result = 0
        for customer in accounts :
            cust_result = 0
            for banks in customer : 
                cust_result += banks
            if result < cust_result :
                result = cust_result 
                
        return result

```

### Java Code
```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int max_Wealth = 0;

        for(int[] customer : accounts){
            int cust_wealth = 0;
            for(int banks : customer){
                cust_wealth += banks;
            }
            max_Wealth = Math.max(max_Wealth, cust_wealth);
        }
        return max_Wealth;
    }

}

```

### Output
```
Input
accounts = [[2,8,7],[7,1,3],[1,9,5]]
Output
17
Expected
17

```

### Points to remember 


- [Return to TOC](#table-of-contents-dsa)

<hr>

## Fizz Buzz

[**Question**](https://leetcode.com/problems/fizz-buzz/description/): 
Given an integer  `n`, return  _a string array_ `answer` _(**1-indexed**) where_:

-   `answer[i] == "FizzBuzz"`  if  `i`  is divisible by  `3`  and  `5`.
-   `answer[i] == "Fizz"`  if  `i`  is divisible by  `3`.
-   `answer[i] == "Buzz"`  if  `i`  is divisible by  `5`.
-   `answer[i] == i`  (as a string) if none of the above conditions are true.

**Example 1:**

**Input:** n = 3
**Output:** ["1","2","Fizz"]

**Example 2:**

**Input:** n = 5
**Output:** ["1","2","Fizz","4","Buzz"]

[**Solution**]() : 
In this solution first we take care of the case where FizzBuzz will appear since it needs to ce

### Python Code 
```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        array = []

        for i in range (1, n+1) :
            if i % 3 == 0 and i % 5 == 0 :
                array.append("FizzBuzz") 
            elif i % 3 == 0 :
                array.append("Fizz")
            elif i % 5 == 0 :
                array.append("Buzz")
            else :
                array.append(str(i))
        return array

```

### Java code ( Leetcodes )
```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> array = new ArrayList<>(n);

        for(int i=1; i <= n; i++){
            boolean div3 = i % 3 == 0;
            boolean div5 = i % 5 == 0;

            if (div3 && div5){
                array.add("FizzBuzz");
            }
            else if(div3){
                array.add("Fizz");
            }else if(div5){
                array.add("Buzz");
            }
            else {
                array.add(String.valueOf(i));
            }   

        }
        return array;
    }
}

```

### Output
```
Input
n = 15
Output
["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
Expected
["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Tuesday, 9th July 2024

## Palindrome Number

[**Question**](https://leetcode.com/problems/palindrome-number/description/): 
Given an integer  `x`, return  `true` _if_ `x` _is a_

_**palindrome**_

_, and_ `false` _otherwise_.

**Example 1:**

**Input:** x = 121
**Output:** true
**Explanation:** 121 reads as 121 from left to right and from right to left.

**Example 2:**

**Input:** x = -121
**Output:** false
**Explanation:** From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

[**Solution**](https://chatgpt.com/share/ee760b5a-51de-4896-a172-619868e74808) : 


### Java Code ( Leetcodes )
```java
class Solution {
    public boolean isPalindrome(int x) {
        
        if(x < 0){
            return false;
        }

        int digit = 0;
        // Use long long if they are expected to provide extremely large values
        long reversed = 0;
        // For some reason they have used long over here and I'm guessing that is to accept larger int values
        int temp = x;

        while (temp!=0){
            digit = temp % 10;
            reversed = reversed*10 + digit;
            temp /= 10;
        }

        if( reversed == x ){
            return true;
        }
        else
            return false;
        

    }
}

```



### Output
```
Input
x = 121
Output
true
Expected
true


```

- [Return to TOC](#table-of-contents-dsa)

<hr>


##  Average Waiting Time

[**Question**](https://leetcode.com/problems/average-waiting-time/description/?envType=daily-question&envId=2024-07-09): 
There is a restaurant with a single chef. You are given an array  `customers`, where  `customers[i] = [arrivali, timei]:`

-   `arrivali`  is the arrival time of the  `ith`  customer. The arrival times are sorted in  **non-decreasing**  order.
-   `timei`  is the time needed to prepare the order of the  `ith`  customer.

When a customer arrives, he gives the chef his order, and the chef starts preparing it once he is idle. The customer waits till the chef finishes preparing his order. The chef does not prepare food for more than one customer at a time. The chef prepares food for customers  **in the order they were given in the input**.

Return  _the  **average**  waiting time of all customers_. Solutions within  `10-5`  from the actual answer are considered accepted.

**Example 1:**

**Input:** customers = [[1,2],[2,5],[4,3]]
**Output:** 5.00000
**Explanation:** 1) The first customer arrives at time 1, the chef takes his order and starts preparing it immediately at time 1, and finishes at time 3, so the waiting time of the first customer is 3 - 1 = 2.
2) The second customer arrives at time 2, the chef takes his order and starts preparing it at time 3, and finishes at time 8, so the waiting time of the second customer is 8 - 2 = 6.
3) The third customer arrives at time 4, the chef takes his order and starts preparing it at time 8, and finishes at time 11, so the waiting time of the third customer is 11 - 4 = 7.
So the average waiting time = (2 + 6 + 7) / 3 = 5.

[**Solution**]() : 


### Algorithm


### Java Code 
```java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        double wait = 0;
        int end_time = 0;
        int arrival = 0;
        int time = 0;
        int n = customers.length;
        for(int i =0; i < n; i++){
            arrival = customers[i][0];
            time = customers[i][1];
            if( arrival > end_time)
                end_time = arrival;
            end_time += time;
            wait += end_time - arrival;
        }
        return wait/n;
    }
}

```

### Output
```
Input
customers = [[1,2],[2,5],[4,3]]
Output
5.00000
Expected
5.00000

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Wednesday, 10th July 2024

## Crawler Log Folder

[**Question**](https://leetcode.com/problems/crawler-log-folder/description/?envType=daily-question&envId=2024-07-10): 
The Leetcode file system keeps a log each time some user performs a  _change folder_  operation.

The operations are described below:

-   `"../"`  : Move to the parent folder of the current folder. (If you are already in the main folder,  **remain in the same folder**).
-   `"./"`  : Remain in the same folder.
-   `"x/"`  : Move to the child folder named  `x`  (This folder is  **guaranteed to always exist**).

You are given a list of strings  `logs`  where  `logs[i]`  is the operation performed by the user at the  `ith`  step.

The file system starts in the main folder, then the operations in  `logs`  are performed.

Return  _the minimum number of operations needed to go back to the main folder after the change folder operations._

[**Solution**]() : 
Easy as fuck. Only thing is while negating the counts of the steps required to return to the main folder when the step "../" has been done, you need to makesure the value of the steps required to return is greater than 0 ( makes it a tricky condition because you need to nest another if so that it goes into the first if when we meet a "../" but ignores the next if , if the value of steps_ret == 0)

### Java Code 
```java
class Solution {
    public int minOperations(String[] logs) {
        int steps_ret = 0;
        String parent = "../";
        String remain = "./";
        
        for(int i = 0; i < logs.length; i++){
            if(logs[i].equals(parent)){
                
                if(steps_ret > 0){
                    steps_ret += -1 ;
                }
            }
            else if(logs[i].equals(remain) ){

            }
            else{
                steps_ret += 1;
            }
        }
        return steps_ret;
    }
}

```

### Output
```
Input
logs = ["d1/","d2/","../","d21/","./"]
Output
2
Expected
2

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Thursday, 11th July 2024

## Reverse Substrings between each pair of Parentheses

[**Question**](https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses/description/?envType=daily-question&envId=2024-07-11): 
You are given a string  `s`  that consists of lower case English letters and brackets.

Reverse the strings in each pair of matching parentheses, starting from the innermost one.

Your result should  **not**  contain any brackets.

**Example 1:**

**Input:** s = "(abcd)"
**Output:** "dcba"

**Example 2:**

**Input:** s = "(u(love)i)"
**Output:** "iloveu"
**Explanation:** The substring "love" is reversed first, then the whole string is reversed.

[**Solution**]() : 

#### StringBuilder Usage

### Java Code 
```java
class Solution {
    public String reverseParentheses(String s) {
        Stack<Character> stack = new Stack<>();
        
        for (char ch : s.toCharArray()) {
            if (ch == ')') {
                // Pop characters until we find an opening parenthesis '('
                StringBuilder sb = new StringBuilder();
                while (stack.peek() != '(') {
                    sb.append(stack.pop());
                }
                // Pop the '(' from the stack
                stack.pop();
                // Push the reversed string back to the stack
                for (char reversedChar : sb.toString().toCharArray()) {
                    stack.push(reversedChar);
                }
            } else {
                stack.push(ch);
            }
        }
        
        // Build the final result from the stack
        StringBuilder result = new StringBuilder();
        for (char ch : stack) {
            result.append(ch);
        }
        
        return result.toString();
    }
}


```

### Output
```
Input
s = "(ed(et(oc))el)"
Output
"leetcode"
Expected
"leetcode"

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Friday, 12th July 2024

## Maximum Score from Removing substrings

[**Question**](https://leetcode.com/problems/maximum-score-from-removing-substrings/description/?envType=daily-question&envId=2024-07-12): 
You are given a string  `s`  and two integers  `x`  and  `y`. You can perform two types of operations any number of times.

-   Remove substring  `"ab"`  and gain  `x`  points.
    -   For example, when removing  `"ab"`  from  `"cabxbae"`  it becomes  `"cxbae"`.
-   Remove substring  `"ba"`  and gain  `y`  points.
    -   For example, when removing  `"ba"`  from  `"cabxbae"`  it becomes  `"cabxe"`.

Return  _the maximum points you can gain after applying the above operations on_  `s`.

**Example 1:**

**Input:** s = "cdbcbbaaabab", x = 4, y = 5
**Output:** 19
**Explanation:**
- Remove the "ba" underlined in "cdbcbbaaabab". Now, s = "cdbcbbaaab" and 5 points are added to the score.
- Remove the "ab" underlined in "cdbcbbaaab". Now, s = "cdbcbbaa" and 4 points are added to the score.
- Remove the "ba" underlined in "cdbcbbaa". Now, s = "cdbcba" and 5 points are added to the score.
- Remove the "ba" underlined in "cdbcba". Now, s = "cdbc" and 5 points are added to the score.
Total score = 5 + 4 + 5 + 5 = 19.

[**Solution**](https://chatgpt.com/c/90f0851a-301f-4288-a0f5-8b2ea64594ae) : 

### My shitty try at coding
```java
class Solution {
    public int maximumGain(String s, int x, int y) {
        ArrayList<String> text = new ArrayList<String>();
        for(int j = 0; j < s.length(); j++){
            text.add(s.charAt(j));
        }
        int score = 0;

        for(int i = 0; i < s.length(); i++){
            if(s.charAt(i).equals("a") && s.charAt(i+1).equals("b")){
                score += x;
                text.remove(i);
                text.remove(i+1);
            }
            else if(i.equals("b") && (i+1).equals("a")){
                score += y;
                text.remove(i);
                text.remove(i+1);
            }

        }
        return score;
    }
}

```

### Errors made here 
1. Used primitive type character at one point and tried to create an arraylist of characters, but I couldn't figure out how to access the indexes and teh nI couldn't figure out how to compare and remove the compared strings after that.
2. 

### Java Code using StringBuilder
```java
class Solution {
    public int maximumGain(String s, int x, int y) {

        StringBuilder str = new StringBuilder(s);
        int score = 0;
        String firstPair, secondPair;
        int firstScore, secondScore;
        if (x > y) {
            firstPair = "ab";
            secondPair = "ba";
            firstScore = x;
            secondScore = y;
        } else {
            firstPair = "ba";
            secondPair = "ab";
            firstScore = y;
            secondScore = x;
        }

        score += removePairs(str, firstPair, firstScore);
        score += removePairs(str, secondPair, secondScore);
        return score;
    }
    private int removePairs(StringBuilder sb, String pair, int score) {
        int totalScore = 0;
        int index;
        while ((index = sb.indexOf(pair)) != -1) {
            sb.delete(index, index + 2);
            totalScore += score;
        }
        return totalScore;
    }
}

```

### Java Code using Stack
```java

class Solution {
    public int maximumGain(String s, int x, int y) {
        int score = 0;
        Stack<Character> stack = new Stack<>();

        // Helper method to process the string and remove pairs
        score += processString(s, stack, 'a', 'b', x, y);
        score += processString(stackToString(stack), new Stack<>(), 'b', 'a', y, x);

        return score;
    }

    private int processString(String s, Stack<Character> stack, char first, char second, int firstScore, int secondScore) {
        int score = 0;
        for (char c : s.toCharArray()) {
            if (!stack.isEmpty() && stack.peek() == first && c == second) {
                stack.pop();
                score += firstScore;
            } else {
                stack.push(c);
            }
        }
        return score;
    }

    private String stackToString(Stack<Character> stack) {
        StringBuilder sb = new StringBuilder();
        while (!stack.isEmpty()) {
            sb.insert(0, stack.pop());
        }
        return sb.toString();
    }
}


```

### Output
```
Input
s = "cdbcbbaaabab"
x = 4
y = 5
Output
19
Expected
19
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Saturday, 13th July 2024


## Robot Collisions

[**Question**](https://leetcode.com/problems/robot-collisions/description/?envType=daily-question&envId=2024-07-13): 
There are  `n`  **1-indexed**  robots, each having a position on a line, health, and movement direction.

You are given  **0-indexed**  integer arrays  `positions`,  `healths`, and a string  `directions`  (`directions[i]`  is either  **'L'**  for  **left**  or  **'R'**  for  **right**). All integers in  `positions`  are  **unique**.

All robots start moving on the line **simultaneously**  at the  **same speed** in their given directions. If two robots ever share the same position while moving, they will  **collide**.

If two robots collide, the robot with  **lower health**  is  **removed**  from the line, and the health of the other robot  **decreases**  **by one**. The surviving robot continues in the  **same**  direction it was going. If both robots have the  **same**  health, they are both  removed from the line.

Your task is to determine the  **health**  of the robots that survive the collisions, in the same  **order** that the robots were given,  i.e. final heath of robot 1 (if survived), final health of robot 2 (if survived), and so on. If there are no survivors, return an empty array.

Return  _an array containing the health of the remaining robots (in the order they were given in the input), after no further collisions can occur._

**Note:**  The positions may be unsorted.

**Example 1:**

![](https://assets.leetcode.com/uploads/2023/05/15/image-20230516011718-12.png)

**Input:** positions = [5,4,3,2,1], healths = [2,17,9,15,10], directions = "RRRRR"
**Output:** [2,17,9,15,10]
**Explanation:** No collision occurs in this example, since all robots are moving in the same direction. So, the health of the robots in order from the first robot is returned, [2, 17, 9, 15, 10].

[**Solution**](https://chatgpt.com/share/0da14daa-c7a1-4dc7-a8c4-54812bbd65d1) : 


### Algorithm
We need to split up the logic for the collisions.
The robot will always move one number at a time, so in that case, robots moving in the same direction will not collide at all.
In this case I think we have to create another array that will keep track of the positions of the serparate robots, and using those indices we will gather the health of the robots when collision occurs

### Python Code 
```python
class Solution:
    def survivedRobotsHealths(self, positions, healths, directions):
        # Pair positions with their indices, healths, and directions
        robots = sorted(zip(positions, healths, directions, range(len(positions))))
        
        stack = []
        result = [None] * len(positions)
        
        for position, health, direction, index in robots:
            if direction == 'R':
                stack.append((health, index))
            else:
                while stack and health > 0:
                    prev_health, prev_index = stack.pop()
                    if prev_health > health:
                        stack.append((prev_health - 1, prev_index))
                        health = 0
                    elif prev_health < health:
                        health -= 1
                    else:
                        health = 0
                if health > 0:
                    result[index] = health

        # Remaining robots in the stack are all moving to the right and haven't collided
        while stack:
            health, index = stack.pop()
            result[index] = health

        # Filter out None values, meaning those robots didn't survive
        return [h for h in result if h is not None]

# Example usage:
solution = Solution()
positions = [5, 4, 3, 2, 1]
healths = [2, 17, 9, 15, 10]
directions = "RRRRR"
print(solution.survivedRobotsHealths(positions, healths, directions))  # Output: [2, 17, 9, 15, 10]


```

### Output
```
Input
positions = [5,4,3,2,1]
healths = [2,17,9,15,10]
directions = "RRRRR"
Stdout
[2, 17, 9, 15, 10]
Output
[2,17,9,15,10]
Expected
[2,17,9,15,10]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Roman to Integer

[**Question**](https://leetcode.com/problems/roman-to-integer/): 
Roman numerals are represented by seven different symbols: `I`,  `V`,  `X`,  `L`,  `C`,  `D`  and  `M`.

**Symbol**       **Value**
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

For example, `2`  is written as  `II` in Roman numeral, just two ones added together.  `12`  is written as `XII`, which is simply  `X + II`. The number  `27`  is written as  `XXVII`, which is  `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not  `IIII`. Instead, the number four is written as  `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as  `IX`. There are six instances where subtraction is used:

-   `I`  can be placed before  `V`  (5) and  `X`  (10) to make 4 and 9.
-   `X`  can be placed before  `L`  (50) and  `C`  (100) to make 40 and 90.
-   `C`  can be placed before  `D`  (500) and  `M`  (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

**Example 1:**

**Input:** s = "III"
**Output:** 3
**Explanation:** III = 3.

**Example 2:**

**Input:** s = "LVIII"
**Output:** 58
**Explanation:** L = 50, V= 5, III = 3.

[**Solution**](https://chatgpt.com/share/4884bfb3-1d0c-4efa-9ddc-89e32d6c2f72) : 

### Algorithm
1. We need to give a certain string value it's corresponding integer value. This should be done with the use of switch case
2. When it encounters the respective switch case while we iterate through the string then we can give it the respective numerical value

### Problems faced
How to split the string into it's respective components ?

Make sure you write the incrementing as `i += 1` always and not `i + 1` because that will be incorrect and will not sum add the value `1` to `i`

### Python Code 
```python
class Solution:
    def romanToInt(self, s: str) -> int:
        total = 0
        i = 0
        while i < len(s):
            if  i+1 < len(s) and s[i] == "I" and s[i+1] == "V" :
                total += 4
                i += 2
            elif i+1 < len(s) and s[i] == "I" and s[i+1] == "X" :
                total += 9
                i += 2
            elif i+1 < len(s) and s[i] == "X" and s[i+1] == "L" :
                total += 40
                i += 2
            elif i+1 < len(s) and s[i] == "X" and s[i+1] == "C" :
                total += 90
                i += 2
            elif i+1 < len(s) and s[i] == "C" and s[i+1] == "D" :
                total += 400
                i += 2
            elif i+1 < len(s) and s[i] == "C" and s[i+1] == "M" :
                total += 900
                i += 2
            elif s[i] == "I":
                total += 1
                i += 1
            elif s[i] == "V":
                total += 5
                i += 1
            elif s[i] == "X":
                total += 10
                i += 1
            elif s[i] =="L":
                total += 50
                i += 1
            elif s[i] == "C":
                total += 100
                i += 1
            elif s[i] == "D":
                total += 500
                i += 1
            elif s[i] == "M":
                total += 1000
                i += 1
        return total

```

### Output
```
Input
s ="MCMXCIV"
Output
1994
Expected
1994

```

- [Return to TOC](#table-of-contents-dsa)

<hr>


## Integer to Roman

[**Question**](): 
Seven different symbols represent Roman numerals with the following values:

Symbol

Value
| Roman | Integer |
| -- | -- |
| I | 1 |
|V | 5 |
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|

Roman numerals are formed by appending the conversions of decimal place values from highest to lowest. Converting a decimal place value into a Roman numeral has the following rules:

-   If the value does not start with 4 or 9, select the symbol of the maximal value that can be subtracted from the input, append that symbol to the result, subtract its value, and convert the remainder to a Roman numeral.
-   If the value starts with 4 or 9 use the **subtractive form** representing one symbol subtracted from the following symbol, for example, 4 is 1 (`I`) less than 5 (`V`):  `IV` and 9 is 1 (`I`) less than 10 (`X`):  `IX`. Only the following subtractive forms are used: 4 (`IV`), 9 (`IX`), 40 (`XL`), 90 (`XC`), 400 (`CD`) and 900 (`CM`).
-   Only powers of 10 (`I`,  `X`,  `C`,  `M`) can be appended consecutively at most 3 times to represent multiples of 10. You cannot append 5 (`V`), 50 (`L`), or 500 (`D`) multiple times. If you need to append a symbol 4 times use the  **subtractive form**.

Given an integer, convert it to a Roman numeral.

**Example 1:**

**Input:**  num = 3749

**Output:**  "MMMDCCXLIX"

**Explanation:**

3000 = MMM as 1000 (M) + 1000 (M) + 1000 (M)
 700 = DCC as 500 (D) + 100 (C) + 100 (C)
  40 = XL as 10 (X) less of 50 (L)
   9 = IX as 1 (I) less of 10 (X)
Note: 49 is not 1 (I) less of 50 (L) because the conversion is based on decimal places

[**Solution**]() : 
Remember the largest roman numeral that can be represented is `3,999` as `MMMCMXCIX`

### Algorithm
Even this one is the exact opposite to the first one we need to implement a different idea here, since we need to be able to get the correct values from summing up certain numbers

### Python Code 
```python


```

### Output
```


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Sunday, 14th July 2024

## Regular Expression Matching

[**Question**](https://leetcode.com/problems/regular-expression-matching/): 
Given an input string  `s` and a pattern  `p`, implement regular expression matching with support for  `'.'`  and  `'*'`  where:

-   `'.'`  Matches any single character.​​​​
-   `'*'`  Matches zero or more of the preceding element.

The matching should cover the  **entire**  input string (not partial).

**Example 1:**

**Input:** s = "aa", p = "a"
**Output:** false
**Explanation:** "a" does not match the entire string "aa".

**Example 2:**

**Input:** s = "aa", p = "a*"
**Output:** true
**Explanation:** '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".

**Example 3:**

**Input:** s = "ab", p = ".*"
**Output:** true
**Explanation:** ".*" means "zero or more (*) of any character (.)".

[**Solution**](https://chatgpt.com/share/ee218118-4346-408c-be56-b71f20623ee1) : 
The idea here was to try and account for all possible cases, which became very tough and lengthy using simple if and else loops. 

I need to upgrade my process of thinking, to be able to go ahead and use ideas just beside regular loops

### Python Code ( Mine with numerous errors )
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        if(s == p):
            return True 
        # setup a for loop within an if loop for the asterxi condition and then increment the i value so that when it exits it'll affect the overall while loop
        i = j  = 0
        counter = 1
        ans = True
        
        while i < len(s) and j < len(p):
            #case for . character matching any single character
            if p[j] == "." :
                if j + 1 < len(p) and p[j+1] == "*":
                    counter = 1
                    while counter < len(s) and s[i + counter] == s[i] :
                        counter += 1
                        if counter == len(s):
                            return True
                    i += counter - 1
                j += 1
                i += 1
            elif s[i] == p[j] and j + 1 >= len(p) and i+1 < len(s):
                ans = False
                i += 1
                j += 1
            elif s[i] == p[j] :
                if j + 1 < len(p) and p[j+1] == "*":
                    counter = 1
                    while counter < len(s) and s[i + counter] == s[i] :
                        counter += 1
                        if counter == len(s):
                            return True
                    i += counter - 1
                i += 1
                j += 1
            elif s[i] != p[j] :
                if p[j+1] == "*" :
                    j += 1
                j += 1
            else : 
                ans = False
        return ans
```

### Python Code ( Chatgpts )
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        if s == p:
            return True 
        
        i = j = 0
        
        while i < len(s) and j < len(p):
            # Case for '.' character matching any single character
            if p[j] == ".":
                if j + 1 < len(p) and p[j + 1] == "*":
                    # Try to match zero or more of any character
                    while i < len(s):
                        if self.isMatch(s[i:], p[j + 2:]):
                            return True
                        i += 1
                    return self.isMatch(s[i:], p[j + 2:])
                else:
                    i += 1
                    j += 1
            elif j + 1 < len(p) and p[j + 1] == "*":
                # Case for '*' handling zero or more of the preceding element
                while i < len(s) and (s[i] == p[j] or p[j] == "."):
                    if self.isMatch(s[i:], p[j + 2:]):
                        return True
                    i += 1
                return self.isMatch(s[i:], p[j + 2:])
            elif s[i] == p[j]:
                i += 1
                j += 1
            else:
                return False
        
        # Check for remaining pattern
        while j + 1 < len(p) and p[j + 1] == "*":
            j += 2
        
        # Both s and p should be fully consumed for a match
        return i == len(s) and j == len(p)



```

### Python Code ( Efficient method of solving )
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        def dfs(i, j):
            if (i, j) in memo:
                return memo[(i, j)]
            
            if j == len(p):
                return i == len(s)
            
            match = i < len(s) and (p[j] == s[i] or p[j] == '.')
            
            if j + 1 < len(p) and p[j + 1] == '*':
                memo[(i, j)] = dfs(i, j + 2) or (match and dfs(i + 1, j))
                return memo[(i, j)]
            
            if match:
                memo[(i, j)] = dfs(i + 1, j + 1)
                return memo[(i, j)]
            
            memo[(i, j)] = False
            return False
        
        memo = {}
        return dfs(0, 0)


```

> Over here we do something called memo creation where we use it to store those values have already been checked
> This method takes `56ms` whereas my method takes around `9892ms`. The difference ? Insane.

### Output
```
Input
s = "ab"
p = ".*"
Output
true

```

- [Return to TOC](#table-of-contents-dsa)

<hr>


## Container with most water

[**Question**](https://leetcode.com/problems/container-with-most-water/description/): 
You are given an integer array  `height`  of length  `n`. There are  `n`  vertical lines drawn such that the two endpoints of the  `ith`  line are  `(i, 0)`  and  `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return  _the maximum amount of water a container can store_.

**Notice**  that you may not slant the container.

[**Solution**]() : 


### Algorithm


### Python Code ( which only works for simple simple cases, but exceeds time cuz of $O(n^2)$ complexity )
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        # To find the area containing most water we will have to multiply the length with the breadth
        l = b = curr_area = max_area = 0
        for i in range (0, len(height)):
            for j in range (i+1, len(height)):
                curr_area = ( j - i )*(min(height[i],height[j]))
                max_area = max(curr_area, max_area)
        
        return max_area

```

### Output
```
Input
height = [1,8,6,2,5,4,8,3,7]
Output
49
Expected
49

```

### Python Code 
```python


```

### Output 
```


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

##  Longest Common Prefix

[**Question**](https://leetcode.com/problems/longest-common-prefix/description/): 
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string  `""`.

**Example 1:**

**Input:** strs = ["flower","flow","flight"]
**Output:** "fl"

**Example 2:**

**Input:** strs = ["dog","racecar","car"]
**Output:** ""
**Explanation:** There is no common prefix among the input strings.

[**Solution**]() : 


### Solving Method
1. Since it's prefix, that means to a certain extent from the starting character.
2. Since the prefix has to exist within each word we can use a single word's size as reference.
3. Decide to character to compare
4. Iterate through the list
5. If the index is out of range ( i.e., consecutive words are smaller but match up till then, or the character isn't matching)
6. Within the if statemetn return the prefix till the given i-1 index ( which will be represented as i since it's exclusive) if the character is `NOT` similar to the given current character

### Python Code 
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        # Since it's prefix, that means to a certain extent from the starting character.
        if not strs :
            return ""
        
        result = ""

        # Since the prefix has to exist within each word we can use a single word's size as reference
        first_word = strs[0]

        for i in range(0, len(first_word)):
            # Decide to character to compare
            char = first_word[i]
            
            # Iterate through the list
            for word in strs[1:]:
                #If the index is out of range ( i.e., consecutive words are smaller but match up till then, or the character isn't matching)
                if i >= len(word) or char != word[i] :
                    # return the prefix till the given i-1 index ( which will be represented as i since it's exclusive) 
                    return first_word[:i]
            
        return first_word
                

```

### Output
```
Input
strs = ["flower","flow","flight"]
Output
"fl"
Expected
"fl"

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Smallest Missing Integer Greater Than Sequential Prefix Sum

[**Question**](https://leetcode.com/problems/smallest-missing-integer-greater-than-sequential-prefix-sum/): 
You are given a  **0-indexed**  array of integers  `nums`.

A prefix  `nums[0..i]`  is  **sequential**  if, for all  `1 <= j <= i`,  `nums[j] = nums[j - 1] + 1`. In particular, the prefix consisting only of  `nums[0]`  is  **sequential**.

Return  _the  **smallest**  integer_  `x`  _missing from_  `nums`  _such that_  `x`  _is greater than or equal to the sum of the  **longest**  sequential prefix._

**Example 1:**

**Input:** nums = [1,2,3,2,5]
**Output:** 6
**Explanation:** The longest sequential prefix of nums is [1,2,3] with a sum of 6. 6 is not in the array, therefore 6 is the smallest missing integer greater than or equal to the sum of the longest sequential prefix.

[**Solution**]() : 

###  Solving Method
The idea is to calculate the sum of the longest sequential prefix, so we will implementa loop that will find it first

### Python Code 
```python


```

### Output
```


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Number of Atoms

[**Question**](https://leetcode.com/problems/number-of-atoms/description/?envType=daily-question&envId=2024-07-14): 
Given a string  `formula`  representing a chemical formula, return  _the count of each atom_.

The atomic element always starts with an uppercase character, then zero or more lowercase letters, representing the name.

One or more digits representing that element's count may follow if the count is greater than  `1`. If the count is  `1`, no digits will follow.

-   For example,  `"H2O"`  and  `"H2O2"`  are possible, but  `"H1O2"`  is impossible.

Two formulas are concatenated together to produce another formula.

-   For example,  `"H2O2He3Mg4"`  is also a formula.

A formula placed in parentheses, and a count (optionally added) is also a formula.

-   For example,  `"(H2O2)"`  and  `"(H2O2)3"`  are formulas.

Return the count of all elements as a string in the following form: the first name (in sorted order), followed by its count (if that count is more than  `1`), followed by the second name (in sorted order), followed by its count (if that count is more than  `1`), and so on.

The test cases are generated so that all the values in the output fit in a  **32-bit**  integer.

**Example 1:**

**Input:** formula = "H2O"
**Output:** "H2O"
**Explanation:** The count of elements are {'H': 2, 'O': 1}.

**Example 2:**

**Input:** formula = "Mg(OH)2"
**Output:** "H2MgO2"
**Explanation:** The count of elements are {'H': 2, 'Mg': 1, 'O': 2}.

[**Solution**]() : 


###  Solving Method


### Python Code 
```python
class Solution:
    def countOfAtoms(self, formula: str) -> str:
        import collections
        import re
        
        stack = [collections.Counter()]
        i = 0
        n = len(formula)
        
        while i < n:
            if formula[i] == '(':
                stack.append(collections.Counter())
                i += 1
            elif formula[i] == ')':
                top = stack.pop()
                i += 1
                i_start = i
                while i < n and formula[i].isdigit():
                    i += 1
                multiplier = int(formula[i_start:i] or 1)
                for elem, count in top.items():
                    stack[-1][elem] += count * multiplier
            else:
                i_start = i
                i += 1
                while i < n and formula[i].islower():
                    i += 1
                elem = formula[i_start:i]
                i_start = i
                while i < n and formula[i].isdigit():
                    i += 1
                count = int(formula[i_start:i] or 1)
                stack[-1][elem] += count
        
        result = []
        for elem in sorted(stack[-1].items()):
            result.append(elem[0])
            if elem[1] > 1:
                result.append(str(elem[1]))
        
        return ''.join(result)

```

### Output
```
Input
formula = "K4(ON(SO3)2)2"
Output
"K4N2O14S4"
Expected
"K4N2O14S4"

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day :  Monday, 15th July 2024

## Create Binary Tree from Descriptions

[**Question**](): 
You are given a 2D integer array  `descriptions`  where  `descriptions[i] = [parenti, childi, isLefti]`  indicates that  `parenti`  is the  **parent**  of  `childi`  in a  **binary**  tree of  **unique**  values. Furthermore,

-   If  `isLefti == 1`, then  `childi`  is the left child of  `parenti`.
-   If  `isLefti == 0`, then  `childi`  is the right child of  `parenti`.

Construct the binary tree described by  `descriptions`  and return  _its  **root**_.

The test cases will be generated such that the binary tree is  **valid**.

**Example 1:**

![](https://assets.leetcode.com/uploads/2022/02/09/example1drawio.png)

**Input:** descriptions = [[20,15,1],[20,17,0],[50,20,1],[50,80,0],[80,19,1]]
**Output:** [50,20,80,15,17,19]
**Explanation:** The root node is the node with value 50 since it has no parent.
The resulting binary tree is shown in the diagram.

[**Solution**]() : 


###  Solving Method


### Python Code 
```python
import java.util.*;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode() {}
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public TreeNode createBinaryTree(int[][] descriptions) {
        // Map to store the nodes by their value
        Map<Integer, TreeNode> nodeMap = new HashMap<>();
        // Set to store all child nodes
        Set<Integer> childNodes = new HashSet<>();
        
        // Create all nodes and establish parent-child relationships
        for (int[] description : descriptions) {
            int parentVal = description[0];
            int childVal = description[1];
            boolean isLeft = description[2] == 1;
            
            // Get or create parent node
            TreeNode parentNode = nodeMap.getOrDefault(parentVal, new TreeNode(parentVal));
            nodeMap.put(parentVal, parentNode);
            
            // Get or create child node
            TreeNode childNode = nodeMap.getOrDefault(childVal, new TreeNode(childVal));
            nodeMap.put(childVal, childNode);
            
            // Establish the relationship
            if (isLeft) {
                parentNode.left = childNode;
            } else {
                parentNode.right = childNode;
            }
            
            // Mark this node as a child
            childNodes.add(childVal);
        }
        
        // The root is the node which is never a child
        TreeNode root = null;
        for (int val : nodeMap.keySet()) {
            if (!childNodes.contains(val)) {
                root = nodeMap.get(val);
                break;
            }
        }
        
        return root;
    }
}


```

### Output
```
Input
descriptions = [[20,15,1],[20,17,0],[50,20,1],[50,80,0],[80,19,1]]
Output
[50,20,80,15,17,19]
Expected
[50,20,80,15,17,19]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Tuesday, 16th July 2024

## Step-By-Step Directions From a Binary Tree Node to Another

[**Question**](https://leetcode.com/problems/step-by-step-directions-from-a-binary-tree-node-to-another/description/?envType=daily-question&envId=2024-07-16): 
You are given the  `root`  of a  **binary tree**  with  `n`  nodes. Each node is uniquely assigned a value from  `1`  to  `n`. You are also given an integer  `startValue`  representing the value of the start node  `s`, and a different integer  `destValue`  representing the value of the destination node  `t`.

Find the  **shortest path**  starting from node  `s`  and ending at node  `t`. Generate step-by-step directions of such path as a string consisting of only the  **uppercase**  letters  `'L'`,  `'R'`, and  `'U'`. Each letter indicates a specific direction:

-   `'L'`  means to go from a node to its  **left child**  node.
-   `'R'`  means to go from a node to its  **right child**  node.
-   `'U'`  means to go from a node to its  **parent**  node.

Return  _the step-by-step directions of the  **shortest path**  from node_ `s` _to node_  `t`.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/11/15/eg1.png)

**Input:** root = [5,1,2,3,null,6,4], startValue = 3, destValue = 6
**Output:** "UURL"
**Explanation:** The shortest path is: 3 → 1 → 5 → 2 → 6.

[**Solution**]() : 


###  Solving Method


### Java Code 
```java
class Solution {
    public String getDirections(TreeNode root, int startValue, int destValue) {
        // Find LCA
        TreeNode lca = findLCA(root, startValue, destValue);
        
        // Find paths from LCA to startValue and destValue
        StringBuilder pathToStart = new StringBuilder();
        StringBuilder pathToDest = new StringBuilder();
        
        findPath(lca, startValue, pathToStart);
        findPath(lca, destValue, pathToDest);
        
        // Generate directions
        StringBuilder result = new StringBuilder();
        
        // Add 'U' for each character in pathToStart
        for (int i = 0; i < pathToStart.length(); i++) {
            result.append('U');
        }
        
        // Append pathToDest
        result.append(pathToDest);
        
        return result.toString();
    }
    
    // Helper method to find the Lowest Common Ancestor (LCA)
    private TreeNode findLCA(TreeNode root, int startValue, int destValue) {
        if (root == null || root.val == startValue || root.val == destValue) {
            return root;
        }
        
        TreeNode left = findLCA(root.left, startValue, destValue);
        TreeNode right = findLCA(root.right, startValue, destValue);
        
        if (left != null && right != null) {
            return root;
        }
        
        return left != null ? left : right;
    }
    
    // Helper method to find the path from the given node to the target value
    private boolean findPath(TreeNode root, int target, StringBuilder path) {
        if (root == null) {
            return false;
        }
        
        if (root.val == target) {
            return true;
        }
        
        // Try to go to the left child
        path.append('L');
        if (findPath(root.left, target, path)) {
            return true;
        }
        path.deleteCharAt(path.length() - 1); // backtrack
        
        // Try to go to the right child
        path.append('R');
        if (findPath(root.right, target, path)) {
            return true;
        }
        path.deleteCharAt(path.length() - 1); // backtrack
        
        return false;
    }
}



```

### Output
```
Input
root =[5,1,2,3,null,6,4]
startValue = 3
destValue = 6
Output
"UURL"
Expected
"UURL"

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Three Sum

[**Question**](https://leetcode.com/problems/3sum/description/): 
Given an integer array nums, return all the triplets  `[nums[i], nums[j], nums[k]]`  such that  `i != j`,  `i != k`, and  `j != k`, and  `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [[-1,-1,2],[-1,0,1]]
**Explanation:** 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

[**Solution**](https://chatgpt.com/share/022752b7-8048-4db7-b0cb-ad1ff29ac1c7) : 


###  Solving Method
So there are two things to cehck in this case. First that the numbers are not equal and second, that the sum is somehow 0.

3 nested for loops should od the trick, but the better way to go about this should be,


### Java Code 
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        int n = nums.length;
        List<List<Integer>> result = new ArrayList<>();

        // Sort the array to handle duplicates and use two pointers
        Arrays.sort(nums);

        for (int i = 0; i < n - 2; i++) {
            // Skip duplicate elements
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            int j = i + 1;
            int k = n - 1;
            while (j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                if (sum == 0) {
                    result.add(Arrays.asList(nums[i], nums[j], nums[k]));
                    // Skip duplicate elements
                    while (j < k && nums[j] == nums[j + 1]) j++;
                    while (j < k && nums[k] == nums[k - 1]) k--;
                    j++;
                    k--;
                } else if (sum < 0) {
                    j++;
                } else {
                    k--;
                }
            }
        }
        return result;
    }
}



```

### Output
```
Input
nums = [-1,0,1,2,-1,-4]
Output
[[-1,-1,2],[-1,0,1]]
Expected
[[-1,-1,2],[-1,0,1]]
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Letter Combinations of a Phone Number

[**Question**](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/): 
Given a string containing digits from  `2-9`  inclusive, return all possible letter combinations that the number could represent. Return the answer in  **any order**.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![](https://assets.leetcode.com/uploads/2022/03/15/1200px-telephone-keypad2svg.png)

**Example 1:**

**Input:** digits = "23"
**Output:** ["ad","ae","af","bd","be","bf","cd","ce","cf"]

**Example 2:**

**Input:** digits = ""
**Output:** []

**Example 3:**

**Input:** digits = "2"
**Output:** ["a","b","c"]

[**Solution**](https://chatgpt.com/share/e6013b52-3d8e-4c06-9769-2dc82c5c63b9) : 


### :red_circle: Solving Method
Recursion is what we use here where we recursively pass the ( **I do not understand the recursion here so this question has to be solved again**)

### Python Code 
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits :
            return []
            # We return an empty list if there are no digits


        # The idea is to create two things, first a dictionary of the corresponding numbers and the count of letters under then, secondly an array of the different letters, so that we can concatenate the products. 
        digits_to_letter = {'2':'abc','3':'def','4':'ghi','5':'jkl','6':'mno','7':'pqrs','8':'tuv','9':'wxyz'}

        # Here we define the recursive function that will create all possible combinations
        def backtrack(idx, combination):
            if idx == len(digits):
                res.append(combination)
                return
            
            for letter in digits_to_letter[digits[idx]]:
                # What is happening here is that we're basically passing digits[idx] as a parameter to the dictionary digits_to_letters.
                backtrack(idx + 1, combination + letter)
                # This will go through each individual letter in each key and combine it 
            
            
        res = []
        backtrack(0,"")

        return res

```

### Output
```
Input
digits ="23"
Output
["ad","ae","af","bd","be","bf","cd","ce","cf"]
Expected
["ad","ae","af","bd","be","bf","cd","ce","cf"]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Wednesday, 17th July 2024

## Valid Parenthesis

[**Question**](https://leetcode.com/problems/valid-parentheses/description/): 
Given a string  `s`  containing just the characters  `'('`,  `')'`,  `'{'`,  `'}'`,  `'['`  and  `']'`, determine if the input string is valid.

An input string is valid if:

1.  Open brackets must be closed by the same type of brackets.
2.  Open brackets must be closed in the correct order.
3.  Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

**Input:** s = "()"
**Output:** true

**Example 2:**

**Input:** s = "()[]{}"
**Output:** true

**Example 3:**

**Input:** s = "(]"
**Output:** false

[**Solution**]() : 


###  Solving Method
There are effectively 3 kinds of parenthesis
Using a stack for this might be the best idea.
First we put all the parenthesis in a stack and then we go ahead and check for each one and we pop the value till we encounter it.
If it doesn't then it isn't a valid parenthesis ? 
- But then what about the nested parenthesis??

### Python Code 
```python
class Solution:
    def isValid(self, s: str) -> bool:
        str_stack = []

        for c in s :
            if c in '({[':
                str_stack.append(c)
            else:
                if not str_stack or (c == ')' and str_stack[-1] != '(') or ( c == '}' and str_stack[-1] != '{') or (c == ']' and str_stack[-1] != '['):
                    return False
                str_stack.pop()
            
        return not str_stack

```
`This had a much better runtime and beat around 68.20% of the peoples answers`


### Java Code 
```java
class Solution {
    public boolean isValid(String s) {
        while(true){
            if(s.contains("()")){
                s = s.replace("()","");
            }
            else if(s.contains("{}")){
                s = s.replace("{}","");
            }
            else if(s.contains("[]")){
                s = s.replace("[]","");
            }
            else{
                return s.isEmpty();
                
            }
        }
    }
}

```
` This had a much slower execution time and only beat around 5.01%`


### Output
```
Input
s =
"()[]{}"
Output
true
Expected
true

```

### if condition writing
Here in this case you need to make sure you aren't making your if conditions too complex. To simple check if something isn't true / is false, in python the use of `not` helps to do that.<br>
So instead of writing : 
```python
if str_stack == False :
# Some random condition

```

we will write
```python
if not str_stack :
# Some random condition
```

Also pay attention to how they have used this : 
```python
if not str_stack or (c == ')' and str_stack[-1] != '(') or ( c == '}' and str_stack[-1] != '{') or (c == ']' and str_stack[-1] != '['):

```

### New shortcut discovered
Pressing `Ctrl + Shift + B` gives you an automatic template to enter bold text. <br> Similarly pressing `Ctl+Shift+I` will give you a template to enter italicized text


- [Return to TOC](#table-of-contents-dsa)

<hr>

## Set Matrix Zeroes

[**Question**](https://leetcode.com/problems/set-matrix-zeroes/description/): 
Given an  `m x n`  integer matrix  `matrix`, if an element is  `0`, set its entire row and column to  `0`'s.

You must do it  [in place](https://en.wikipedia.org/wiki/In-place_algorithm).

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/08/17/mat1.jpg)

**Input:** matrix = [[1,1,1],[1,0,1],[1,1,1]]
**Output:** [[1,0,1],[0,0,0],[1,0,1]]

[**Solution**]() : 
The idea in this question was basically not to set the entire row to 0 immediately ( since those might affect future computations ) but rather set them to max or min possible value and then in another loop we set all those individual values to 0

### Brute Force Approach
```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m = len(matrix)
        n = len(matrix[0])

        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0:
                    self.markRow(matrix, i, n)
                    self.markColumn(matrix, j, m)
        
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == -1:
                    matrix[i][j] = 0
    
    def markRow(self,matrix : List[List[int]], row : int, num_cols : int) -> None:  
        for i in range(num_cols):
            if matrix[row][i] != 0 :
                matrix[row][i] = -1

    def markColumn(self,matrix : List[List[int]], cols : int, num_rows : int) -> None:
        for i in range(num_rows):
            if matrix[i][cols] != 0 :
                matrix[i][cols] = -1
     
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m = len(matrix)
        n = len(matrix[0])

        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0:
                    self.markRow(matrix, i, n)
                    self.markColumn(matrix, j, m)
        
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 99999:
                    matrix[i][j] = 0
    
    def markRow(self,matrix : List[List[int]], row : int, num_cols : int) -> None:  
        for i in range(num_cols):
            if matrix[row][i] != 0 :
                matrix[row][i] = 99999

    def markColumn(self,matrix : List[List[int]], cols : int, num_rows : int) -> None:
        for i in range(num_rows):
            if matrix[i][cols] != 0 :
                matrix[i][cols] = 99999   
```

### Better method 
1. Instead of iterating throught the individual column and rows we can check if there is a minimum of even 1 0 in a given row then we can mark that row to be converter in a column
2. So we can instantiate two new arrays of size `m` and `n`
3. Then we store 1 or 0 ( as true or false ) if there is a zero in the row or column
4. The only issue is this takes an auxillary space to complete and hence is not fully optimal


```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m = len(matrix)
        n = len(matrix[0])
        col_check = [0 for _ in range(n)]
        row_check = [0 for _ in range(m)]

        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0 :
                    col_check[j] = 1
                    row_check[i] = 1

        for i in range(m):
            for j in range(n):
                if(row_check[i] == 1 or col_check[j] == 1):
                    matrix[i][j] = 0
                    
```

### Optimal Method
Now to not use a matrix we will have to do any and every operations within the matrix itself.


### Output
```
Input
matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]

Output
[[0,0,0,0],[0,4,5,0],[0,3,1,0]]
Expected
[[0,0,0,0],[0,4,5,0],[0,3,1,0]]
```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Delete Nodes And Return Forest

[**Question**](https://leetcode.com/problems/delete-nodes-and-return-forest/description/?envType=daily-question&envId=2024-07-17): 
Given the  `root`  of a binary tree, each node in the tree has a distinct value.

After deleting all nodes with a value in  `to_delete`, we are left with a forest (a disjoint union of trees).

Return the roots of the trees in the remaining forest. You may return the result in any order.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/07/01/screen-shot-2019-07-01-at-53836-pm.png)

**Input:** root = [1,2,3,4,5,6,7], to_delete = [3,5]
**Output:** [[1,2,null,4],[6],[7]]

**Example 2:**

**Input:** root = [1,2,4,null,3], to_delete = [3]
**Output:** [[1,2,4]]

**Constraints:**

-   The number of nodes in the given tree is at most  `1000`.
-   Each node has a distinct value between  `1`  and  `1000`.
-   `to_delete.length <= 1000`
-   `to_delete`  contains distinct values between  `1`  and  `1000`.


[**Solution**]() : 




### Python Code 
```python

```

### Output
```


```


###  Hash Tables

> [Link to video](https://www.youtube.com/watch?v=eJiGN1h8XzM&ab_channel=ApnaCollege)

A hash set is an important data structure because of it's time complexity.
If we need to `search, insert or delete` an element into it then it takes time $O(1)$. 

Whereas in these other data structures we have the following comparisions :
|Operation|HashMap|Array|Sorted Array|BST|
|--|--|--|--|--|
|`Insertion`|$O(1)$|$O(1)$|$O(n)$|$O(h)$|
|`Search`|$O(1)$|$O(n)$|$O(logn)$|$O(h)$|
|`Deletion`|$O(1)$|$O(n)$|$O(n)$|$O(h)$|

### Java Code
```java
// Import statmenet for HashSets
import java.util.HashSet;
// IMport statmenet for iterator
import java.util.Iterator;

public class Hashing {

    public static void main(String[] args) {
        HashSet<Integer> set = new HashSet<>();

        // Insert function
        set.add(9);
        set.add(2);
        set.add(5);
        set.add(9); // 9 will be added only once.

        // Search Function
        set.contains(1); // This should return the boolean value 'true' or 'false'
        if(set.contains(2)){
            System.out.println("Set contains 2");
        }
        if(!set.contains(4)){
            System.out.println("Set doesn't contain 4");
        }

        // Delete function

        set.remove(9);

        if(!set.contains(9)){
            System.out.println("9 has been removed from the set");
        }

        System.out.println(" Size of the set is "+ set.size());

        //Printing a whole set
        System.out.println(set);

        //Iterator
        Iterator it = set.iterator(); // This will return a variable that will help us traverse the HashSet
        // hasNext, next functions are usable for this.

        // next() will return the next value in the set ( the first time iterator 'it' will be pointing at null)

        while(it.hasNext()){
            System.err.println(it.next());
        }
        //it.hasNext() is a bool value that will check if a next value exists.
        // The order of elements present in the HashSet can be RANDOM, and the iteration order isn't specified.
        

    }
}
```

### Output
```
Set contains 2
Set doesn't contain 4
9 has been removed from the set
Size of the set is 2
[2, 5]
2
5
```

### :exclamation: Point to remember :exclamation:
- An `ArrayList` and a `HashSet` have similar functions that are used for `search, insert, checking size and delete functions` which are `contains()`,`add()`,`size()` and `remove()` functions.

## HashMaps

> [Link to video](https://www.youtube.com/watch?v=WeF3_nk-UqY)

 

<hr>

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Thursday, 18th July 2024

## Number of Good Leaf Nodes

[**Question**](https://leetcode.com/problems/number-of-good-leaf-nodes-pairs/description/?envType=daily-question&envId=2024-07-18): 
You are given the  `root`  of a binary tree and an integer  `distance`. A pair of two different  **leaf**  nodes of a binary tree is said to be good if the length of  **the shortest path**  between them is less than or equal to  `distance`.

Return  _the number of good leaf node pairs_  in the tree.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/07/09/e1.jpg)

**Input:** root = [1,2,3,null,4], distance = 3
**Output:** 1
**Explanation:** The leaf nodes of the tree are 3 and 4 and the length of the shortest path between them is 3. This is the only good pair.

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/07/09/e2.jpg)

**Input:** root = [1,2,3,4,5,6,7], distance = 3
**Output:** 2
**Explanation:** The good pairs are [4,5] and [6,7] with shortest path = 2. The pair [4,6] is not good because the length of ther shortest path between them is 4.

**Example 3:**

**Input:** root = [7,1,4,6,null,5,3,null,null,null,null,null,2], distance = 3
**Output:** 1
**Explanation:** The only good pair is [2,5].

[**Solution**]() : 


###  Solving Method


### Python Code 
```python

```

### Output
```


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Friday, 19th July 2024

## Lucky numbers in a Matrix

[**Question**](https://leetcode.com/problems/lucky-numbers-in-a-matrix/description/?envType=daily-question&envId=2024-07-19): 
Given an  `m x n`  matrix of  **distinct** numbers, return  _all  **lucky numbers**  in the matrix in  **any** order_.

A  **lucky number**  is an element of the matrix such that it is the minimum element in its row and maximum in its column.

**Example 1:**

**Input:** matrix = [[3,7,8],[9,11,13],[15,16,17]]
**Output:** [15]
**Explanation:** 15 is the only lucky number since it is the minimum in its row and the maximum in its column.

[**Solution**]() : 


###  Solving Method
We need to iterate through the column adn the row at the same time and then we need to check for the minimum 

1. Create a while loop that is dependent on both the variables reaching the max of the rows and columns
2. Within the while loop create two for loops that are dependent 

### Some bullshit idea on recursion
```python
class Solution:
    def luckyNumbers (self, matrix: List[List[int]]) -> List[int]:
        row_count = len(matrix)
        col_count = len(matrix[0])
        row_min = 999999
        col_max = 0
        result = []
      
        def row_check(row_idx : int,i : int, row_min : int):
            if(i == col_count):
                return row_min
            else :
                row_check(row_idx, i+1, min(matrix[row_idx][i],row_min))

        def col_check(col_idx : int, j : int, col_max : int):
            if(j == row_count):
                return col_max
            else :
                col_check(col_idx, j+1, max(matrix[j][col_idx],col_max))
        
        for i in range(col_count):
            row_check(i,0,row_min)
            col_check(i,0,col_max)
            if row_check == col_check :
                resul.append(row_check)
        

```

### Some other random try that doesn't solve majority of the casese 
```python code
class Solution:
    def luckyNumbers (self, matrix: List[List[int]]) -> List[int]:
        row_count = len(matrix)
        col_count = len(matrix[0])
        result = []
        row_check = col_check = 0
      
        while(row_check < row_count and col_check < col_count):
            row_min = float('inf')
            col_max = -float('inf')
            # For minimum in row
            for i in range (col_count):
                row_min = min(matrix[row_check][i],row_min)

            # For max in column
            for j in range (row_count):
                col_max = max(matrix[j][col_check], col_max)

            if row_min == col_max : 
                result.append(row_min)
            # These two will remain as one of the static components while either the row value or column value get's incremented
            row_check += 1
            col_check += 1
        return result

```

### Python Code ( By me )
```python
class Solution:
    def luckyNumbers (self, matrix: List[List[int]]) -> List[int]:
        row_count = len(matrix)
        col_count = len(matrix[0])
        result = []
        row_list = []
        col_list = []

        for i in range (row_count):
            row_min = float('inf')
            for j in range(col_count):
                row_min = min(matrix[i][j],row_min)
            row_list.append(row_min)

        for i in range(col_count):
            col_max = -float('inf')
            for j in range(row_count):
                col_max = max(matrix[j][i],col_max)
            col_list.append(col_max)

        for val in row_list:
            if val in col_list:
                result.append(val)

        return result


```

### Python Code ( Leetcode )
```python
class Solution:
    def luckyNumbers(self, matrix: list[list[int]]) -> list[int]:
        rows: int = len(matrix)
        cols: int = len(matrix[0])

        row_maximum_of_minimums: int = 0
        for row in matrix:
            row_maximum_of_minimums = max(min(row), row_maximum_of_minimums)

        col_minimum_of_maximums: int = 10**5 + 1
        for col_ind in range(cols):
            col_maximum = max([matrix[row_ind][col_ind] for row_ind in range(rows)])
            col_minimum_of_maximums = min(col_maximum, col_minimum_of_maximums)

        return [col_minimum_of_maximums] if row_maximum_of_minimums == col_minimum_of_maximums else []


```

### Output
```
Input
matrix =
[[3,7,8],[9,11,13],[15,16,17]]
Output
[15]
Expected
[15]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Pascal's Triangle

[**Question**](https://leetcode.com/problems/pascals-triangle/): 
Given an integer  `numRows`, return the first numRows of  **Pascal's triangle**.

In  **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

**Example 1:**

**Input:** numRows = 5
**Output:** [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

**Example 2:**

**Input:** numRows = 1
**Output:** [[1]]

[**Solution**](https://chatgpt.com/share/8ef7d05f-cff8-471a-b6b6-3c5184ecd1ef) : 
###  Solving Method
The logic behing this is that we just have to add the previous two elements so let us figure out the math behind this. Each row contains an increasing number of elements so 
`row 1` : 1 element
`row 2` : 2 elements

.
.
..... and so on
So if we think of each row numbered starting from the $0^{th}$ index then each row needs i + 1 values. 
An element needs to have at least two predecessors for it to have a value that isn't 1

### Python Code 
```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        result = []

        if numRows == 0 :
            return result
        
        result.append([1])
        for i in range(1, numRows):
            row = []
            for j in range(0,i+1):
                if j == 0 or j == i:
                    row.append(1)
                else : 
                    val = result[i-1][j-1] + result[i-1][j]
                    row.append(val)
            result.append(row)

        return result

```

### Output
```
Input
numRows = 5
Output
[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
Expected
[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

## Next Permutation

[**Question**](https://leetcode.com/problems/next-permutation/description/): 
A  **permutation**  of an array of integers is an arrangement of its members into a sequence or linear order.

-   For example, for  `arr = [1,2,3]`, the following are all the permutations of  `arr`:  `[1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1]`.

The  **next permutation**  of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the  **next permutation**  of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

-   For example, the next permutation of  `arr = [1,2,3]`  is  `[1,3,2]`.
-   Similarly, the next permutation of  `arr = [2,3,1]`  is  `[3,1,2]`.
-   While the next permutation of  `arr = [3,2,1]`  is  `[1,2,3]`  because  `[3,2,1]`  does not have a lexicographical larger rearrangement.

Given an array of integers  `nums`,  _find the next permutation of_  `nums`.

The replacement must be  **[in place](http://en.wikipedia.org/wiki/In-place_algorithm)**  and use only constant extra memory.

**Example 1:**

**Input:** nums = [1,2,3]
**Output:** [1,3,2]

**Example 2:**

**Input:** nums = [3,2,1]
**Output:** [1,2,3]

**Example 3:**

**Input:** nums = [1,1,5]
**Output:** [1,5,1]

**Constraints:**

-   `1 <= nums.length <= 100`
-   `0 <= nums[i] <= 100`

[**Solution**]() : 


###  Two Pointers





### Python Code 
```python

```

### Output
```


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Saturday, 20th July 2024

## Find Valid Matrix Given Row and Column Sums

[**Question**](https://leetcode.com/problems/find-valid-matrix-given-row-and-column-sums/description/?envType=daily-question&envId=2024-07-20): 
You are given two arrays  `rowSum`  and  `colSum`  of non-negative integers where  `rowSum[i]`  is the sum of the elements in the  `ith`  row and  `colSum[j]`  is the sum of the elements of the  `jth`  column of a 2D matrix. In other words, you do not know the elements of the matrix, but you do know the sums of each row and column.

Find any matrix of  **non-negative**  integers of size  `rowSum.length x colSum.length`  that satisfies the  `rowSum`  and  `colSum`  requirements.

Return  _a 2D array representing  **any**  matrix that fulfills the requirements_. It's guaranteed that  **at least one** matrix that fulfills the requirements exists.

**Example 1:**

**Input:** rowSum = [3,8], colSum = [4,7]
**Output:** [[3,0],
         [1,7]]
**Explanation:** 
0th row: 3 + 0 = 3 == rowSum[0]
1st row: 1 + 7 = 8 == rowSum[1]
0th column: 3 + 1 = 4 == colSum[0]
1st column: 0 + 7 = 7 == colSum[1]
The row and column sums match, and all matrix elements are non-negative.
Another possible matrix is: [[1,2],
                             [3,5]]

**Example 2:**

**Input:** rowSum = [5,7,10], colSum = [8,6,8]
**Output:** [[0,5,0],
         [6,1,0],
         [2,0,8]]

**Constraints:**

-   `1 <= rowSum.length, colSum.length <= 500`
-   `0 <= rowSum[i], colSum[i] <= 108`
-   `sum(rowSum) == sum(colSum)`

[**Solution**]() : 


###  Solving Method
The simple idea would be giving the numbers varibles and then solving the number accordingly. Quadratic equations witll only be valid for certain cases.

Example case : 
`rowSum` = [3,8]
`colSum` = [4,7]

| | Column | Column|
|--|--|--|
|Row|3|0|
|Row|1|7|

a + b = 3
a + c = 4
c + d = 8
b + d = 7



### Python Code 
```python
class Solution:
    def restoreMatrix(self, rowSum: List[int], colSum: List[int]) -> List[List[int]]:
        m = len(rowSum)
        n = len(colSum)
        cur_row = 0
        cur_col = 0
        
        result = [[0 for _ in range(n)]for _ in range(m)]

        while cur_row < m or cur_col < n:
            if cur_row >= m :
                result[m - 1][cur_col] = colSum[cur_col]
                cur_col += 1
                continue
            elif cur_col >= n:
                result[cur_row][n-1] = rowSum[cur_row]
                cur_row += 1
                continue
            value_to_put = min(rowSum[cur_row], colSum[cur_col])
            rowSum[cur_row] -= value_to_put
            colSum[cur_col] -= value_to_put
            result[cur_row][cur_col] = value_to_put

            if rowSum[cur_row] == 0:
                cur_row += 1
            if colSum[cur_col] == 0:
                cur_col += 1
        
        return result


```

### Output
```
Input
rowSum =
[3,8]
colSum =
[4,7]
Output
[[3,0],[1,7]]
Expected
[[3,0],[1,7]]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>

> Day : Sunday, 21st July 2024

## Build a Matrix With Conditions

[**Question**](https://leetcode.com/problems/build-a-matrix-with-conditions/?envType=daily-question&envId=2024-07-21): 
You are given a  **positive**  integer  `k`. You are also given:

-   a 2D integer array  `rowConditions`  of size  `n`  where  `rowConditions[i] = [abovei, belowi]`, and
-   a 2D integer array  `colConditions`  of size  `m`  where  `colConditions[i] = [lefti, righti]`.

The two arrays contain integers from  `1`  to  `k`.

You have to build a  `k x k`  matrix that contains each of the numbers from  `1`  to  `k`  **exactly once**. The remaining cells should have the value  `0`.

The matrix should also satisfy the following conditions:

-   The number  `abovei`  should appear in a  **row**  that is strictly  **above**  the row at which the number  `belowi`  appears for all  `i`  from  `0`  to  `n - 1`.
-   The number  `lefti`  should appear in a  **column**  that is strictly  **left**  of the column at which the number  `righti`  appears for all  `i`  from  `0`  to  `m - 1`.

Return  _**any**  matrix that satisfies the conditions_. If no answer exists, return an empty matrix.

**Example 1:**

![](https://assets.leetcode.com/uploads/2022/07/06/gridosdrawio.png)

**Input:** k = 3, rowConditions = [[1,2],[3,2]], colConditions = [[2,1],[3,2]]
**Output:** [[3,0,0],[0,0,1],[0,2,0]]
**Explanation:** The diagram above shows a valid example of a matrix that satisfies all the conditions.
The row conditions are the following:
- Number 1 is in row 1, and number 2 is in row 2, so 1 is above 2 in the matrix.
- Number 3 is in row 0, and number 2 is in row 2, so 3 is above 2 in the matrix.
The column conditions are the following:
- Number 2 is in column 1, and number 1 is in column 2, so 2 is left of 1 in the matrix.
- Number 3 is in column 0, and number 2 is in column 1, so 3 is left of 2 in the matrix.
Note that there may be multiple correct answers.

[**Solution**]() : 
###  Solving Method
So the idea here is that we individually align the rowCondition and colCondition

### Java Code 
```java
class Solution {
    public int[][] buildMatrix(int k, int[][] rowConditions, int[][] colConditions) {
        List<Integer> row_sorting = topo_sort(rowConditions, k);
        List<Integer> col_sorting = topo_sort(colConditions, k);
        if (row_sorting.isEmpty() || col_sorting.isEmpty())
            return new int[0][0];

        Map<Integer, int[]> value_position = new HashMap<>();
        for (int n = 1; n <= k; ++n) {
            value_position.put(n, new int[2]);  // element -> [row_index, col_index]
        }
        for (int ind = 0; ind < row_sorting.size(); ++ind) {
            value_position.get(row_sorting.get(ind))[0] = ind;
        }
        for (int ind = 0; ind < col_sorting.size(); ++ind) {
            value_position.get(col_sorting.get(ind))[1] = ind;
        }

        int[][] res = new int[k][k];
        for (int value = 1; value <= k; ++value) {
            int row = value_position.get(value)[0];
            int column = value_position.get(value)[1];
            res[row][column] = value;
        }

        return res;
    }

    // return True if all okay and return False if cycle was found
    private boolean dfs(int src, Map<Integer, List<Integer>> graph, Set<Integer> visited, Set<Integer> cur_path, List<Integer> res) {
        if (cur_path.contains(src)) return false;  // cycle detected
        if (visited.contains(src)) return true;  // all okay, but we've already visited this node

        visited.add(src);
        cur_path.add(src);

        for (int neighbor : graph.getOrDefault(src, Collections.emptyList())) {
            if (!dfs(neighbor, graph, visited, cur_path, res))  // if any child returns false
                return false;
        }

        cur_path.remove(src);  // backtrack path
        res.add(src);
        return true;
    }

    // if there will be cycle - return empty array, in other case return 1d array as described above
    private List<Integer> topo_sort(int[][] edges, int k) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        for (int[] edge : edges) {
            graph.computeIfAbsent(edge[0], x -> new ArrayList<>()).add(edge[1]);
        }

        Set<Integer> visited = new HashSet<>();
        Set<Integer> cur_path = new HashSet<>();
        List<Integer> res = new ArrayList<>();

        for (int src = 1; src <= k; ++src) {
            if (!dfs(src, graph, visited, cur_path, res))
                return Collections.emptyList();
        }

        Collections.reverse(res);  // we will have res as reversed so we need to reverse it one more time
        return res;
    }
}
```

### Output
```
Input
k =
3
rowConditions = [[1,2],[3,2]]
colConditions = [[2,1],[3,2]]
Output
[[3,0,0],[0,0,1],[0,2,0]]
Expected
[[3,0,0],[0,0,1],[0,2,0]]

```

- [Return to TOC](#table-of-contents-dsa)

<hr>


## Template for Solving

[**Question**](): 


[**Solution**]() : 


###  Solving Method


### Python Code 
```python

```

### Output
```


```

- [Return to TOC](#table-of-contents-dsa)

<hr>

# Interview Questions

## Table of Contents interview
1. Infosys Questions
	- [Monster Killing](#monster-killing)
	- [Unique Birthday Gift](#unique-birthday-gift)

- [Template for interview questions](#template-for-interview-questions)


## Monster Killing

**Question**: 
While playing an RPG game, you were assigned to complete one of the hardest quests in this game.
There are n monsters you'll need to defeat in this quest. Each monster i is described with two integer numbers - $power_i$ and $bonus_i$. To defeat this monster, you'll need at least $power_i$ experience points. If you try fighting this monster without having enough experience points, you lose immediately. You will also gain $bonus_i$ experience points if you defeat this monster. You can defeat monsters in any order.
The quest turned out to be very hard - you try to defeat the monsters but keep losing repeatedly. Your friend told you that this quest is impossible to complete. Knowing that, you're interested, what is the maximum possible number of monsters you can defeat? (Question difficulty level: Hardest)

`Input:`
The first line contains an integer, n, denoting the number of monsters.
The next line contains an integer, e, denoting your initial experience.
Each line `i` of the `n` subsequent lines (where `0 ≤ i < n`) contains an integer, $power_i$, which represents power of the corresponding monster.
Each line `i` of the `n` subsequent lines (where `0 ≤ i < n`) contains an integer, $bonus_i$, which represents bonus for defeating the corresponding monster.

**![](https://lh7-us.googleusercontent.com/docsz/AD_4nXeEL9_C8RuW7xw5jKdAgVr2Unws5VJApEUI16lFEtT3iKLfQpk2Zug7Xe0TtXA7fC-oMFTmNM15xDL1z6M6FoyndfVEh5vts9dWdJE81Xa7ASU2aZreO4mvXgExaF2Eh5aKUnLuO47JWZV65QpaGJ83bjE?key=ZHy1vNG2cH9g5PquhAKV5g)**

[**Solution**](https://chatgpt.com/share/15544e13-5a45-49c9-80a7-58e8b5132ac9) : 

> [Stack Overflow Solution](https://stackoverflow.com/questions/68694587/what-is-the-maximum-possible-number-of-monsters-you-can-defeat)

###  Solving Method
This is a relatively simple quesiton where the input will be in the form of a linear array and they have mentioned where to access what given values. WIth this a simple check at each iteration of the loop, to compare the experience of the fighter with the monster will let us know if he can go ahead and defeat it.
1. In this case it isn't mentioned that the user has to defeat them in order and if a weaker monster exists further in the arrya, he can defeat that and gain bonus exp points
2. This will let him defeat the other monsters

:red_circle: **Major note to keep in mind is that I've assumed they're going to be given in a singular array, whereas it is mentioned in the question that they will be individual inputs ( so we are to input them as follows in the terminal line and not pass it as an array )**

### Java Code ( My approach )
```java
import java.util.Arrays;
import java.util.Comparator;

public class MonsterKiller {
    public static void main(String[] args) {
        int[][] arrays = {
            {2, 123, 78, 130, 10, 0},
            {3, 100, 101, 100, 304, 100, 1, 524}
        };

        for (int[] array : arrays) {
            int result = monsterKiller(array);
            System.out.println("Monsters defeated: " + result);
        }
    }

    public static int monsterKiller(int[] array){

        if (array.length == 0){
            return 0;
        }

        int defeated = 0;
        int n = array[0];
        int user_exp = array[1];

        // Here we will initialize the array based on my defined monster arrau
        Monster[] monsters = new Monster[n];
        // This is to input the respective bonus values connected to the each monster
        for(int i =0; i < n; i ++){
            monsters[i] = new Monster(array[i+2], array[i+2+n]);
        }

        // Now the sorting
        Arrays.sort(monsters,Comparator.comparingInt(m -> m.strength));

        // This method is when you have to linearly iterate through an array without needing to use the variable for any other previous checks
        for(Monster monster : monsters){
            if(monster.strength > user_exp){
                return defeated;
            }
            else{
                defeated++;
                user_exp += monster.bonus;
            }
        }       
        
        return defeated;
    }

}

// This class is to create an array of type monster that stores the strength and the bonus value along with it

// This is helpful in learning user defined datatypes that can help in solving questions of such format
// If you don't do this then you'll have to create two loops to manually sort the function instead of depending on the higher order 'sort()' function in the java.util.Arrays package.

class Monster{
    int strength;
    int bonus;

    Monster(int strength, int bonus){
        this.strength = strength;
        this.bonus = bonus;
    }
}

```

### Java code ( Chatgpt approach )
```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.Scanner;

public class RPGGame {
    static class Monster {
        int power;
        int bonus;

        Monster(int power, int bonus) {
            this.power = power;
            this.bonus = bonus;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the number of monsters:");
        int n = scanner.nextInt();

        System.out.println("Enter the initial experience:");
        int e = scanner.nextInt();

        int[] power = new int[n];
        int[] bonus = new int[n];

        System.out.println("Enter the power of each monster:");
        for (int i = 0; i < n; i++) {
            power[i] = scanner.nextInt();
        }

        System.out.println("Enter the bonus for each monster:");
        for (int i = 0; i < n; i++) {
            bonus[i] = scanner.nextInt();
        }

        System.out.println(maxDefeatedMonsters(n, e, power, bonus));
    }

    public static int maxDefeatedMonsters(int n, int e, int[] power, int[] bonus) {
        Monster[] monsters = new Monster[n];
        for (int i = 0; i < n; i++) {
            monsters[i] = new Monster(power[i], bonus[i]);
        }

        Arrays.sort(monsters, new Comparator<Monster>() {
            public int compare(Monster m1, Monster m2) {
                if (m1.power != m2.power) {
                    return Integer.compare(m1.power, m2.power);
                }
                return Integer.compare(m2.bonus, m1.bonus);
            }
        });

        int defeated = 0;
        for (Monster monster : monsters) {
            if (e >= monster.power) {
                e += monster.bonus;
                defeated++;
            } else {
                break;
            }
        }
        return defeated;
    }
}


```

### Python code ( Chatgpt approach )
```python
def max_defeated_monsters(n, e, power, bonus):
    monsters = sorted(zip(power, bonus), key=lambda x: (x[0], -x[1]))
    
    defeated = 0
    for p, b in monsters:
        if e >= p:
            e += b
            defeated += 1
        else:
            break
    return defeated

# Example usage:
if __name__ == "__main__":
    n = int(input("Enter the number of monsters: "))
    e = int(input("Enter the initial experience: "))
    
    power = []
    bonus = []
    
    print("Enter the power of each monster:")
    for _ in range(n):
        power.append(int(input()))
    
    print("Enter the bonus for each monster:")
    for _ in range(n):
        bonus.append(int(input()))
    
    print(max_defeated_monsters(n, e, power, bonus))


```


### Output
```
Monsters defeated: 2
Monsters defeated: 2

```

- [Return to TOC](#table-of-contents-interview)

<hr>

## Unique Birthday Gift

**Question**: 
Your birthday is coming soon and one of your friends, Alex, is thinking about a gift for you. He knows that you really like integer arrays with interesting properties.

He selected two numbers, N and K and decided to write down on paper all integer arrays of length K (in form a[1], a[2], ..., a[K]), where every number a[i] is in range from 1 to N, and, moreover, a[i+1] is divisible by a[i] (where 1 < i <= K), and give you this paper as a birthday present.
Alex is very patient, so he managed to do this. Now you're wondering, how many different arrays are written down on this paper?
Since the answer can be really large, print it modulo 10000.

`Input:`
The first line contains an integer, n, denoting the maximum possible value in the arrays.
The next line contains an integer, k, denoting the length of the arrays.

**![](https://lh7-us.googleusercontent.com/docsz/AD_4nXdBRGNIg5RvwDD3cFVz4smy6sB5uY1bxEJfRIZ9KiPDJE8cnmAgg1jYvn_daF4DwHliXGoaK-q63waVdNjxhXlacj8xAD95uFIuRzJjtlAN4Wg3-cgYSE8qnJsXPgg0q-juqrmROB93pFcj_fRKO2umDcL8?key=ZHy1vNG2cH9g5PquhAKV5g)**

[**Solution**]() : 
###  Solving Method
Use the scanner to accept the maximum possible values for the array and then the length of the arrays

### Java Code 
```java

```

### Output
```


```

- [Return to TOC](#table-of-contents-interview)

<hr>

## Template for interview questions

**Question**: 


[**Solution**]() : 


###  Solving Method


### Python Code 
```python

```

### Output
```


```

- [Return to TOC](#table-of-contents-interview)

<hr>

# Python Study Course 
> [Course Link](https://www.udemy.com/course/pythonforbeginnersintro/learn/lecture/38031990#overview)

## Table of contents
1. [Python String indexing](#python-string-indexing)
2. [Placeholder usage](#placeholder-usage)
3. [Format String](#format-string)
4. [Introduction to Lists in Python](#introduction-to-lists-in-python)
5. [Tuples in Python](#tuples-in-python)
6. [Exercises - Lists, Dictionaries, Tuples](#exercises-2)
7. [Conditional Statments](#conditional-statments)
8. [For Loop](#for-loop)
9. [While Loop](#while-loop) 
10. [Template](#template)


## Python String Indexing

[Return to TOC](#table-of-contents)

- When you are accessing a given specific index of characters from a string then when setting the end index you need to make sure it is +1 than the one you wish to choose, because it's exclusive in nature : 

### Python Code 
```python
sentence  =  "Aaron was playing basketball"
print(sentence[0:6])
print(sentence[0:10])
```

### Output 
```
Aaron 
Aaron was
```

<hr>

##  Placeholder Usage

[Return to TOC](#table-of-contents)

- When you are going to replace certain values obtained after using a method or such while printing a certain statement the usage of placeholders helps in making it easier.

### Python Code
```python
name  =  "Aaron"
sentence  =  "%s is %d years old"
print(sentence  %(name, 21))
# Creating the tuple with names and ages

people  = (
("Aaron", 21),
("Tejas", 22),
("Somesh", 22),
("Prasad", 21),
("Tatvam", 22),
("Mitesh", 22),
("Deepak", 21),
("Viraj", 22)
)
for  name,age  in  people :
print(sentence  %(name,age))
```

### Output :
```
Aaron is 21 years old
Aaron is 21 years old
Tejas is 22 years old
Somesh is 22 years old
Prasad is 21 years old
Tatvam is 22 years old
Mitesh is 22 years old
Deepak is 21 years old
Viraj is 22 years old
```

<hr>

## Exercise 1

[Return to TOC](#table-of-contents)

```python
# Exercise 1 
# 1. Write a script that adds 15 and 30 and divides the sum by 2. Print out the answer.
x = 15
print(f"The output will be {(x + 2*x)/2}")

# 2. Initialize two variables and use arithmetic operators to add, subtract, multiply, divide, and find the remainder.]
x = 20
y = 4

print(f"Performing arithmetic operations on the values {x} and {y} we have : \n Addition :{x+y}\n Subtraction : {x-y} \n Multiplication : {x*y} \n Division : {x/y} \n Remainder : {x%y}")

# 3.Create a variable called name and store your name in it as a string.

name = "Aaron"

# 4. Create three variables in one line and assign each one a different food item.

x, y, z = "Orange","Carpaccio","Croissant"
sentence = "Some food items are : %s %s %s"
print(sentence %(x, y, z))

# 5. Print out "Hello" ten times using arithmetic operators.

word = "Hello "
print(word*10)

# 6. Set your name and age variables in one line with multiple assignment

name, age = "Aaron", 21
print("My name is %s and I am %d years old" %(name,age))

# 7. Create two strings and then create a third variable combining both of the two original strings.

x, y, z = "Mango", "Ice-cream", x+" "+y
print(z)


# 8. Create a string and print the fourth letter of the word.

game = "Basketball"
print(game[3])

# 9. Create a string and print the letters from index 0 to 5.

person = "Rajesh Adhau"
print(person[0:6])

# 10. Create a variable and print all the letters from the first index until the end.

sentence = "The cricket event was extremely long"
print(sentence[1:])
```

### Output
```
The output will be 22.5
Performing arithmetic operations on the values 20 and 4 we have :
 Addition :24
 Subtraction : 16
 Multiplication : 80
 Division : 5.0
 Remainder : 0
Some food items are : Orange Carpaccio Croissant
Hello Hello Hello Hello Hello Hello Hello Hello Hello Hello   
My name is Aaron and I am 21 years old
k
Rajesh
he cricket event was extremely long
```


<hr>

##  Format String

[Return to TOC](#table-of-contents)

- The main idea is this allows you to incorporate strings directly into sentences without having to break continuity and it also allows you to use expressions within curly braces 

### Python Code
```python
name="Aaron"
print(f"Hello {name}")

x = 10 
y = 20
print(f" The sum of x and y is {x + y}")
```

### Output :
```
Hello Aaron
The sum of x and y is 30
```

<hr>

## Introduction to Lists in Python

[Return to TOC](#table-of-contents)

> This is a **List** not a **Linked List**

### Python Code
```python
#Introduction to Lists
shopping_list = ['apples', 'oranges bananas cheese']

# add items to our list
shopping_list.append('blueberries')

#update items in our list
shopping_list[0] = 'cherries'

del shopping_list[1]
print(shopping_list)

list_num = [1, 4, 5, 24, 6]
print(max(list_num))
print(min(list_num))
```

1. This will let us create a list ( array of strings basically )
2. We can add items using the _append()_ function
3. We can access them by their index values and finally we can delete them by typing <br>_del shopping_list[index]_
4. Also you can get the maximum using the _max()_ function and minimum using _min()_

<hr>

## Introduction to Dictionaries

[Return to TOC](#table-of-contents)

### Python Code 
```python
students = {'bob':12,'rachel':13, 'emily':15}
# Define the dictionary

print(students['rachel'])
# This will print the respective value associated with the key

students['rachel'] = 14

del students['emily']

print(len(students))
# This will print the entire dictionary 
```

### Output
```
13
2
```

### Information Learned
1. You cannot use the same keys / key names in a dictionary since it will create conflict when calling the value related to it.

<hr>

## Tuples in Python

[Return to TOC](#table-of-contents)

### Python Code 
```python
# Introduction to Tuples
# Tuples are immutable - they can't be modified

tup = ("oranges", "apples", "bananas")
#tup[0] = "cherries"
# The above code will throw us an error
print(tup[0:2])
print(tup)

# even though we can't modify tuples we can create new tuples by concatenating two different tuples
tup2 = (14, 16)
tup3 = tup + tup2

```

### Output
```
('oranges', 'apples')
('oranges', 'apples', 'bananas')

```

### Information Learned
Learned how tuples are immutable, but a new tuple can be made by combining two other tuples.

<hr>

## Exercises 2

[Return to TOC](#table-of-contents)

### Python Code 
```python
#1. Create a list of names and print the second item. 
names = ['Aaron','Tejas','Akhilesh','Rishikesh']
print(names[1])

#2. Create a list of sports and then replace the second item with another sport.
sports = ['Basketball','Cricket','badminton','volleyball','squash']
sports[1] = 'Swimming'
print(sports)

#3. Create a list containing numbers and delete the fifth number from the array.
num_list = [1, 5, 7, 21, 13, 12]
del num_list[4]
print(num_list)

#4. Create two lists of numbers and merge them.
list1 = [1, 7, 6, 2, 15, 13,12]
list2 = [6, 18, 21, 10, 13]
list3 = list1 + list2
print(list3)

#5. Create a list of numbers and find the length, minimum, and maximum.
list_num = [1, 7, 6, 2, 15, 13,12]
print(len(list_num))
print(min(list_num))
print(max(list_num))

##6. Create a dictionary of students and scores and print out a student’s score.
scores = {'Aaron': 100, 'Nandini': 99, 'Devansh': 59, 'Akhil':78 }
print(scores['Aaron'])


#7. Create a dictionary with the key being names and values being ages and then delete the second key/value pair.
person_dict = {'Shravan':22, 'Ayan':21, 'Hasnain':24, 'Delilah':25}
print(person_dict)
del person_dict['Ayan']
print(person_dict)

#8. Create a dictionary of names and ages and then print out all the keys and values
person_dict = {'Shravan':22, 'Ayan':21, 'Hasnain':24, 'Delilah':25}
print(person_dict)

#9. Create a tuple of your favorite movies
tup = ('How to Train your Dragon','How to train your dragon:Riders of Berk','How to train your dragon 3')


#10. Create a tuple and print all the items from the first to third index.
Grocery_tuple =('Milk','Tomatoes','Potatoes','Bananas')
print(Grocery_tuple)

```

### Output
```
Tejas
['Basketball', 'Swimming', 'badminton', 'volleyball', 'squash']
[1, 5, 7, 21, 12]
100
{'Shravan': 22, 'Ayan': 21, 'Hasnain': 24, 'Delilah': 25}     
{'Shravan': 22, 'Hasnain': 24, 'Delilah': 25}
{'Shravan': 22, 'Ayan': 21, 'Hasnain': 24, 'Delilah': 25}     
('Milk', 'Tomatoes', 'Potatoes', 'Bananas')

```

<hr>

## Conditional Statments

[Return to TOC](#table-of-contents)

### Python Code 
```python
if 3 < 2 :
    print('hello')
else :
    print('Math makes no sense anymore')

age = 17

if age <= 15 :
    print("You are younger than 16")
elif age == 16 : 
    print("You are 16 years old")
else :
    print ("You are older than 16 years old by %d year(s)" %(age - 16))

# Similarly you can create more elifs to check if someone is a child, teenager or an adult


```

### Output
```
Math makes no sense anymore
You are older than 16 years old by 1 years

```


<hr>

## For Loop

[Return to TOC](#table-of-contents)

### Python Code 
```python
# In the for loop if we define a range then the ending value is excluded.

for i in range (0,11):
    print(i)

# This will only iterate from 0 to 10

# Another nice trick is you can add an additional number that will create a condition

for i in range(0, 11, 2):
    print(i)

# This will print all even numbers between 1 to 10 ( so numbers divisible by 2 )

for i in range(5, 51, 5):
    print(i)

# NEsted for loops are quite powerful

for i in range(0,5):
    for j in range(0,3):
        print(i*j)

# Example 2D array
array = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Iterating using nested for loops
for row in array:
    for element in row:
        print(element, end=' ')
    print()  # For new line after each row
```

### Output
```
0
1
2
3
4
5
6
7
8
9
10
0
2
4
6
8
10
5
10
15
20
25
30
35
40
45
50
0
0
0
0
1
2
0
2
4
0
3
6
0
4
8

1 2 3 
4 5 6 
7 8 9 

```

<hr>

## While loop

[Return to TOC](#table-of-contents)

### Python Code 
```python
# There are 3 control statments we can use to affect the flow of a given loop:
# break, continue, pass

a = b = c = 0

while a <5 :
    a = a + 1
    if a == 3:
        break
    print(a)


while b <5 :
    b = b + 1
    if b == 3:
        continue
    print(b)
# here when the value of c == 3 it will skip the remaining statements and continue to the for while loop condition again.
# pass is nothing but a placeholder and helps you structure your code

while c <5 :
    c = c + 1
    if c == 3:
        pass
    print(c)

```

### Output
```
1
2
1
2
4
5
1
2
3
4
5

```
<hr>

## Try and Except Statements

[Return to TOC](#table-of-contents)

### Python Code 
```python
# Try and Except

try :
    if name > 3:
        print("hello")
except Exception as e:
    print(f"An error was detected in your code, with the following error  : {e}")



```

### Output
```
An error was detected in your code, with the following error  : name 'name' is not defined

```

<hr>

## Function

[Return to TOC](#table-of-contents)

### Python Code 
```python

def hello_world():
    print("Hello World!")

def greeting(name):
    print(f"Hi {name}")

def add(num1, num2):
    return num1 + num2

def mul(num1, num2):
    return num1*num2

greeting("Aaron")
num_sum = add(10, 15)
print(num_sum)
print(mul(add(1,2),add(3,4)))

```

### Output
```
Hi Aaron
25
21

```


<hr>

## Template

[Return to TOC](#table-of-contents)

### Python Code 
```python


```

### Output
```


```

### Information Learned


<hr>

# Java Functions

## Table of Contents Java Functions
1. [Strings](#strings)
2. [String Builder](#string-builder)
3. [Scanner to accept input](#scanner-to-accept-input)



## Strings

> [Return to Table of Contents](#table-of-contents-java-functions)

Within Java on a `String` there are various functions that can be used for varying kinds of purposes. These are the different kinds of functions along with the purpose for which they've been implemented : 


1. **`length()`**:
   - **Description**: Returns the number of characters in the string.
   - **Usage**: `int len = str.length();`
   - **Limits**: None, but be aware that it returns `0` for an empty string.

2. **`charAt(int index)`**:
   - **Description**: Returns the character at the specified index.
   - **Usage**: `char c = str.charAt(0);`
   - **Limits**: Throws `IndexOutOfBoundsException` if the index is out of range.

3. **`substring(int beginIndex, int endIndex)`**:
   - **Description**: Returns a new string that is a substring of the original string.
   - **Usage**: `String sub = str.substring(1, 4);`
   - **Limits**: Throws `IndexOutOfBoundsException` if the indices are out of range.

4. **`substring(int beginIndex)`**:
   - **Description**: Returns a new string that starts from the specified index to the end of the original string.
   - **Usage**: `String sub = str.substring(2);`
   - **Limits**: Throws `IndexOutOfBoundsException` if the index is out of range.

5. **`equals(Object anObject)`**:
   - **Description**: Compares this string to the specified object for equality.
   - **Usage**: `boolean isEqual = str1.equals(str2);`
   - **Limits**: Returns `false` if the object is not a string or is `null`.

6. **`equalsIgnoreCase(String anotherString)`**:
   - **Description**: Compares this string to another string, ignoring case considerations.
   - **Usage**: `boolean isEqual = str1.equalsIgnoreCase(str2);`
   - **Limits**: None, but returns `false` if the other string is `null`.

7. **`compareTo(String anotherString)`**:
   - **Description**: Compares two strings lexicographically.
   - **Usage**: `int result = str1.compareTo(str2);`
   - **Limits**: Returns a negative integer, zero, or a positive integer if this string is lexicographically less than, equal to, or greater than the specified string.

8. **`compareToIgnoreCase(String str)`**:
   - **Description**: Compares two strings lexicographically, ignoring case considerations.
   - **Usage**: `int result = str1.compareToIgnoreCase(str2);`
   - **Limits**: Same as `compareTo`.

9. **`contains(CharSequence s)`**:
   - **Description**: Returns `true` if the string contains the specified sequence of characters.
   - **Usage**: `boolean hasSubstring = str.contains("abc");`
   - **Limits**: Returns `false` if the sequence is not found.

10. **`startsWith(String prefix)`**:
    - **Description**: Tests if this string starts with the specified prefix.
    - **Usage**: `boolean starts = str.startsWith("abc");`
    - **Limits**: Returns `false` if the prefix is not found.

11. **`endsWith(String suffix)`**:
    - **Description**: Tests if this string ends with the specified suffix.
    - **Usage**: `boolean ends = str.endsWith("xyz");`
    - **Limits**: Returns `false` if the suffix is not found.

12. **`indexOf(int ch)`**:
    - **Description**: Returns the index within this string of the first occurrence of the specified character.
    - **Usage**: `int index = str.indexOf('a');`
    - **Limits**: Returns `-1` if the character is not found.

13. **`indexOf(String str)`**:
    - **Description**: Returns the index within this string of the first occurrence of the specified substring.
    - **Usage**: `int index = str.indexOf("abc");`
    - **Limits**: Returns `-1` if the substring is not found.

14. **`lastIndexOf(int ch)`**:
    - **Description**: Returns the index within this string of the last occurrence of the specified character.
    - **Usage**: `int index = str.lastIndexOf('a');`
    - **Limits**: Returns `-1` if the character is not found.

15. **`lastIndexOf(String str)`**:
    - **Description**: Returns the index within this string of the last occurrence of the specified substring.
    - **Usage**: `int index = str.lastIndexOf("abc");`
    - **Limits**: Returns `-1` if the substring is not found.

16. **`toLowerCase()`**:
    - **Description**: Converts all characters in the string to lowercase.
    - **Usage**: `String lower = str.toLowerCase();`
    - **Limits**: None, but the original string remains unchanged.

17. **`toUpperCase()`**:
    - **Description**: Converts all characters in the string to uppercase.
    - **Usage**: `String upper = str.toUpperCase();`
    - **Limits**: None, but the original string remains unchanged.

18. **`trim()`**:
    - **Description**: Returns a copy of the string with leading and trailing whitespace removed.
    - **Usage**: `String trimmed = str.trim();`
    - **Limits**: None, but does not remove whitespace in the middle of the string.

19. **`replace(char oldChar, char newChar)`**:
    - **Description**: Returns a new string resulting from replacing all occurrences of `oldChar` with `newChar`.
    - **Usage**: `String replaced = str.replace('a', 'b');`
    - **Limits**: None, but the original string remains unchanged.

20. **`replace(CharSequence target, CharSequence replacement)`**:
    - **Description**: Replaces each substring of this string that matches the literal target sequence with the specified literal replacement sequence.
    - **Usage**: `String replaced = str.replace("old", "new");`
    - **Limits**: None, but the original string remains unchanged.

21. **`split(String regex)`**:
    - **Description**: Splits this string around matches of the given regular expression.
    - **Usage**: `String[] parts = str.split(",");`
    - **Limits**: The regex must be valid; otherwise, `PatternSyntaxException` is thrown.

22. **`isEmpty()`**:
    - **Description**: Returns `true` if the string is empty (`length() == 0`).
    - **Usage**: `boolean empty = str.isEmpty();`
    - **Limits**: None.

23. **`matches(String regex)`**:
    - **Description**: Tells whether or not this string matches the given regular expression.
    - **Usage**: `boolean matches = str.matches("[a-z]+");`
    - **Limits**: The regex must be valid; otherwise, `PatternSyntaxException` is thrown.

24. **`toCharArray()`**:
    - **Description**: Converts this string to a new character array.
    - **Usage**: `char[] charArray = str.toCharArray();`
    - **Limits**: None.

25. **`format(String format, Object... args)`**:
    - **Description**: Returns a formatted string using the specified format string and arguments.
    - **Usage**: `String formatted = String.format("Hello, %s!", name);`
    - **Limits**: The format string and arguments must be compatible; otherwise, `IllegalFormatException` is thrown.

These methods provide a broad range of functionality for manipulating and inspecting strings in Java.

<hr>

## String Builder

> [Return to Table of Contents](#table-of-contents-java-functions)

A string builder is something we can use to be able to perform actions on a given string, since strings in Java are immutable.
[Usage of String builder](#stringbuilder-usage)

<hr>

## Scanner to accept input
> [Return to Table of Contents](#table-of-contents-java-functions)

```java

import  java.util.Scanner;
public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        

    }

```



<hr>

# Python Functions
## Table of Contents Python Functions
1. 





> [Return to Table of Contents](#table-of-contents-python-functions)

<hr>
