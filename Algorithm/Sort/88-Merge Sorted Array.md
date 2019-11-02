# Merge Sorted Array
## 描述
问题描述：对两个有序数组归并,改变入参数组nums1,是归并排序的并部分;
函数类型：(nums1:int[], m:int, nums2:int[], n:int) =>void
## 思路
1.判断异常情况
2.截取数组nums1的m个元素，nums2的n个元素
3.判断当前左侧是否已经排完，是则直接copy右侧，如右侧已经拍完copy左侧，其他则比较左右数组值，取小的替换原数组nums1的下标元素。
## 实现
```javascript
const merge = (nums1, m, nums2, n) => {
    if(nums1.length<m+n ||nums1.length<m || nums2.length<n)throw new Error('wrong!');
    let copyNums1 = nums1.slice(0,m);
    let copyNums2 = nums2.slice(0,n);
    let k = 0;
    let i = 0;
    let j = 0;
    
    while(k<m+n){
        if(i >= m){
            nums1[k++] = copyNums2[j++];
        } else if(j>=n){
            nums1[k++] = copyNums1[i++];
        } else{
            nums1[k++] = copyNums1[i]<=copyNums2[j]?copyNums1[i++]:copyNums2[j++];
        }
    }
};
```

