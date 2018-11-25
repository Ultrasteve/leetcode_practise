# Stack  
stack的作用主要在于回溯，根据这一性质，又派生出几种功能不同的stack  
### 单调栈  
单调栈是指从栈底到栈顶递增/递减的栈，利用单调栈，可以找到从左/右遍历第一个比它小/大的元素的位置。  
[网上的解释](https://blog.csdn.net/wubaizhe/article/details/70136174)  
单调栈的一些性质(单调递增栈为例)：  
- 每次从栈中 pop 出一个数a的时候，就找到了往左数比a小的第一个数（当前栈顶）和往右数比a小的第一个数（即将入栈的数）  
- 通过每次把>=入栈数的栈顶元素c pop出，剩下的那个就是左边第一个小于c的数  
- 稳定之后的stack中，每个element所在栈中的位置就是其相对于栈顶的正确位置（排列后）  
例题：[122. Largest Rectangle in Histogram](https://www.lintcode.com/problem/largest-rectangle-in-histogram/description)    
# Queue  
FIFO，保证元素一定会按照进队的顺序出队，重要的作用是层序遍历，bfs  
### 单调队列  
其实实现起来需要使用到[Deque](https://www.cnblogs.com/bushi/p/6681543.html)，有时候需要进行去除尾部的操作来维持队列的单调性  
相比于单调队列，多了一个去头的操作  
例题：[Sliding Window Maximum](https://www.lintcode.com/zh-cn/problem/sliding-window-maximum/)  
