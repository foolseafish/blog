# 插入排序
## 描述
- 插入排序的原地排序，稳定排序。
- 时间复杂度最差 O(n2)
## 介绍
类比体育课排个子，从第二个开始（第一个默认有序），把这个人挑出来，拿这个人跟前面一个一个比，如果比前面的高就挑下一个，如果比前面的矮，把前面的这个人放后面，然后再往前继续同样的操作，直到前面的人比这个人矮就把他放这里。
## 思路
1. 从第二个开始(循环从i = 1开始)
2. 把这个人挑出来(存下变量temp=arr[i])
3. 拿这个人跟前面的比,如果比前面的高就挑下一个（外循环continue）
4. 如果比前面的矮，把前面的这个人放后面,然后再往前继续同样的操作。(内循环j递减,把数组下标j赋值为j-1)
5. 直到前面的人比这个人矮就把他放这里(arr[j] = temp)

## 实现
```javascript
const insertSort = (arr)=>{
    const len = arr.length;
    for(let i = 1; i<len; i++){
        const temp = arr[i];
        if(temp > arr[i-1]) continue;
        for(let j= i; j>=0; j--){
            if (temp<arr[j - 1]) {
                arr[j] = arr[j-1]
            } else {
                arr[j] = temp;
                break;
            }
        }
    }
}
```

