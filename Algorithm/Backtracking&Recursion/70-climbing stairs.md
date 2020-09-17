# 70-climbing stairs
## 描述
- 只能爬一步或者两步,给定台阶数，求到达目的的方式数目。

## 思路
用数学归纳法
{
    0：1
    1：1
    f(n):f(n-1) + f(n-2)
}
是斐波那契数列。
## 实现
```javascript
var climbStairs = function(n) {
    const dp = [1,1];
    let i = 1;
    while(++i<=n){
        dp[i] = dp[i-1] + dp[i-2];
    }
    return dp[n];
};
```

