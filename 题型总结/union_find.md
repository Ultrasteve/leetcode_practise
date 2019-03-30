# 并查集  
Union find.  
find(Node a): 找到a节点的祖先  
union(Node a, Node b): 将a与b所代表的两个cluster连接起来  
可以用O(1)的时间检查两个元素是不是在同一个cluster里面（均摊复杂度的情况下） 
## 优化  
- 路径压缩：在find的时候一边查找，一边将node指向root，压缩了path的高度（变成2）  
- union by rank: 把components少的cluster merge到多的components里面  

### Framework  
```
    class UnionFind:
        func UnionFind(n):
            parents = [1...n] //一开始都指向自己
            ranks = [0] //一开始除自己以外都没有别的成员

        func find(x):
            if x != find(x) //表示不是根结点
                parents[x] = find(parent[x]) //路径压缩
            return parents[x]

        func union(x, y):
            parent_x, parent_y = find(x), find(y)
            if ranks[parent_x] < ranks[parent_y]: parent[parent_x] = parent_y
            if ranks[parent_x] > ranks[parent_y]: parent[parent_y] = parent_x
            if ranks[parent_x] == ranks[parent_y]:
                parent[parent_y] = parent_x
                ranks[parent_x]++
```