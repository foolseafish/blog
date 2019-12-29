# Find Minimum in Rotated Sorted Array
## 描述
- 问题描述：给定一个旋转数组，确定值数组内最小值，数组元素不重复
- 函数类型：(nums:int[]) =>int
## 细节介绍
1. 有序(旋转)数组，查找最小的数，即采用二叉搜索树。
2. 主要判断有两点。</br>
    2.1 数组元素不重复，判断是否左右两边哪边有序。
        未知情况：由于数组元素可以重复，如果low与mid值相同，则不能判断哪边有序(例如[1,1,1,3,1,1]和[1,3,1,1,1])。可以将left++,最小索引值为left。
        左边有序：在中间值不为target的情况下，只要保证mid>left即可保证左边有序。最小索引值为left
        右边有序: 在中间值不为target的情况下，由于数组元素可以重复，右边有序可能是右边元素全一致。所以不能判断right>mid。只需判断left>mid证明左边无需即可说明右边有序。最小索引值为mid;
    2.2 已知左右有序分界。走正常二叉树搜索判断即可。      
## 实现
```javascript
var findMin = function(nums) {
    let left = 0,right = nums.length-1;
    let minIndex = 0;
    let min = nums[minIndex];
    while(left<=right){
        let mid = left + Math.floor((right-left)/2);        
        if(nums[left]  < nums[mid]){
            minIndex = left;
            left = mid ;
        } else if(nums[left]>nums[mid]){
            minIndex = mid;
            right = mid;
        } else {
            minIndex = left;
            left++;
        }
        min = min>nums[minIndex]?nums[minIndex]:min;
    }
    return min;
};
```

