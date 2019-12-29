# Search in Rotated Sorted Array II
## 描述
- 问题描述：给定一个旋转数组和一个值，确定值是否在数组内。*数组内的元素可以重复
- 函数类型：(nums:int[],target:int) =>bool
## 细节介绍
1. 有序(旋转)数组和一个值，查找索引或第一个XX的数，即采用二叉搜索树。
2. 主要判断有两点。</br>
    2.1 判断是否左右两边哪边有序。
        未知情况：由于数组元素可以重复，如果low与mid值相同，则不能判断哪边有序(例如[1,1,1,3,1,1]和[1,3,1,1,1])。可以将low++。
        左边有序：在中间值不为target的情况下，只要保证mid>low即可保证左边有序。
        右边有序: 在中间值不为target的情况下，由于数组元素可以重复，右边有序可能是右边元素全一致。所以不能判断high>mid。只需判断low>mid证明左边无需即可说明右边有序。        
    2.2 已知左右有序分界。走正常二叉树搜索判断即可。      
## 实现
```javascript
var search = function(nums, target) {
    if(nums.length === 0)return false;
    let low = 0,high = nums.length-1;
    while(low<=high){
        let mid = low + Math.floor((high-low)/2);
        if(nums[mid] === target)return true;
        if(nums[low]<nums[mid]){
            if(nums[low]<=target && target <nums[mid]){
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        } else if(nums[low] > nums[mid]){
            if(nums[mid]<target && target <=nums[high]){
                low = mid +1;
            } else {
                high = mid -1;
            }
        } else {
            low++;
        }
    }
    return false;
};
```

