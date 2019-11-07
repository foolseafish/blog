# Kth Largest Element in an Array
## 描述
- 问题描述：输出数组中第k大的数
- 函数类型：(nums:int[], k:int)=>int
## 细节介绍
由于只要输出第K大的数，排序没有顺序限制，适合使用快排，只需找到K下标就可输出，时间复杂度为On。
## 思路
1. 基础的快排实现
2. 增加判断当中间量为K-1时，return结束快排。

## 实现
```javascript
const findKthLargest = (nums, k) => {
    quickSort(nums,0,nums.length-1,k);
    return nums[k-1];
};
    
const quickSort = (arr,start,end,k) =>{   
    if(start>=end)return;
    let i = sort(arr,start,end);
    if(i === k-1)return;//增加快排判断
    quickSort(arr,start,i-1);
    quickSort(arr,i+1,end);
}

const sort = (arr,start,end) =>{
    let mid = arr[end];
    let i,j;
    for(i = start,j = start;j<end;j++){
        if(arr[j]>mid)
            swap(arr,i++,j);
    }    
    swap(arr,i,end);
    return i;
}

const swap = (arr,index1,index2) => {
    let temp = arr[index1];
    arr[index1] = arr[index2];
    arr[index2] = temp;
}
```

