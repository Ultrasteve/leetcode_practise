# 线段树  
它实际上是一颗二叉树，树种的每一个节点表示一个区间[a, b]，左儿子的区间是[a, (a+b)/2]，右儿子的区间是[(a+b)/2+1, b]。  
- 查询、更新操作O(logn)  
- 需要额外的空间O(n)