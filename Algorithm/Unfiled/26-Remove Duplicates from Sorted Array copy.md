# Remove Duplicates from Sorted Array
## 描述
## 细节介绍 

## 实现
```javascript
var removeDuplicates = function(nums) {
    let now = 0,next = now;
    while(++next<nums.length){
        if(nums[now] !== nums[next]){
            nums[++now] = nums[next];
        }
    }
    return now+1;
};
```

