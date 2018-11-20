# Two Pointers  
two pointer类型的题目主要分为：对撞型（又分为 two sum类，partition类和灌水类），同向型（window类和快慢指针）。  
## 对撞型  
+ two sum类: 通过调整左右指针调整sum的大小  
+ partition类：  
```
    //在[l,r]之间进行partition
    public void partition(int[] num, int l, int r) {
        int left = l, right = r;
        int pivot = num[left];
        
        //partition
        while(left < right) {
            while(left < right && num[right] >= pivot) right--;
            
            num[left] = num[right];
            
            while(left < right && num[left] <= pivot) left++;

            num[right] = num[left];
        }

        //将pivot移动到相应的位置
        num[left] = pivot;
    }
```
+ 灌水类 or 普通对撞（常常用于寻找区间本质是通过移动指针缩小范围，直到找到合适的区间）:  
```
    //模板
    while(i < j) {
        if(A[i] A[j] 满足某条件)
            j--; //不再考虑[i...j-1, j]区间
            do something
        else if()
            i++; //不再考虑[i, i+1...j]区间
            do something
        else
            i++;
            j--;
    }
```

  
## 同向型  
+ window类型：  
```
    //先移动right指针，再移动left指针，目的是找到一段合适的区间
    for(int j = 0; j < nums.length; j++) {
        while(i < nums.length && 某条件) {
            i++;
        }
    }
```
例题：  
``` 
 minimum-size-subarray-sum
 Minimum Window Substring
 Longest Substring with At Most K Distinct Characters 
 Longest Substring Without Repeating Characters
```
+ 快慢指针：经常用于链表