

# 设计一个获取最小元素的栈



https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/

## 1. 设计思路

​	使用单链表结构来实现可以在常数时间内获取栈中最小元素的数据结构。

```c++
class MinStack {
public:
    /** initialize your data structure here. */
    
    void push(int x) {
        // 判断是否头结点是否为空
        if( !head ) head = new Node(x, x);
        else head = new Node(x, ::min(head->_min, x), head);
    }
    
    void pop() {
        
        if( !head ) return ;
        Node* tmp = head;
        head = head->next;
        delete tmp;

    }
    
    int top() {
        return head->_val;
    }
    
    
    int min() {
        
        return head->_min;

    }


private:
    
    class Node
    {
        public:
            int _val;	// 每个节点的值
            int _min; 	// 记录链表中的最小值
            Node* next;	// 指针域
        	
        	// constructor
            Node( int val, int min, Node* next = nullptr )
            {
                _val = val;
                _min = min;
                this->next = next;
            }

    };
    
    Node *head;
       
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->min();
 */
```

