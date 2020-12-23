# Part 1 时间复杂度 - 用 T 函数表示法计算时间复杂度
# Part 2 递归与二分法
# Part 3 空间复杂度 - 内存中的栈空间与堆空间
# Part 4 什么是递归深度

----

# Part 1 时间复杂度 - 用 T 函数表示法计算时间复杂度

在这一节课中，我们要来通过递归来了解二分的基础知识。首先我们要对上一节课中时间复杂度分析进行一些扩充，来了解一下T函数推导法

接下来我们来接受一种计算时间复杂度的方法 --- 用 T 函数表示法计算时间复杂度。

用 T 函数表示法计算时间复杂度
T 函数推导法

我们介绍一种时间复杂度的推导方法：
## ***T函数推导法***


比如二分法。二分法是每次通过 O(1) 的时间将规模为 n 的问题降低为规模为 n/2的问题。

这里我们用 T(n) 来表示规模为 n 的问题在该算法下的时间复杂度，那么我们得出推导公式：

```
T(n) = T(n/2) + O(1)
```

我们来逐个说明一下这个公式的意义。

首先 T 代表的是 Time Complexity,n 代表的是问题规模（二分法里就是数组的大小）。

那么 T(n) 代表的就是：**求处理问题规模为n的数据的时间复杂度是多少**。注意这里是一个问句，不是一个答案。

T(n) 根据算法的不同可以是O(n), 也可以是 O(nlogn)或任何值，而 O(n) 就是 O(n)。

然后 O 代表的是时间复杂度。O(1) 就意味着，你大概用一个 if 语句，或者简单的加加减减，就可以完成。O 在这里的意思是数量级约等于。在 O 的世界里，我们只考虑最高项是什么，不考虑系数和常数项。比如：

O(100n) = O(n)

O(n^2 + n) = O(n^2)

O(2^n + n^2 + 10) = O(2^n)

## ***如何推导 T 函数***

我们可以使用不断展开的方法进行推导：
```
T(n) = T(n/2) + O(1)
     = T(n/4) + O(1) + O(1)
     = T(n/8) + O(1) * 3
     = T(n/16) + O(1) * 4
     ...
     = T(1) + O(1) * logn
     = O(logn)
```

在时间复杂度的领域里，有如下的一些性质：

1. T(1) = O(1)// 解决规模为1的问题通常时间复杂度为O(1)。这个不100%对，但是99.9%的情况下都是如此。
2. k * O(n) = O(kn)
3. O(n) + O(m) = O(n + m)


上面的方法，是采用 T 函数展开的方法，将二分法的时间复杂度最终用 O(...) 来表示


### **那我们了解时间复杂度有什么用呢？**

- 在做题过程中，如果知道题目的数据范围，我们可以通过数据范围估算时间复杂度，***再根据时间复杂度估计算法***。

### **算法中，常见的时间复杂度有：**

|复杂度	|可能对应的语法|	备注|
|-|-|-|
|O(1)	|位运算	|常数级复杂度，一般面试中不会有|
|O(logn)	|二分法，倍增法，快速幂算法，辗转相除法	||
|O(n)	|枚举法，双指针算法，单调栈算法，KMP算法，Rabin Karp，Manacher's Algorithm|	又称作线性时间复杂度|
|O(nlogn)	|快速排序，归并排序，堆排序	||
|O(n^2)	|枚举法，动态规划，Dijkstra	||
|O(n^3)	|枚举法，动态规划，Floyd	||
|O(2^n)	||与组合有关的搜索问题	|
|O(n!)	||与排列有关的搜索问题|
||

在面试中，经常会涉及到时间复杂度的计算。当你在对于一个问题给出一种解法之后，面试官常会进一步询问，是否有更优的方法。此时就是在问你是否有时间复杂度更小的方法（有的时候也要考虑空间复杂度更小的方法），这个时候需要你对常用的数据结构操作和算法的时间复杂度有清晰的认识，从而分析出可优化的部分，给出更优的算法。

例如，给定一个已经排序的数组，现在有多次询问，每次询问一个数字是否在这个数组中，返回True or False.
- 方法1： 每次扫描一遍数组，查看是否存在。
这个方法，每次查询的时间复杂度是: O(n)。

- 方法2：由于已经有序，可以使用二分查找的方法。
这个方法，每次查询的时间复杂度是: O(logn)。

- 方法3：将数组中的数存入Hashset。
这个方法，每次查询的时间复杂度是: O(1)。

可以看到，上述的三种方法是递进的，时间复杂度越来越小。

在面试中还有很多常见常用的方法，他们的时间复杂度并不是固定的，都需要掌握其时间复杂度的分析，要能够根据算法过程自己推算出时间复杂度。


# Part 2 递归与二分法

接下来我们就来看一下二分算法。在这一小节中，我们主要是要使用递归的方式来实现二分，因此我们先来看一下什么是递归。


递归要考虑的3个点：
1. 递归的定义： 函数接受什么样的参数，返回什么样的值，代表什么样的意思
2. 递归的拆解
3. 递归的出口



<img src="chapter6.png">

LC:

[366. Fibonacci](../lintcode/366.Fibonacci.md)

整个递归的流程你是否掌握了呢？

对于下面的两个递归代码块，如果在函数体外部调用了solve(5)，整个的执行流程是什么样子的呢？

请稍加思考再点击下面的【继续】按钮哦~
```
int solve(int x) {
    if (x == 1) {
        return x;
    }
    return solve(x - 1) + 1;
}
def solve(x):
    if x == 1:
        return x
    return solve(x - 1) + 1
```

<img src="chapter6-2.png">

那么如何用递归的方式来写二分法呢，我们可以看下面这个视频了解一下

# Part 3 空间复杂度 - 内存中的栈空间与堆空间

在视频中我们提到了stack Overflow, 那什么是 stack overflow呢，我们首先要来了解几个基础概念：内存中的栈空间和堆空间是什么？

为了分析这种写法的空间复杂度，我们需要了解一下内存中，栈和堆占用了多少空间

## 内存中的栈空间与堆空间

我们通常所说的内存空间，包含了两个部分：栈空间（Stack space）和堆空间（Heap space）

当一个程序在执行的时候，操作系统为了让进程可以使用一些固定的不被其他进程侵占的空间用于进行函数调用，递归等操作，会开辟一个固定大小的空间（比如 8M）给一个进程使用。这个空间不会太大，否则内存的利用率就很低。这个空间就是我们说的栈空间，Stack space。

我们通常所说的栈溢出（Stack Overflow）是指在函数调用，或者递归调用的时候，开辟了过多的内存，超过了操作系统余留的那个很小的固定空间导致的。那么哪些部分的空间会被纳入栈空间呢？栈空间主要包含如下几个部分：

- 函数的参数与返回值
- 函数的局部变量

我们来看下面的这段代码：

Java:
```Java
public int f(int n) {
    int[] nums = new int[n];
    int sum = 0;
    for (int i = 0; i < n; i++) {
        nums[i] = i;
        sum += i;
    }
    return sum;
}
```
python:
```Python
def f(n):
    nums = [0]*n  # 相当于Java中的new int[n]
    sum = 0
    for i in range(n):
        nums[i] = i
        sum += i
    return sum
```    
C++:
```C++
int f(int n) {
   int *nums = new int[n];
    int sum = 0;
    for (int i = 0; i < n; i++) {
        nums[i] = i;
        sum += i;
    }
    return sum;
}
```

根据我们的定义，参数 n，最后的函数返回值f，局部变量 sum 都很容易的可以确认是放在栈空间里的。那么主要的难点在 nums。

这里 nums 可以理解为两个部分：

- 一个名字叫做 nums 的局部变量，他存储了指向内存空间的一个地址（Reference），这个地址也就是 4 个字节（32位地址总线的计算机，地址大小为 4 字节）

- new 出来的，一共有 n 个位置的整数数组，int[n]。一共有 4 * n 个字节。

这里 nums 这个变量本身，是存储在栈空间的，因为他是一个局部变量。但是 nums 里存储的 n 个整数，是存储在堆空间里的，Heap space。他并不占用栈空间，并不会导致栈溢出。

在大多数的编程语言中，特别是 Java, Python 这样的语言中，万物皆对象，基本上每个变量都包含了变量自己和变量所指向的内存空间两个部分的逻辑含义。

来看这个例子：

Java:
```java
public int[] copy(int[] nums) {
    int[] arr = new int[nums.length];
    for (int i = 0; i < nums.length; i++) {
        arr[i] = nums[i]
    }
    return arr;
}

public void main() {
    int[] nums = new int[10];
    nums[0] = 1;
    int[] new_nums = copy(nums);
}
```
Python:
```python
def copy(nums):
    arr = [0]*len(nums)  # 相当于Java中的new int[nums.length]
		for i in range(len(nums)):
        arr[i] = nums[i]
    return arr
		
# 用list comprehension实现同样功能
def copy(nums):
    arr = [x for x in nums]
    return arr
		
# 以下相当于Java中的main函数
if __name__ == "__main__":
    nums = [0]*10
    nums[0] = 1
    new_nums = copy(nums)
```
C++:
```C++
int* copy(int nums[], int length) {
    int *arr = new int[length];
    for (int i = 0; i < length; i++) {
        arr[i] = nums[i];
    }
    return arr;
}

int main() {
    int *nums = new int[10];
    nums[0] = 1;
    int *new_nums = copy(nums, 10);
	return 0;
}
```

在 copy 这个函数中，arr 是一个局部变量，他在 copy 函数执行结束之后就会被销毁。但是里面 new 出来的新数组并不会被销毁。

这样，在 main 函数里，new_nums 里才会有被复制后的数组。所以可以发现一个特点：

- ***栈空间里存储的内容，会在函数执行结束的时候被撤回***

简而言之可以这么区别栈空间和堆空间：

- ***new 出来的就放在堆空间，其他都是栈空间***

# Part 4 什么是递归深度

接下来我们就可以来看一下递归深度与栈溢出的关系了

## 什么是递归深度

递归深度就是递归函数在内存中，同时存在的最大次数。

例如下面这段求阶乘的代码：

Java:
```java
int factorial(int n) {
    if (n == 1) {
        return 1;
    }
    return factorial(n - 1) * n;
}
```
Python:
```python
def factorial(n):
    if n == 1:
        return 1
    return factorial(n-1) * n
```
C++:
```C++
int factorial(int n) {
    if (n == 1) {
        return 1;
    }
    return factorial(n - 1) * n;
}
```


当n=100时，递归深度就是100。一般来说，我们更关心递归深度的数量级，在该阶乘函数中递归深度是O(n)，而在二分查找中，递归深度是O(log(n))。在后面的教程中，我们还会学到基于递归的快速排序、归并排序、以及平衡二叉树的遍历，这些的递归深度都是(O(log(n))。注意，此处说的是递归深度，而并非时间复杂度。

## 太深的递归会内存溢出

首先，函数本身也是在内存中占空间的，主要用于存储传递的参数，以及调用代码的返回地址。

函数的调用，会在内存的栈空间中开辟新空间，来存放子函数。递归函数更是会不断占用栈空间，例如该阶乘函数，展开到最后n=1时，内存中会存在factorial(100), factorial(99), factorial(98) ... factorial(1)这些函数，它们从栈底向栈顶方向不断扩展。

当递归过深时，栈空间会被耗尽，这时就无法开辟新的函数，会报出stack overflow这样的错误。

所以，在考虑空间复杂度时，递归函数的深度也是要考虑进去的。

### Follow up：

尾递归：若递归函数中，递归调用是整个函数体中最后的语句，且它的返回值不属于表达式的一部分时，这个递归调用就是尾递归。（上例factorial函数满足前者，但不满足后者，故不是尾递归函数）

尾递归函数的特点是：在递归展开后该函数不再做任何操作，这意味着该函数可以不等子函数执行完，自己直接销毁，这样就不再占用内存。一个递归深度O(n)的尾递归函数，可以做到只占用O(1)空间。这极大的优化了栈空间的利用。

但要注意，这种内存优化是由编译器决定是否要采取的，不过大多数现代的编译器会利用这种特点自动生成优化的代码。在实际工作当中，尽量写尾递归函数，是很好的习惯。

而在算法题当中，计算空间复杂度时，建议还是老老实实地算空间复杂度了，尾递归这种优化提一下也是可以，但别太在意。

这一章节，我们了解了什么是递归，且知道了只会用递归来实现二分可能会有一些不太好的地方。在下一章我们会来讲解如何直接在数组中进行二分，不见不散嗷。