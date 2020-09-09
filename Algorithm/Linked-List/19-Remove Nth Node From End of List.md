# Remove Nth Node From End of List
## 描述
## 细节介绍 

## 实现
```javascript
var removeNthFromEnd = function(head, n) {
  let prev = head;
    
    while(prev){
        let next = prev;
        let num = n;
        while(num && next.next){
            num--
            next = next.next;
        }        
        if(prev === next)return null;
        if(num > 0)return head.next;
        if(!next.next){
            prev.next = n === 1?null:prev.next.next;
            break;
       }   
        prev = prev.next;
    }
    return head;
};

 const removeNthFromEnd = (n,head)=>{
        if(n<=0)return head;
        let parent = new ListNode();
        parent.next = head;
        let slow = parent;
        let fast = parent;

        let loop = n + 1;
        while(loop && fast){
            fast = fast.next;
            loop--;
        }            
        if(!fast && loop>0)return head;
        while(fast){
            slow = slow.next;
            fast = fast.next;
        }
        slow.next = slow.next.next;
        return parent.next;
    }
```

