# Find Minimum in Rotated Sorted Array II
## 描述
- 问题描述：给定一个旋转数组，确定值数组内最小值，数组元素可重复
- 函数类型：(nums:int[]) =>int
## 细节介绍
1. 有序(旋转)数组，查找最小的数，即采用二叉搜索树。
2. 主要判断有两点。</br>
    2.1 数组元素不重复，判断是否左右两边哪边有序。
        左边有序：在中间值不为target的情况下，只要保证mid>low即可保证左边有序。最小值为left索引所在位置
        右边有序: 上述不成立则说明右边有序。最小值为min索引所在位置。        
    2.2 已知左右有序分界。走正常二叉树搜索判断即可。      
## 实现
```javascript
var findMin = function(nums) {
    let left = 0,right = nums.length-1;
    let minIndex = 0;
    let min = nums[minIndex];
    while(left<=right){
        let mid = left + Math.floor((right - left)/2);
        if(nums[left]<=nums[mid]){
            minIndex = left;
            left = mid +1;
        } else {
            minIndex = mid;
            right = mid - 1;
        }
        min = nums[minIndex]<min?nums[minIndex]:min;
    }
    return min
};
```

