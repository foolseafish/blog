# Remove Element
## 描述
## 细节介绍 

## 实现
```javascript
var removeElement = function(nums, val) {
    let cur = 0,next = cur;
    while(next < nums.length){
        if(nums[next] !== val){
           nums[cur++] = nums[next];
        }     
        next++;
    }
    return cur;
};
```

