# Leetcode
876.https://leetcode.com/problems/middle-of-the-linked-list/description/
class Solution {
public:
    int size(ListNode* head)
    {
        ListNode* tmp=head;
        int cnt = 0;
        while(tmp!=NULL)
        {
            cnt++;
            tmp = tmp->next;
        }
        return cnt ;
    }
    ListNode* middleNode(ListNode* head) 
    {
        int sz=size(head);
        ListNode* tmp=head;
        for(int i=1;i<=sz/2;i++)
        {
            tmp=tmp->next;
        }
        return tmp;
    }
};
141.https://leetcode.com/problems/linked-list-cycle/description/
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* slow=head;
        ListNode* fast=head;
        while(fast!=NULL && fast->next!=NULL)
        {
            slow=slow->next;
            fast=fast->next->next;
            if(slow==fast)
            {
                return true;
            }
        }
        return false;
    }
};

83.https://leetcode.com/problems/remove-duplicates-from-sorted-list/
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(head==NULL) return head;
        ListNode* tmp=head;
        while(tmp->next!=NULL)
        {
            if(tmp->val==tmp->next->val)
            {
                tmp->next=tmp->next->next;
            }
            if(tmp->next==NULL) break;
            else if(tmp->val!=tmp->next->val)
            {
                tmp=tmp->next;
            }
        }
        return head;
    }
};

206 https://leetcode.com/problems/reverse-linked-list/description/

class Solution {
public:
    void reverse(ListNode *&head,ListNode *cur)
    {
        if(cur->next==NULL)
        {
            head=cur;
            return;
        }
        reverse(head,cur->next);
        cur->next->next=cur;
        cur->next=NULL;
    }
    ListNode* reverseList(ListNode* head) {
        if(head==NULL) return head;
        reverse(head, head);
        return head;
        
    }
};

19.https://leetcode.com/problems/remove-nth-node-from-end-of-list/
class Solution {
public:
    int size(ListNode *head)
    {
        ListNode* tmp=head;
        int cnt=0;
        while(tmp!=NULL)
        {
            cnt++;
            tmp=tmp->next;
        }
        return cnt;
    }
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int sz=size(head);
        ListNode* tmp=head;
        int pos=sz-n;
        if(pos==0) 
        {
            return
            head->next;
        }
        for(int i=1;i<=pos-1;i++)
        {
            tmp=tmp->next;
        }
        ListNode* deletedNode=tmp->next;
        tmp->next=tmp->next->next;
        delete deletedNode;
        //cout<<tmp<<endl;
        return head;
    }
};
