# 前缀和  
给定一个数组A[1..n]，前缀和数组PrefixSum[1..n]定义为：PrefixSum[i] = A[0]+A[1]+...+A[i-1]；  
例如：A[5,6,7,8] --> PrefixSum[0,5,11,18,26]  
一个重要的作用就是求区间的和：  
A[a,b] = PrefixSum[b+1] - PrefixSum[a]  
例题：Maximum subarray  