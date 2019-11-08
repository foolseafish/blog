# Decode Ways
## 描述
- 问题描述：对字符串进行解码，获取可能的密码种数。
- 函数类型：s:String=>int
## 细节介绍
异常情况较多需要注意：
1. 如果起始第一个字符为0，则输出为0。因为0没有对应字符
2. 最大字符为26,所以两个字符前一个字符大于2就不可能为一个字母了。
## 思路
1. 采用递归需要找到递归的逻辑。
2. 分析可以发现能组成一个字母的字符最大为两个，去除这两个字符，另外N个字符对应的种类是x,则加上这两个也为x,
3. 能组成一个字母的最小个数为1，所以同理另外N个字符对应的种类为y,加在这个字符也为y,种数应该为x+y。<br />
**注：其中另外N个字符，N可以为0,表示只有分析的这种情况，对应为1。**

## 实现
```javascript
const numDecodings = (s) => {
    if(s === '' || s.startsWith('0'))return 0;
    let arr = s.split('');
    return recursion(arr,arr.length-1);
};

const recursion = (arr,lastIndex)=>{
    if(lastIndex <= 0)return 1;
    let cur = arr[lastIndex];
    let prev = arr[lastIndex-1];
    let count = 0;
    if(cur>0)
        count += recursion(arr,lastIndex - 1);
    if(prev === '1' || prev === '2' && cur <= '6')
        count += recursion(arr,lastIndex - 2);
    return count;
    
}
```

