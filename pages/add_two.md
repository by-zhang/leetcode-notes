Two non-negative integers are represented in two linked lists and the digits are stored
in reverse order.
For example:   807 7->0->8
	
	ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *resList = new ListNode(0);
        ListNode *p = l1, *q = l2, *cur = resList;
        int carry = 0;
        while ( p != NULL || q != NULL || carry != 0) { //Dont neglect carry condition.
            int x = 0, y = 0;
            if (p != NULL) {            //0 for NULL pointer.
                x = p->val;
                p = p->next;
            }
            if (q != NULL) {
                y = q->val;
                q = q->next;
            }
            cur->next = new ListNode((x + y + carry) % 10);
            cur=cur->next;
            carry = (x+y+carry)/ 10;    //carry must be calculated with the last carry.
        }
        return resList->next;
    }
