# 计数排序
## 描述
- 计数排序，非原地，可以稳定排序。
- 时间复杂度 O(M+N)
- 适合环境下，排序的时间复杂度低于O(nlogn)算法。
- 适合1.整数2.整数数组最大最小值跨度不大。
## 介绍
类比要给班级里面的前10名优等生的成绩排个序，正常都是看着卷子报分数比如95，然后记下来95一个。等报完之后就知道有几个95，几个96，几个98。然后排序就是直接[95,95,96,96,96,98,98];
## 思路
1. 正常都是看着卷子报分数，然后记下来(数组计数，以下标作为分数，以值作为频率)
2. 等报完之后就知道有几个95，几个96，几个98。然后排序(外循环数组，内循环数组值生成结果数组)
## 注意
1步生成的数组可以用hash数组，也可以用原值减最小值建立新下标，后面下标加上最小值作为最后的输出值。
上述思路实现的是非稳定排序，想要生成稳定排序，需要多建立一张排名表（就是95分排第几名，98分排第几名）
1.以上述思路第一步生成的计数表为基础，arr[i] = arr[i - 1] + arr[i],生成排名表;
2.在上述思路第二步时，循环原无序数组，按照排名表生成结果数组。
## 实现
```javascript
const countSort = (arr)=>{
 if(arr.length === 0)return 0;
 const countArr = [];
 for(let i=0,len=arr.length; i<len; i++){
    cons num = arr[i];
    countArr[num] =countArr[num] || 0;
    countArr[num]++;
 }
 const result = [];
 countArr.forEach((num,index) => {
    for(let i = 0;i<num;i++){
       result.push(index);
    }
 })
}
return result;
```

