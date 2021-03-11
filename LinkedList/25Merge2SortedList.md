

# 合并两个有序链表

## 1. 基础题：合并两个有序链表

## 第一种解法：递归解法

```c++
ListNode* mergeTwoLists(ListNode* l1, ListNode* l2)
{
    if( !l1 ) return l2;
    if( !l2 ) return l1;
    
    if( l1->val < l2->val )
    {
        l1->next = mergeTwoLists(l1->next, l2);
        return l1;
    }
   	else
    {
        l2->next = mergeTwoLists(l1, l2->next);
        return l2;
    }
}


```

## 第二种解法：迭代法

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */

    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        
        if( !l1 ) return l2;
        if( !l2 ) return l1;
        
        // 新建虚拟头结点
        ListNode* dummy = new ListNode(0);
        ListNode* p = dummy;

        while( l1 && l2 )
        {

            if( l1->val < l2->val )
            {
                p->next = l1;
                l1 = l1->next;
            }
            else
            {
                p->next = l2;
                l2 = l2->next;
            }

            p = p->next;

        }

        // 判断是否有非空链表
        if( l1 ) p->next = l1;
        if( l2 ) p->next = l2;
        
        return dummy->next;
    }

```

