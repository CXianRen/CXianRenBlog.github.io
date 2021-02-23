### 题目:
+ 给你两个 非空 的链表，表示两个非负的整数。它们每位数字都是按照 逆序 的方式存储的，并且每个节点只能存储 一位 数字。请你将两个数相加，并以相同形式返回一个表示和的链表

### 解
```c++
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int a=0,b=0,c=0;
        ListNode *res=new ListNode();
        ListNode *h=res;
        while(true){
            a=0,b=0;
            if(l1)a=l1->val;
            if(l2)b=l2->val;
            if(l1!=nullptr || l2!=nullptr || c>0){
                c=a+b+c;
                res->next=new ListNode(c%10);
                res=res->next;
                c=c/10;
                if(l1)l1=l1->next;
                if(l2)l2=l2->next;
            }else{
                break;
            }
        }
        return h=h->next;
    }
};
//res 	44 ms	69.6 MB
```

### 思考:
> 和加法有关的必定要考虑进位的问题


