# Two Sum II - Input array is sorted
## 描述
## 细节介绍
## 思路

## 实现
```javascript
var twoSum = function(numbers, target) {
    let i = 0;
    while(i<numbers.length){
        let nowNumber = numbers[i];
        let searchNumber = binarySearch(numbers.slice(i + 1),target-nowNumber);
        if(searchNumber !== undefined)return [i + 1,searchNumber + i + 2];
        while(numbers[i] === numbers[++i]);
    }
};

var binarySearch = function(numbers,target){
     let start = 0,end = numbers.length -1;
    while(start<=end){
        let mid = start + ((end-start)>>1);
        if(numbers[mid] === target)return mid;
        if(numbers[mid]<target){
            start = mid + 1;            
        } else {
            end = mid - 1;
        }        
    }
}
```

