# Find First and Last Position of Element in Sorted Array
## 描述
- 问题描述：给定一个有序数组和一个值，返回值在数组中的索引区间。
- 函数类型：(nums:int[],target:int) => [int low,int high]
## 细节介绍
1. 有序数组和一个值，查找索引或第一个XX的数，即采用二叉搜索树。
2. 主要判断有两点。</br>
    2.1 判断是否当前索引是不是上下区间。
        上区间（high）：索引值等于target。索引+1不等于target或者索引为最后索引。
        下区间（low）: 索引值等于target。索引-1不等有target或者索引为0。
    2.2 当已有上区间，则查找 low与mid（当前索引）区间。当已有下区间，则查找mid（当前索引）与high区间。
      
## 实现
```javascript
var searchRange = function(nums, target) {    
    let result = [];
    binarySearch(nums,target,0,nums.length-1,result);
    if(result.length === 0)result = [-1,-1];
    return result;
};
    

var binarySearch = function(nums,target,low,high,result){
    if(low > high) return -1;
    
    let mid = low + ((high-low)>>1);
    
     if(nums[mid] === target){
        if(mid === 0 || nums[mid - 1] !== target){
            result[0] = mid;            
        } 
        if(mid === nums.length-1 || nums[mid + 1] !== target){
            result[1] = mid;
        } 
         
         if(result[1] === undefined){
            binarySearch(nums,target,mid+1,high,result);
        }
        if(result[0] === undefined){
            binarySearch(nums,target,low,mid-1,result);
        }
            
     } else if(nums[mid] < target){       
       binarySearch(nums,target,mid+1,high,result);
     } else{
       binarySearch(nums,target,low,mid-1,result);
     }
}
```

