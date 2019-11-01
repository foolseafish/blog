# Valid Parentheses
## 描述
函数描述：(s:string) =>bool
假设入参'{}{}()[()][]',输出为true;'{}{}([)()][]',输出为false
## 思路
1.建立对应库,(对应),[对应],{对应}。
2.遍历字符串,如果当前字符与栈顶字符一致则出栈，否则入栈。
3.返回栈长 === 0
##实现
  ```javascript
const isValid = (s) => {
    let stack = [];
    for(let char of s){
        if(pairs[char] == stack[stack.length-1]){
            stack.pop();
        } else {
            stack.push(char);
        }
    }
    return stack.length === 0;
};
const pairs = {
    '[':']',
    ']':'[',
    '{':'}',
    '}':'{',
    '(':')',
    ')':'(',
}
  ```

