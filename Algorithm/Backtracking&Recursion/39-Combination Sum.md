# Combination Sum
## 描述
- 问题描述：给定一个数组和一个值，列出所有元素相加等于这个值的数组子集。
- 函数类型：(candidates:int[],target:int) => int[]
## 细节介绍
1. 遇到需要列出所有枚举的情况，大概率是使用递归的回溯。
## 实现
```javascript
var combinationSum = function(candidates, target) {
    let result = [];
    backTracking(candidates,target,0,result,[]);
    return result;    
};

var backTracking = (candidates,target,start,result,solution)=>{
    //判断异常情况
    if(target<0)return;
    //正常返回情况
    if(target === 0){
        result.push([...solution]);
        return;
    }
    //回溯体
    for(let i = start,len = candidates.length;i<len;i++){
        //先尝试将放入集种,方便后面直接使用solution获取
        solution.push(candidates[i]);
        //因为元素可以重复使用，所以从i开始。
        backTracking(candidates,target-candidates[i],i,result,solution);
        //使用完后弹出栈，成功的已经记录了，不成功的没必要继续。
        solution.pop();
    }    
    
}
```

