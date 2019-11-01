# Kth Smallest Element in a BST
## 描述
问题描述：给定一棵二叉树tree和整数k,返回第k小的值。
函数类型：（root:TreeNode,k:int）=>number
假设入参root=   
&nbsp&nbsp&nbsp3
&nbsp&nbsp/&nbsp\
 1&nbsp&nbsp&nbsp4
 &nbsp\
 &nbsp&nbsp2  ,k=2，输出 2。
## 思路
1.中序遍历搜索二叉树，输出升序数组
2.返回数组第k个值
## 实现
```javascript
const inorder = (node,array)=>{
    if(node === null)return;
    inorder(node.left,array);
    array.push(node.val);
    inorder(node.right,array);
};

const kthSmallest = function(root, k) {
    let array = [];
    inorder(root,array);
    return array[k-1];
};
  ```

