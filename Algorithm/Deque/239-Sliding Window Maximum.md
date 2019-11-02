# Valid Parentheses
## 描述
- 问题描述：比较当前下标元素和后k-1个元素，取最大值。组成新数组。
- 函数类型：(nums:int[],k:int)=>int[]<br>
假设入参nums = [1,3,-1,-3,5,3,6,7],k = 3,输出为[3,3,5,5,6,7]
- 双端队列：同时具备栈和队列的功能，如JS的Array;
## 思路
- 思路一：双循环实现
1. 遍历nums,至length-k
2. 遍历k,取最大值push入新数组
- 思路二：单循环双端队列实现
1. 新建双端队列deque,遍历nums
2. 循环判断当前元素是否大于栈顶元素，是则pop
3. 将新元素push
4. 判断栈顶元素是否已过窗口（栈顶元素的下标是否小于当前下标-k）,是则shift
5. 当前下标大于等于k-1时，组装返回数组。

##实现
  ```javascript
const maxSlidingWindow = function(nums, k) {
    let result = [];
    let deque = [];    
    nums.forEach((num,index) =>{
            while(deque.length>0 && deque[deque.length-1].num<num){
                deque.pop();
            }
             deque.push({
                    num,
                    index
                });
            if(deque[0].index <= index-k){
                deque.shift();
            }
        
        if(index-k >=-1){
            result[index-k+1] =deque[0].num;   
        }        
    })
    return result;
};
  ```

