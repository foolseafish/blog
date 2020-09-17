# Generate Parentheses
## 描述
给定正整数n，输出n个‘（’和n个‘）’组成的所有括号组合。
## 细节介绍
1.组合后的字符长度为 2*n，即有n个（ 和n个右
2.如果(的个数< n, 则可以继续添加(
3.如果(的个数>)的个数, 则可以继续添加)

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

