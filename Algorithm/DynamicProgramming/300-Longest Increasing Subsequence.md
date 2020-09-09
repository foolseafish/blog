# Longest Increasing Subsequence
## 描述
- 问题描述：给定一个数组，找出最长上升序列长度
- 函数类型：(nums:int[]) =>int
## 细节介绍
1. 动态规划的题目中需要找出最优子结构。
2. 假定已知f(i,i<n),f(1),得出f(n)。(n>1);
    2.1 存在索引i<n,使得nums[i]<nums[n]且nums前i个以nums[i]结尾的最长上升序列,长度为y。
    2.2 获取2.1中的最大值,以nums[n]结尾的最长上升序列即为y+1。
    2.3 获取2.2中的最大值即为最后的值。
3.确定状态转移方程f(n,n>1)= max(1<=i<n,nums[i]<nums[n]){f(i)} + 1
## 实现
```javascript
var lengthOfLIS = function(nums) {
    if(nums.length<2)return nums.length;
    let max = 1,len = nums.length;
    let dp = [];
    for(let i = 0;i<len;i++){
        dp[i] = 1;
        for(let j = 0 ;j<i;j++){
            if(nums[i]>nums[j] && dp[i]<dp[j] + 1){
                dp[i] = dp[j] + 1 
            }
        }        
        max = Math.max(dp[i],max);
    }
        return max;
};
  ```

