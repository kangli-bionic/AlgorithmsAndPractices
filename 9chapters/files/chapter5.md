- Part 1: Quick Sort, Merge Sort
- Part 2: Quick Select


|Alg|Time Complexity|Space Complexity|Stability*|DC time*|
|-|-|-|-|-|
|快速排序（Quick Sort）|Avg: O(nlogn); Worst: O(n^2)*|O(1) in place|Not|Do O(n) first|
|归并排序（Merge Sort）|Theta(nlogn)|O(n)*|Yes|Do T(n/2) first|
||


Note *:

1. The **worst case** is when the array is already sorted but pivot select the arr[0] every time, making it become O(1) + O(n^2) => O(n^2).
2. Merge Sort need a seperate new **temporary array** to store.
3. An example for **stability** is that to sort array {2, 1, 1, 2} and we label the two 2s as 2' and 2'' respectively. So we want {2', 1, 1, 2"} to become to {1, 1, 2', 2"} which is called having stability. 
4. When we use **Divide and Conquer (DC)** algorithm we calculate the running time using T(n) = 2T(n/2) + O(n). The QS does the O(n) first. This is called 先整体有序，再局部有序. While MS does the T(n/2) first. This is 先局部有序，在整体有序.

三个要点：
<img src="files/chapter5_3keypoints.png">


[Quick Sort web](https://www.jiuzhang.com/problem/quick-sort/) or local.
[Merge Sort web](https://www.jiuzhang.com/problem/merge-sort/) or local.

### LC:

[463. Sort Integers](lintcode/463.Sort_Integers.md) QS MS

[1153. string sorting](lintcode/1153.string_sorting.md) QS

[6. Merge Two Sorted Arrays](lintcode/6.Merge_Two_Sorted_Arrays.md) MS

[532. Reverse Pairs](532.Reverse_Pairs.md) MS


## Quick Select

找到n个无序元素中的第K大元素，最简单的办法就是将所有元素排序，再去找第k个元素。但实际上，这个过程中会有许多冗余的操作，我们可以进行一些优化，也就是使用接下来要讲的quick select算法。

### 快速选择算法的 Partition 的实质：

快速选择/快速排序中的 partition 是 可左可右 的partition，也就是说，对于nums[i] == pivot 时，这个数字既可以放在左边，也可以放在右边。

### 为什么这样划分数组呢？

原因是为了避免出现类似 [1,1,1,1,1,1] 的数组中的元素，全部被分到一边的情况。我们让 nums[i] == pivot 的情况既不属于左边也不属于右边，这样就能够让 partition 之后的结果稍微平衡一些。
如果 quick select / quick sort 写成了nums[i] < pivot 在左侧，nums[i] >= pivot 在右侧这种形式，就会导致划分不平均，从而导致错误或者超时。

### 为什么问题《partition array》不能使用同样的代码？

对于问题《partition array》来说，题目的要求是将数组划分为两个部分，一部分满足一个条件，另外一部分不满足这个条件，所以可以严格的把 nums[i] < pivot 放在左侧，把 nums[i] >= pivot 放在右侧，这样子做完一次 partition 之后，就能够将这两部分分开。

### 总结

简单的说就是，quick select 和 quick sort 的 partition 目标不是将数组 严格的按照 nums[i] < pivot 和nums[i] >= pivot 去拆分开，而是只要能够让左半部分 <= 右半部分即可。这样子 nums[i] == pivot 放在哪儿都无所谓，两边都可以放。

### LC:
[5. Kth Largest Element](5.Kth_Largest_Element.md) Quick Select

[80. Median](80.Median.md) Q select

[148. Sort Colors](148.Sort_Colors.md) Q select.
