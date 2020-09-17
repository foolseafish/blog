# 中序遍历
## 描述
- 树的先序遍历顺序：1.左 2.根 3.右
- 中序遍历经常在BST中用到。
## 思路
递归思路比较简单：
1.递归左节点
2.先输出根
3.递归右节点

非递归思路：利用栈
1. 入栈根节点
2. 循环入栈左侧节点，直到左侧无节点。
3. 出栈栈顶节点(左侧无节点，即该节点是个叶子节点或者是只带有右侧节点的根节点)，指向该节点的右侧节点，再执行2.

## 实现
```javascript
const inorderTraversal  = (node)=>{    
    return node
    ? inorderTraversal(node.left).concat([node.val]).concat(inorderTraversal(node.right))
    :[];
}

//非递归。
const inorderTraversal  = (root) =>{
    if(!root)return;
    const result = [];
    const stack = [root];
    let curNode = root;
    while(stack.length){
        if(curNode.left){
            curNode = node.left;
            stack.push(curNode);
            continue;
        }
        curNode = stack.pop();
        result.push(curNode);
        curNode = curNode.right;
    }
    return result;
}
```

