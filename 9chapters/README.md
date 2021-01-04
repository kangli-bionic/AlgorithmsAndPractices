# Notes for 9 chapters Algorithms Course 2020

([Go back to respository ReadMe](../README.md))

---

This is my notes for the 9 chapters Algorithms course 2020. Mainly contains the exercise problesm and code and solutinos.

Class notes are inside Notability. Recorded video are also provided. 

# Contents:
- [Two Pointers Algorithm](#2p)
- [Recursion/Stack/Heap/Tree](#rec)
- [二分法](#divide)
- [Queue](#q)
- [BFS + Graph](#bfs)
- [分治法](#dc)
- [DFS](#dfs)
- [HashMap Heap](#hash)


</br>

# [第一章【视频】FB面试官揭秘算法面试速成技巧 - 怎样做到 Bug Free 和刷100题等于别人刷300题](nb_第一章_FB面试官揭秘算法面试速成技巧.pdf) 
详见notability

# [第二章【互动】真实面试案例分析（上）与面试评分标准](nb_2._真实面试案例分析上)
详见notability

- Part 1 Longest palindromic substring
- Part 2 双指针 与 DP 解法.
- Part 3 面试评分体系 and Coding Quality. 


### LC:
<table>
<tr>
<td>

[200. Longest Palindromic Substring](https://www.lintcode.com/problem/longest-palindromic-substring/description), [sol](https://www.jiuzhang.com/solution/longest-palindromic-substring/)

</td>
<td>

[667. Longest Palindromic Subsequence](https://www.lintcode.com/problem/longest-palindromic-subsequence/description), [sol](https://www.jiuzhang.com/problem/longest-palindromic-subsequence)
</td>
</tr>
</table>

# [第三章【互动】真实面试案例分析（下）与80%求职者会踩坑的基础知识](files/chapter3.md)

- Part 1 strStr and Rabin-Karp. 
- Part 2 String 的坑.
- Part 3 Greedy Alg.

### LC:
<table>
<tr>
<td>

[13. Implement strStr()](https://www.lintcode.com/problem/implement-strstr/description), [sol](https://www.jiuzhang.com/problem/implement-strstr)

</td>
<td>

[128. Hash Function](https://www.lintcode.com/problem/hash-function/description), [sol](https://www.jiuzhang.com/problem/hash-function/) 

</td>
<td>

[594. strStr II](https://www.lintcode.com/problem/strstr-ii/description), [sol](https://www.jiuzhang.com/problem/strstr-ii)

</td>
<td>

Greedy Alg [187. Gas Station](https://www.lintcode.com/problem/gas-station/description), [sol](https://www.jiuzhang.com/problem/gas-station)

</td>

</tr>
</table>

</br>

([Go back to respository ReadMe](../README.md))

---
---
---
# 🔴 <span id="2p" style="color:purple">  ***Two Pointers Algorithm***:</span>


# 第四章【互动】复杂度理论与双指针算法入门

- Part 1 Timing and Space complexity. 
- Part 2 三种双指针算法 two pointers
- Part 3 Use 2 pointers: Valid Palindrome & Valid Palindrome II
- Part 4 Two Sum: HashTable, Sort + 2 pointers, Follow Up Qs



### 学好时间复杂度，有很多帮助，比如：
1. 面试官会问你的算法，时间复杂度是多少
2. 当面试官说，有没有更好的方法时，你知道朝什么样的复杂度优化
3. 利用时间复杂度倒推算法是面试常用技巧。如 O(logN)的算法几乎可以确定是二分法。

### 三种双指针算法
1. 相向双指针 （判断回文串）
   - Two Sum type
     - sum of two numbers. ( [56. Two Sum](lintcode/56.twosum.md); [608. Two Sum II - Input array is sorted](lintcode/608.Two_Sum_II_Input_array_is_sorted.md); [609. Two Sum - Less than or equal to target](lintcode/609.Two_Sum_Less_than_or_equal_to_target.md)  )
     - sum of three numbers. ( [57. 3 Sum](lintcode/57.3sum.md))
   - Reverse type     
     - 判断回文串 palindrome. ( [415. Valid Palindrome](lintcode/415.Valid_Palindrome.md) ; [891. Valid Palindrome II](lintcode/891.Valid_Palindrome_II.md) )
     - 翻转字符串 flip string. 
   - Partition type
     - quick sort. ( [31. Partition Array](lintcode/31.Partition_Array.md) )
     - color sort.
2. 背向双指针 （最长回文串）
3. 同向双指针  

### Two Sum

||Time Complexity|Space Complexity|
|-|-|-|
|Use HashTable| O(n)|O(n)|
|USe sort + 2 pointers|O(nlogn)|O(1)|

Follow Up:
1. What is sorted already?
2. If require you to return the indices. 
3. Two Sum <= target.

</br>

([Go back to respository ReadMe](../README.md))

</br>

# ***Two Pointers Algorithm 2***:

# [第五章【互动】必须熟练掌握的两个排序算法](files/chapter5.md)
- Part 1: Quick Sort, Merge Sort
- Part 2: Quick Select

|Alg|Time Complexity|Space Complexity|Stability*|DC time*|
|-|-|-|-|-|
|快速排序（Quick Sort）|Avg: O(nlogn); Worst: O(n^2)*|O(1) in place|Not|Do O(n) first|
|归并排序（Merge Sort）|Theta(nlogn)|O(n)*|Yes|Do T(n/2) first|
||

</br>

# ***Two Pointers Algorithm 3***:
# 第八章【视频】高频算法之王——双指针算法之相向双指针



([Go back to respository ReadMe](../README.md))

---
---
---
# 🔴 <span id = "rec" style="color:purple" >***Recursion/Stack/Heap/Tree*** :</span>
# [插入章 Recursion/Stack/Heap/Tree](files/recursion.md)
- Part 1 递归三要素 Recursion 3 key parts 
- Part 2 递归调用栈 (内存的堆栈 函数调用栈) Recursion with stack and heap 
- Part 3 值传递与引用传递 Pass by value vs Pass by reference 
- Part 4 综合训练 More practices 


---
---
---
# 🔴 <span id = "divide" style="color:purple"> ***二分法***：</span>
# [第六章【互动】时间复杂度为O(logN)的高频算法——二分法](files/chapter6.md)

- Part 1 时间复杂度 - 用 T 函数表示法计算时间复杂度
- Part 2 递归与二分法
- Part 3 空间复杂度 - 内存中的栈空间与堆空间
- Part 4 什么是递归深度


</br>

([Go back to respository ReadMe](../README.md))

# ***二分法 2***：
# [第七章【互动】一个不会出现死循环的通用二分法模板](files/chapter7.md)
- 二分查找模版
- 四个要点

</br>

([Go back to respository ReadMe](../README.md))

# ***二分法 3***：
# 第九章【视频】简约而不简单——二分法学习的四重境界

---
---
---

# 🔴 <span id = "q" style="color:purple">***Queue***:</span>
# [第十章【互动】队列知识点从易到难](files/chapter10.md)
- Part 1: Queue 
- Part 2: Implement queue using array and its issue
- Part 3: Implement queue using LinkedList, Implement Circular queue using array
- Part 4: Java Queue Interface, Java Basis: Interface Set Map List Queue
- Part 5: Java Basis: Interface vs Abstract Class

</br>

([Go back to respository ReadMe](../README.md))


---
---
---
# 🔴 <span id = "bfs" style="color:purple">***BFS + Graph***:</span>
# [第十一章【互动】宽度优先搜索与图论入门](files/chapter11.md)
- Part 1: BFS 3种适用场景
- Part 2: BFS 3种实现方法：单队列，双队列，DummyNode
- Part 3: 图，二叉树的BFS和图的BFS
- Part 4: 如何定义图的数据结构：邻接矩阵，邻接表

# 第十四章【视频】性价比之王——宽度优先搜索


</br>

([Go back to respository ReadMe](../README.md))


---
---
---

# 🔴 <span id = "dc" style="color:purple">***分治法***:</span>

# [第十二章【互动】用递归实现遍历法和分治法](files/chapter12.md)
- Part 1: 递归、DFS和回溯的的关联和区别
- Part 2: 使用回溯的时机
- Part 3: 从两个不同的角度：遍历（亲力亲为）和分治（分配任务）来看待问题. 遍历法与分治法的联系与区别

# [第十三章【互动】使用非递归实现二叉树的遍历](files/chapter13.md)
- Part 1: 二叉树的中序遍历的非递归实现
- Part 2: 另一种中序遍历的非递归实现
- Part 3: 浅拷贝和深拷贝


# 第十五章【视频】解决99%二叉树问题的算法——分治法


</br>

([Go back to respository ReadMe](../README.md))

---
---
---

# 🔴 <span id = "dfs" style="color:purple">***DFS***:</span>
# [第十六章【互动】组合类DFS](files/chapter16.md)

求所有可能方案 90% -> 用搜索来解 -> 用DFS

- Part 1 用DFS来解决在隐式图上的组合问题, 17.subset两个解法 DFS
- Part 2 18.subset ii 两个解法 DFS+Hash

# [第十七章【互动】排列类DFS](files/chapter17.md)



# 第二十章【视频】刷人利器——深度优先搜索

# 🔴 <span id = "hash" style="color:purple">***HashMap Heap***:</span>

[第十八章【互动】哈希表的原理](files/chapter18.md)

第十八章【互动】哈希表的原理1.mov
第十八章【互动】哈希表的原理2 - rehash.mov

[第十九章【互动】堆的基本原理](files/chapter19.md)

第二十一章【视频】高频数据结构——哈希表与堆


---
([Go back to respository ReadMe](../README.md))
