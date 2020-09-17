# 先序遍历
## 描述
- 树的先序遍历顺序：1.根2.左 3.右
## 思路
递归思路比较简单：
1.先输出根
2.递归左节点
3.递归右节点

非递归思路：利用栈
1. 入栈根节点
2. 出栈上层节点
3. 入栈右节点（因为先入后出）
4. 入栈左节点

## 实现
```javascript
const preorderTraversal = (node)=>{    
     return node
    ? [node.val].concat(preorderTraversal(node.left)).concat(preorderTraversal(node.right))
    :[];
}

//非递归。
const preorderTraversal = (root) =>{
    if(!root)return;
    const result = [];
    const stack = [root];
    while(stack.length){
        const node = stack.pop();
        result.push(node);
        if(node.right)stack.push(node.right); //先right，保证left先出栈
        if(node.left)stack.push(node.left);
    }
    return result;
}
```

