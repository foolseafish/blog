# 14. Longest Common Prefix
## 描述
## 细节介绍 

## 实现
```javascript
var longestCommonPrefix = strs=>    
    strs.length === 0 ?
    '':
    strs.reduce((commonPrefix,next)=>{
        let i = 0,len1=commonPrefix.length,len2 = next.length
        for(;i<len1&&i<len2;i++){
            if(commonPrefix[i] !== next[i])break;
        }
        return commonPrefix.substr(0,i);
    });
```

