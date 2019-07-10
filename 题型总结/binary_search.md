# 二分查找  
二分查找的本质是每次通过分支判断丢弃掉一半的elements。所以需要思考如何去判断所要找的元素不在另一半的范围之内。  
需要注意终止条件，避免死循环。  
- 终止条件看看等于的时候区间还能不能用
- 本质在于排除区间，排除的时候一定要确保被排除的区间中所有元素都不符合要求  
- 一般每次排除一半，排除好排除的那一半  
- 对于mountain(先增加后减小的题目)，可以通过判断本element与两边elements的大小判断当前所属区间  
  
## 二分答案  
二分答案，就是用二分的方法，在可能的答案区间里找出问题的答案  
大多数情况下用于求解满足某种条件下的最大（小）值，前提是答案具有单调性，同时也可以理解为是一种倒推方法（先找答案在判断答案是否可行、有没有更优解）  

## QuickSort  
partition模板  
```
public int partition(int[] nums, int start, int end) {
        int key = nums[start];
        while(start < end) {
            while(start < end && nums[end] >= key) end--;
            nums[start] = nums[end];
            while(start < end && nums[start] < key) start++;
            nums[end] = nums[start];
        }
        nums[start] = key;
        return start;
}
```
  
## Arrays.binarySearch  
⑴.binarySearch(object[ ], object key);

如果key在数组中，则返回搜索值的索引；否则返回-1或者”-“(插入点 = index + 1)。插入点是索引键将要插入数组的那一点，即第一个大于该键的元素索引。  
如果要搜索的元素key在指定的范围内，则返回搜索键的索引；否则返回-1或者”-“(插入点)。
