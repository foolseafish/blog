# Reverse Nodes in k-Group
## 描述
函数类型：（head:LinkNode,k:int）=>LinkNode
假设入参链表head为1->2->3->4->5，k=2，头指针h指向1,输出链表应该为2->1->4->3->5。
## 思路
1.以k为单位翻转链表。
  链表翻转操作一般用3个指针：prev,cur,next
  如描述示例执行：
  首先判断当前链表长度是否不足k,是则直接返回head;
  第一次：prev = null,cur = head,next,翻转节点： next = cur.next,cur.next = prev,prev = cur,cur = next,最后变成
  1 2->3->4->5,cur指向 2,prev指向1;
  第二次：prev = 1,cur = 2,翻转节点： next = cur.next,cur.next = prev,prev = cur,cur = next,最后变成
  1<-2 3->4->5,cur指向 3,prev指向2;
  这时候已经完成了以k为单位翻转了一部分链表,需要将指针1的next指向第二个翻转部分的头部。而指针1即为入参head，指针2(当前prev)即为翻转后的头部指针，由此可以得出采用递归实现前一组组的head指针的next指向后一组组的prev指针上就可以完成整个变换后链表的串联。上述过程即为递归函数体。
  ## 实现
  ```javascript
  const reverseKGroup = (head,k)=>{
      if(getListLength(head)<k)return head;
      let cur = head;
      let prev = null;
      let i = k;
      while(cur&& i-->0){
          let next = cur.next;
          cur.next = prev;
          prev = cur;
          cur = next;
      }
      head.next = reverseKGroup(cur,k);
      return prev;
  }

  const getListLength = (list)=>{
      let i = 0;
      let pointer = list;
      while(pointer){
          pointer = pointer.next;
          i++;
      }
      return i;
  }
  ```

