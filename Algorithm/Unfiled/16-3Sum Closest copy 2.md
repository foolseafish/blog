# 3Sum Closest
## 描述
## 细节介绍 

## 实现
```javascript
var threeSumClosest = function(nums, target) {
    nums = nums.sort((a,b)=>a-b);
    let closest = null;
    for(let start = 0;start<nums.length-2;){
        let mid = start + 1;
        let end = nums.length-1;
        while(mid<end){
            let sum = nums[start] + nums[mid] + nums[end];
            let nowDis = Math.abs(sum-target);
            if(closest !== null){
                let closestDis = Math.abs(closest-target);
                closest = closestDis> nowDis ? sum :closest;                
            } else{
                closest = sum;
            }
            
            if(sum === target){
                return sum;
            } else if(sum <target){
                mid++;
            } else {
                end--;                
            }
            
        }
        while(start<nums.length-2 && nums[start] === nums[++start]);
    } 
    return closest;
};
```

