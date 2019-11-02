# Merge Two Sorted Lists
## 描述
问题描述：对两个有序链表归并,返回归并后的列表,是归并排序的并部分;
函数类型：(l1:ListNode, l2:ListNode) =>ListNode
## 思路
1.所有需要交换链表的操作，先建头部指针fakeHead，并创建cur指向当前fakeHead指针对象。
2.循环，先判断当前l1,当前l2是不是都已为null,是则返回fakeHead的next指针对象。
3.并操作的典型判断：1.左有序对象是否已经遍历完，是则把右侧拷贝到输出对象上。2.右同理3.如果左当前对象小于右，则拷贝左，否则拷贝右。
## 实现
```javascript
const mergeTwoLists = (l1, l2) => {
    let fakeHead = new ListNode(null);
    let cur = fakeHead;
    while(true){
        if(!l1 && !l2)return fakeHead.next;
        if(!l1){
            cur.next = l2;
            l2 = l2.next;
        } else if(!l2) {
            cur.next = l1;
            l1 = l1.next;
        } else if(l1.val<=l2.val){
            cur.next = l1;
            l1 = l1.next;            
        } else{
            cur.next = l2;
            l2 = l2.next;            
        }
        cur = cur.next;
    }
};
```

