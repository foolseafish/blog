# Divide Two Integers
## 描述
- 问题描述：实现除法，不能使用 * ，/ ，%,溢出时返回2**31-1。
- 函数类型：(dividend:int,divisor:int) => int
## 细节介绍

## 实现
```javascript
const divide = function(dividend, divisor) {
    let isNegative = dividend < 0 ^ divisor < 0;
    let dd = Math.abs(dividend);
    let dr = Math.abs(divisor);
    let minValue = -(2**31);
    let maxValue = 2**31-1;
    
    let result = 0;
        
    while(dd >= dr){
        let count = 1;        
        let minutes = dr;
        while( dd >> 1 >= minutes){
            minutes = minutes<<1;
            count = count<<1;
        }
        result +=count;
        dd -= minutes;
    }    
    
    isNegative && (result = -result);
    
    return result<minValue||result>maxValue?
        maxValue:result;
};
```

