- Part 1 用DFS来解决在隐式图上的组合问题, 17.subset两个解法 DFS
- Part 2 18.subset ii 两个解法 DFS+Hash


今天我们一起来学习『组合类DFS』

在非二叉树上的深度优先搜索（Depth-first Search）中，90%的问题，不是求组合（Combination）就是求排列（Permutation）。特别是组合类的深度优先搜索的问题特别的多。而排列组合类的搜索问题，本质上是一个“隐式图”的搜索问题。

本章关键字：DFS（Depth First Search，深度优先搜索），Combination（组合），Subset（子集）。

# 用DFS来解决在隐式图上的组合问题

在本章的学习中，我们将使用DFS来解决在隐式图上的组合问题。

一个问题如果没有明确的告诉你什么是点，什么是边，但是又需要你进行搜索的话，那就是一个隐式图搜索问题了。所以对于这类问题，我们首先要分析清楚什么是点什么是边。

关于分析的过程，我们下面的视频中进行讲解。

- 第十六章【互动】组合类DFS - 1 - subset solution 1.mov
[17. subset](../lintcode/17.subset.md)

- 第十六章【互动】组合类DFS - 2 - subset solution 2.mov

# subset ii

在攻克了上面的问题之后，请同学思考下这个问题：如果所给的集合是[1,2,2,3]，并且我输出的子集中还不允许出现两个[1,2,3]，这时我们该怎么改动搜索过程呢？

这个问题是一个经典的全子集问题的follow up，稍加思考过后，来看看老师对这种带有重复元素的集合是怎么处理的吧。


- 第十六章【互动】组合类DFS - 3 - subset ii.mov
[18. subset ii](../lintcode/18.subset_ii.md)

# subset ii - use hash

对于“选代表”的方法来说，我们采取的办法是从若干个数字相同但顺序不同的小集合中拿出一个有序的集合作为代表，将剩下的无序集合舍弃。

那有没有一种数据结构，可以完成去重工作呢？

答案自然是hash，所以我们可以对所有的集合进行哈希，每次将当前搜索到的集合subset放入结果集合subsets中的时候，只需将这个集合看做是key，如果对应的value不存在，就证明这个集合是个没出现过的新集合，这时再把新的集合放入subsets中即可。

在这段代码中，我们选择将subset从集合变成字符串，从而实现对集合的哈希。
```java
public class Solution {
    /**
     * @param nums: A set of numbers.
     * @return: A list of lists. All valid subsets.
     */
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> subsets = new ArrayList<>();
        HashMap<String, Boolean> visited = new HashMap<String, Boolean>();
        Arrays.sort(nums);
        dfs(nums, 0, new ArrayList<>(), subsets, visited);
        
        return subsets;
    }
    
    String getHash(List<Integer> subset) {
        String hashString = "";
        for (int i = 0;i < subset.size(); i++) {
            hashString += subset.get(i).toString();
            hashString += "_";
        }
        
        return hashString;
    }
    
    void dfs(int[] nums, 
             int startIndex, 
             List<Integer> subset,
             List<List<Integer>> subsets,
             HashMap<String, Boolean> visited) {
        String hashString = getHash(subset);
        
        if (visited.containsKey(hashString)) {
            return ;
        }
        
        visited.put(hashString, true);
        subsets.add(new ArrayList<Integer>(subset));
        for (int i = startIndex;i < nums.length; i++) {
            subset.add(nums[i]);
            dfs(nums, i + 1, subset, subsets, visited);
            subset.remove(subset.size() - 1);
        }
        
    }
    
}
```

使用Python的小伙伴可以在下面的九章题解链接中查看Python的相关代码。

对于此题其他的做法（如BFS、非递归方法）也能在下面的链接中查看。
https://www.jiuzhang.com/solution/subsets-ii/

这一章的内容就到这里，在下一章中我们将使用DFS迎战排列（Permutation）问题，还将接触一类著名的NP问题——旅行商问题，还请同学认真学习哦~~