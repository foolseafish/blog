# Daily Temperatures
## 描述
- 问题描述：给定一个包含一组温度数组，返回每个温度升高所需的天数数组。
- 函数类型：（T:numbers[]）=>numbers[]<br>
假设入参T=[73, 74, 75, 71, 69, 72, 76, 73]，输出[[1, 1, 4, 2, 1, 1, 0, 0]。
## 思路
1. 新建栈stack,遍历nums
2. 循环判断当前元素是否大于栈顶元素，是则pop,将返回数组的对应下表赋值为栈顶元素下标与当前下表的差值,
3. 将新元素和元素下标push
4. 如果栈内还有元素则，对应下标补0。
  ## 实现
  ```javascript
const dailyTemperatures = function(T) {
    let stack = [];
    let returnArr = [];
    T.forEach((temperature,index)=>{
        let data = {
            index,temperature
        }
        while(stack.length>0 && temperature>stack[stack.length-1].temperature){            
            let tempData = stack.pop();       
            returnArr[tempData.index] = index-tempData.index;
        }        
        stack.push(data);  
    })
    while(stack.length>0){
        let tempData=stack.pop();        
        returnArr[tempData.index] = 0;
    }
    return returnArr;
};
  ```

