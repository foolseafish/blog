# Merge k Sorted Lists
## 描述
- 问题描述：对多个有序链表归并,返回归并后的列表,是归并排序的并部分;
- 函数类型：(lists:ListNode[]) =>ListNode
## 思路
1. **所有需要交换链表的操作，先建头部指针fakeHead**，创建cur指向当前fakeHead指针对象。
2. 由于是不定个数需要先判断入参,当入参为[]时需要返回空字符串‘’(返回空ListNode会报错，感觉是BUG)。
3. 利用[].reduce做归并
4. 并操作的典型判断：1.左有序对象是否已经遍历完，是则把右侧拷贝到输出对象上。2.右同理3.如果左当前对象小于右，则拷贝左，否则拷贝右。
## 实现
```javascript
const mergeKLists = (lists) => {    
    if(lists.length == 0) return '';
    return lists.reduce((prev,cur)=>{
        let fakeNode = new ListNode(null);
        let curNode = fakeNode;
        while(true){
           if(!prev && !cur)return fakeNode.next;
           if(!prev){
               curNode.next = cur;
               cur = cur.next;
           } else if(!cur){
               curNode.next = prev;
               prev = prev.next;
           } else if(cur.val<prev.val){
               curNode.next = cur;
               cur = cur.next;
           } else {
               curNode.next = prev;
               prev = prev.next;
           }
            curNode = curNode.next;
        }        
    })
};
```

