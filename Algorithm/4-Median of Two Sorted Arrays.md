# Median of Two Sorted Arrays
## 描述
- 问题描述：对两个有序数组输出中位数。
- 函数类型：([],[])=>int
## 细节介绍
注意：
1. 中位数：求出index= Math.floor((length1+length2)/2),总数奇数个返回第(index+1)小的数,偶数个则返回(index)和(index+1)小的数的平均数。
## 思路
1. 题目就变成，假设有数组nums1(length = x),nums2(length = y)。因为nums1,nums2是有序的。需要找出第k小的数。
2. 解法有很多种，可以采用插入排序n，优先队列nlogn等，本次我们采用时间复杂度更低的分治法log(k)，在x较小的情况下，时间复杂度趋向插入排序。n = min(x,y),k = Math.floor((x+y)/2)。
3. 判断nums1的第m(m=Math.min(length1,Math.floor(k/2)))小的数与nums2的第k-m小的数的大小。
    3.1 如果nums1[m] === nums2[k-m]。nums1[m] == nums2[k-m] > nums1[x](x<m) && nums1[m] == nums2[k-m] > nums2[x](x<k-m)，所以说明nums[m] | nums[k-m]就是要找的第k小的数。
    3.2 如果nums1[m] > nums2[k-m]。nums1[m] > nums2[k-m] && nums1[m]  > nums1[x](x<m) && nums1[m] > nums2[x](x<k-m),所以说nums[m]最小就是第k小的数，而num2[k-m]必定比第k小的数要小。只要搜索nums2[k-m]的右边和nums1[m]的左边（包含其自身）
    3.3 如果nums1[m] < nums2[k-m]。与3.2同理可得第k小的数在nums2[k-m]的左边（包含其自身）和nums1[m]的右边。   

## 实现
```javascript
var findMedianSortedArrays = function(nums1, nums2) {
   let length1 = nums1.length;
    let length2 = nums2.length;
    let mid =Math.floor((length1+length2)/2);
    let midValue;
    if((length1+length2)%2 === 1){
        midValue =  findKthValueInTwoSortArrays(nums1,nums2,mid+1);
    } else {
        midValue = (findKthValueInTwoSortArrays(nums1,nums2,mid)+
                   findKthValueInTwoSortArrays(nums1,nums2,mid+1))/2
    }
    return midValue;
};

var findKthValueInTwoSortArrays = function(nums1,nums2,k){
    let length1 = nums1.length;
    let length2 = nums2.length;
    if(length2< length1){//for next step;
        return findKthValueInTwoSortArrays(nums2,nums1,k);
    }
    
    if(length1 === 0){//the num in nums2
        return nums2[k-1];
    }
    
    if(k === 1){ //bcz length2>=length1 && length1>0 => length2>0
        return Math.min(nums1[0],nums2[0]);
    }
    
    let mid1 = Math.min(length1,Math.floor(k/2))-1;
    let mid2 = k-2-mid1;//bcz k !== 0 && k !==1 => k >=2;
    if(nums1[mid1] === nums2[mid2]){
        return nums1[mid1];
    } 
    
    if(nums1[mid1]>nums2[mid2]){ // nums in mid1'left(includes mid1 self) or mid2'right
        return findKthValueInTwoSortArrays(nums1.slice(0,mid1+1),nums2.slice(mid2+1,length2),k-mid2-1)
    }     
    return findKthValueInTwoSortArrays(nums1.slice(mid1+1,length1),nums2.slice(0,mid2+1),k-mid1-1);//nums in mid2'left(includes mid2 self) or mid1'right
}
```

