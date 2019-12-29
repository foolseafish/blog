# Search in Rotated Sorted Array
## 描述
- 问题描述：给定一个有序旋转数组和一个值，返回值在数组中的索引。
- 函数类型：(nums:int[],target:int) => int
## 细节介绍
1. 有序数组(包含有序旋转)和一个值，查找索引或第一个XX的数，即采用二叉搜索树。
2. 主要判断有一点。</br>
    2.1 判断是否当前左侧是否有序。判断依据为nums[mid]>=nums[low],若成立说明左侧时有序的（因为数组时旋转的所以左右两边必有一边是有序的），否则右侧有序。
      
## 实现
```javascript
var search = function(nums, target) {
    var low = 0,high = nums.length -1;
    
    while(low <= high){
        let mid = low + ((high - low ) >>1);
        if(nums[mid] === target)return mid;
        if(nums[mid] >= nums[low]){
            if(nums[low] <= target && target < nums[mid]){
                high = mid - 1;                
            } else {
                low = mid + 1;
            }            
        } else {
            if(nums[mid]<target && target <= nums[high]){
                low = mid + 1 
            } else {
                high = mid - 1;     
            }            
        }
    }
    return  -1;
};

```

