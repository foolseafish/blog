# Find Peak Element
## 描述
- 问题描述：给定一个数组，找出数组中值大于其两侧的元素的index
- 函数类型：(nums:int[]) =>int
## 细节介绍
1. 数组，查找数，即采用二叉搜索树。
2. 主要判断有两点。</br>
    2.1 找出判断逻辑，什么数比两侧大。
        上升序列：最后一个
        下降序列：第一个
        总结：因为只需找任意一个，如果某个index为x存在nums[x]>nums[x+1],即可认为其位于下降序列，则搜索左边，否则搜索右边加本身（因为当前值可能为上升和下降转接点）。      
## 实现
```javascript
var findPeakElement = function(nums) {
    let left = 0 ,right = nums.length -1;
    while(left<right){
        let mid = left + Math.floor((right-left)/2);
        if(nums[mid]>nums[mid+1]){
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return left;
};
```

