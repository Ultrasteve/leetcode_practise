#[0 1 Matrix](https://leetcode.com/problems/01-matrix/)  
Intuition: if the point in the matrix is 0, then it ans is also 0. If it is 1, then the <font color=#00ff00>ans = min(up, right, left, bottom)</font> However, we can not simplily call the min func, since if the ans of the 4 neighbours is not stable, we will get a wrong ans of this point.  

To deal with this problem, intuitively, deal with the point that can have a stable ans in the first round(the point with value 0 && the point with value 1 but have a 0 neighbour), then we do bfs, find the answer of next level until we done.  

```java
public class Solution {
    public int[][] updateMatrix(int[][] matrix) {
        //Good habit
        int m = matrix.length;
        int n = matrix[0].length;
        
        Queue<int[]> queue = new LinkedList<>();
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 0) {
                    queue.offer(new int[] {i, j});
                }
                else {
                    /**
                    we got to mark those point that already have a stable ans, in case we change the correct ans in the future.
                    This is actualy what we always do in bfs, do not visite the visited point again!!!!!
                    we can use a visited[][]
                    we can also mark those point that has not been deal with, set them as Integer.MAX_VALUE
                    */
                    matrix[i][j] = Integer.MAX_VALUE;
                }
            }
        }
        
        int[][] dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
        
        while (!queue.isEmpty()) {
            int[] cell = queue.poll();
            for (int[] d : dirs) {
                int r = cell[0] + d[0];
                int c = cell[1] + d[1];
                if (r < 0 || r >= m || c < 0 || c >= n || 
                    matrix[r][c] <= matrix[cell[0]][cell[1]] + 1) continue;
                queue.add(new int[] {r, c});
                matrix[r][c] = matrix[cell[0]][cell[1]] + 1;
            }
        }
        
        return matrix;
    }
}
```

Other method:  
We can also do it in two pass, much clever way.
```java
public int[][] updateMatrix(int[][] matrix) {
        int row = matrix.length, col = matrix[0].length;
        /**
        First pass, we only let the point's up and left neighbours to affact its value.
        Unless, the value is stable in this pass.
        */
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                if (matrix[i][j] == 1) {
                    matrix[i][j] = Integer.MAX_VALUE;
                    if (i - 1 >= 0 && matrix[i - 1][j] != Integer.MAX_VALUE) 
                       matrix[i][j] = Math.min(matrix[i][j], 1 + matrix[i - 1][j]);
                    if (j - 1 >= 0 && matrix[i][j - 1] != Integer.MAX_VALUE) 
                      matrix[i][j] = Math.min(matrix[i][j], 1 + matrix[i][j - 1]);
                }
            }
        }
        /**
        Second pass, we only let the point's bottom and right neighbours to affact its value.
        */
        for (int i = row - 1; i >= 0; i--) {
            for (int j = col - 1; j >= 0; j--) {
                    if (i + 1 < row && matrix[i + 1][j] != Integer.MAX_VALUE) 
                      matrix[i][j] = Math.min(matrix[i][j], 1 + matrix[i + 1][j]);
                    if (j + 1 < col && matrix[i][j + 1] != Integer.MAX_VALUE) 
                      matrix[i][j] = Math.min(matrix[i][j], 1 + matrix[i][j + 1]);
            }
        }
        return matrix;
    }
```
