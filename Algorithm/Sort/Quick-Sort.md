# 快速排序
## 描述
- 快速排序的原地排序，非稳定排序。
- 时间复杂度 O(nlogn)
## 介绍
类比在军队里，讲究的是效率。教官下面领着一队新兵。教官指出最左边的一个人出列，说以这个人为基准，比他矮的依次站左边（矮的排好剩下的就是高的了），排号之后再让这个人归队。然后分别在左右两队重复此操作。
## 思路
1. 教官指出最左边的一个人出列(基准下标 pivot= 0,temp = arr[pivot],让这个人不进循环)
2. 说以这个人为基准，比他矮的依次站左边(循环i对比pivot,if(arr[i] < temp) swap(arr,i,temp)，pivot++)
3. 排号之后再让这个人归队（把这个人交换到基准下标位置）
4. 然后分别在左右两队重复此操作(递归执行(arr,start,pivot-1)和(arr,pivot+1,end))
## 注意
写递归的时候记住顺序1.异常判断2.退出判断3.正常递归代码。
1步让基准不进循环的办法：把他放最右边，因为是要找比他矮的，所以更看重的是左边必须有序，那这个人必然不能放在左边，因为有可能被交换。而他放在最右边是不会被交换到的。
4步如果左右两边的长度小于2,就不用递归了。
## 实现
```javascript
//不是数组别搞我
const quickSort = (arr, start=0, end=arr.length-1)=>{
    if(start<0 || end>=arr.length)return;
    if(start>=end)return;
    let pivot = start;
    let temp = arr[pivot];
    swap(arr,start,end);
    for(let i = start; i < end; i++){
       if(arr[i]<temp){
            swap(arr,i,pivot);            
            pivot++;
       }       
    }
    swap(arr,pivot,end);
    if(pivot - 1>start){
        quickSort(arr,start,pivot - 1);
    }
    if(pivot + 1<end){
        quickSort(arr, pivot + 1, end);
    }
}

const swap = (arr,i,j)=>{
    const temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
```

