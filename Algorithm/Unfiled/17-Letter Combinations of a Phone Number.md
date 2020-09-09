# Letter Combinations of a Phone Number
## 描述
## 细节介绍 

## 实现
```javascript
const MAP = {
    2:['a','b','c'],
    3:['d','e','f'],
    4:['g','h','i'],
    5:['j','k','l'],
    6:['m','n','o'],
    7:['p','q','r','s'],
    8:['t','u','v'],
    9:['w','x','y','z'],
}
var letterCombinations = function(digits) {
    if(digits.length === 0) return [];
    let pick = []
    for(let i = 0,len = digits.length;i<len;i++){
        let digit = digits[i];
        if(digit === 1)return[];
        if(pick.length === 0){
            pick = MAP[digit];
            continue;
        }
        let nowPick = [];
        for(let x = 0 ;x < pick.length;x++){
            for(let y = 0;y<MAP[digit].length;y++){
                nowPick.push(pick[x]+MAP[digit][y]);                
            }
        }
        pick = nowPick;
    }
    return pick
};
```

