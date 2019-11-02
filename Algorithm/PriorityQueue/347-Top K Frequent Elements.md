# Top K Frequent Elements
## 描述
- 问题描述：获取数组中出现最频繁的前k个元素。
- 函数类型：(nums:int[],k:int)=>int[]
- 假设入参nums = [1,1,1,2,2,3],k = 2,输出为[1,2]
## 细节介绍
- 优先队列：根据优先级排序的二叉树组;
- 向上筛选：从末尾元素循环上溯比较其与父级元素优先级，若大于则交换位置。当有新元素添加到队列种需要先上溯。
- 向下筛选：从头部元素循环下溯比较其与左右元素优先级，找出优先级最大的子元素交换位置。当有队头元素被删除时需要将队尾元素添加至对头，并作下溯;
- 下标规律：当前元素i,父级下标(i-1)>>1,左孩子下标2*i+1,右2*i+2;
## 思路
1. 看到根据出现次数，先建立hashmap循环数组记录次数;
2. 根据hashmap建立优先队列queue，push元素后对queue做向上筛选。
3. 循环K弹出queue头部元素，弹出后对queue做向下筛选。
4. 返回循环K的queue头部数组。
## 实现
  ```javascript
const topKFrequent = (nums, k) => {
    const hashMap = {};
    const priorityQueue = new PriorityQueue(function(a,b){
        return hashMap[a]>hashMap[b];
    });
    nums.forEach(num=>{
        if(!hashMap[num])hashMap[num] = 0;
        hashMap[num]++;
    });
    for(const key in hashMap){        
        priorityQueue.add(key); 
    }
    return priorityQueue.shift(k); 
};

const _privateQueue = Symbol('_privateQueue');
const _privatePriorityFunction = Symbol('_privatePriorityFunction');
const _privateSwitch = Symbol('_privateSwitch');
const _privateSiftDown = Symbol('_privateSiftDown');
const _privateSiftUp = Symbol('_privateSiftUp');

class PriorityQueue{

    constructor(priorityFunction){
        this[_privateQueue] = [];    
        this[_privatePriorityFunction] = priorityFunction;
    }

    [_privateSiftUp] = ()=>{
        const privateQueue = this[_privateQueue];
        let nowIndex = privateQueue.length-1;
        let rootIndex = 0;
        while(nowIndex != 0 
             &&(rootIndex= (nowIndex-1)>>1,this[_privatePriorityFunction](privateQueue[nowIndex],privateQueue[rootIndex]))){            
            this[_privateSwitch](privateQueue,nowIndex,rootIndex);
            nowIndex = rootIndex;
        }          
    }   

    [_privateSwitch] = (array,index1,index2) =>{
        let temp = array[index1];
        array[index1] = array[index2];
        array[index2] = temp;
    }

    add = (val)=>{
        this[_privateQueue].push(val);
        this[_privateSiftUp]();
    }

    [_privateSiftDown] = ()=>{        
        const privateQueue = this[_privateQueue];
        privateQueue.unshift(privateQueue.pop());
        let length = privateQueue.length;
        let nowIndex = 0;
        let left,right;
        while(right=(2*nowIndex +2),left=right-1,left<length){                      
            var higherPriorityChildren = right<length?this[_privatePriorityFunction](privateQueue[left],privateQueue[right])?left:right:left;                
            if(!this[_privatePriorityFunction](privateQueue[higherPriorityChildren],privateQueue[nowIndex]))return;
            this[_privateSwitch](privateQueue,nowIndex,higherPriorityChildren);
            nowIndex = higherPriorityChildren;            
        }       
    }   
    
    shift = (shiftLength=1)=>{
        let array = [];
        while(shiftLength--){
            array.push(this[_privateQueue].shift());
            this[_privateSiftDown]();
        }        
        return array;
    }
}
  ```

