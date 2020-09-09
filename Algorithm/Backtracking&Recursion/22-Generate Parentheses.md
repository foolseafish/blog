# Generate Parentheses
## 描述
## 细节介绍
## 实现
```javascript
var generateParenthesis = function(n) {
    let res = [];
    var backTracking = (open, close, str)=>{
        if(str.length === n * 2){
            res.push(str);
        }
        
        if(open<n){
            backTracking(open+1,close,str +'(')
        }
        
        if(open>close){
            backTracking(open,close+1,str +')')
        }
    }
    backTracking(0,0,'');
    return res;
};
```

