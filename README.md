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
1721.https://leetcode.com/problems/swapping-nodes-in-a-linked-list/
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
   int size(ListNode*head)
   {
    ListNode*tmp=head; 
    int count=0;
    while(tmp!=NULL)
    {
        count++;
        tmp=tmp->next;
    }
    return count;
   }
    ListNode* swapNodes(ListNode* head, int k) {
        if(head==NULL)
        {
            return head;
        }
        int pos=size(head)-k;
        ListNode*tmp=head;
        for(int i=1;i<=k-1;i++)
        {
            tmp=tmp->next;
           // cout<<tmp->val;
        }
        ListNode*tmp2=head;
        for(int i=1;i<=pos;i++)
        {
            tmp2=tmp2->next;
           // cout<<tmp2->val;
        }
        swap(tmp->val,tmp2->val);
        return head;
    }

};

remove duplicate (stl using list)
#include <bits/stdc++.h>
using namespace std;
int main()
{
    list<int>mylist;
    int val;
    while(cin>>val && val!=-1)
    {
        mylist.push_back(val);
    }

    mylist.sort();
    mylist.unique();
    for(int val:mylist)
    {
        cout<<val<<" ";
    }

    return 0;
}


palindrome doubly linke list
#include <bits/stdc++.h>
using namespace std;
class Node
{
    public:
        int val;
        Node* next;
        Node* prev;
    Node(int val)
    {
        this->val=val;
        this->next=NULL;
        this->prev=NULL;
    }
};
take_input(Node*&head,Node*&tail,int val)
{
    Node *newNode= new Node(val);
    if(head==NULL)
    {
        head=newNode;
        tail=newNode;
        return;
    }
    tail->next=newNode;
    newNode->prev=tail;
    tail=tail->next;
}
void reverse(Node*head,Node*tail)
{
    Node*i=head;
    Node*j=tail;
    while(i!=j && i->next!=j)
    {
        swap(i->val,j-val);
        i=i->next;
        j=k->next;
    }
    swap(i->val,j->val);
}
bool palindrome(Node*head,Node*tail)
{
    Node* newhead=NULL;
    Node* newtail=NULL;
    Node* tmp=head;
    while(tmp!=NULL)
    {
        take_input(newhead,newtail,tmp->val)
        tmp=tmp->next;
    }
    reverse(head,tail);
    tmp=head;
    Node*tmp2=newhead;
    while(tmp!=NULL)
    {
        if(tmp->val!=tmp2->val)
        {
            return false;
        }
        tmp=tmp->next;
        tmp2=tmp2->next;
    }
    return true;
}
int main()
{
    Node* head=NULL;
    Node* tail=NULL;
    int val;
    while(true)
    {
        cin>>val;
        if( val==-1) break;
        take_input(head,tail,val);
    }
    bool x=palindrome(head,tail);
    if(x==true){
        cout<<"YES IS PALINDROME";
    }
    else
    {
        cout<<"No";
    }
    return 0;
}


https://leetcode.com/problems/valid-parentheses/

class Solution {
public:
    bool isValid(string s)
    {
        stack<char>st;
        for(char c:s)
        {
            if(c== '(' || c== '{' || c=='[' )
            {
                st.push(c);
            }
            else
            {
                if(st.empty())
                {
                    return false;
                }
                else
                {
                    if(c==')' && st.top()=='(')
                    {
                        st.pop();
                    }
                    else if(c=='}'&& st.top()=='{')
                    {
                        st.pop();
                    }
                    else if(c==']'&& st.top()=='[')
                    {
                        st.pop();
                    }
                    else 
                    {
                        return false;
                    }
                }
            }
        }
        return st.empty();
    }

};


https://leetcode.com/problems/backspace-string-compare/description/
class Solution
{
public:
    bool backspaceCompare(string s, string t)
    {
        stack<char> s1, s2;
        for (char c : s)
        {
            if (c == '#')
            {
                if (!s1.empty())
                    s1.pop();
            }
            else
            {
                s1.push(c);
            }
        }
        for (char c : t)
        {
            if (c == '#')
            {
                if (!s2.empty())
                    s2.pop();
            }
            else
            {
                s2.push(c);
            }
        }
        return s1 == s2;
    }
};


10101 #last digit

#include <bits/stdc++.h>
using namespace std;
int main()
{
    int t;
    cin>>t;
    while(t--)
    {
        string s;
        cin>>s;
        stack<char>st;

        for(char c:s)
    {
            if(st.empty())
            {
            st.push(c);
            }
        else if(c=='1' && st.top()=='0')
        {
            st.pop();
        }
        else if(c=='0' && st.top()=='1')
        {
            st.pop();
        }
        
        else
        {
            st.push(c);
        }
    }

        if(st.empty()) cout<<"YES"<<endl;
        else
        {
            cout<<"NO"<<endl;
        }
    }

    

    return 0;
}
/*
#include <bits/stdc++.h>
using namespace std;

int main()
{
    int t;
    cin>>t;
    while(t--)
    {
        string s;
        cin>>s;
        deque<char> q;

        for(char c : s)
        {
            if(q.empty())
            {
                q.push_back(c);
            }
            else if((c == '1' && q.back() == '0') || (c == '0' && q.back() == '1'))
            {
                q.pop_back();
            }
            else
            {
                q.push_back(c);
            }
        }

        if(q.empty()) 
            cout << "YES" << endl;
        else 
            cout << "NO" << endl;
    }

    return 0;
}

*/







https://www.naukri.com/code360/problems/maximum-equal-stack-sum_1062571?leftPanelTabValue=PROBLEM

#include <bits/stdc++.h> 
int getSum(stack<int>s)
{
    int sum=0;
    while(!s.empty())
    {
        sum+=s.top();
        s.pop();
    }
    return sum;
}
int maxSum(stack<int> &s1, stack<int> &s2, stack<int> &s3)
{
    // Write your code here
    int sum1=getSum(s1);
    int sum2=getSum(s2);
    int sum3=getSum(s3);

   // cout<<sum1<<" "<<sum2<<" "<<sum3<<" "<<endl;
   while(true)
   {
       if(sum1==sum2 && sum2==sum3)
         break;
        if (sum1 >= sum2 && sum1 >= sum3)
        {
            sum1 -= s1.top();
            s1.pop();
        }
        else if (sum2 >= sum1 && sum2 >= sum3)
        {
            sum2 -= s2.top();
            s2.pop();
        }
        else
        {
            sum3 -= s3.top();
            s3.pop();
        }
   }
   return sum1;   
}


https://www.naukri.com/code360/problems/reversing-a-queue_982934
#include <bits/stdc++.h> 
queue<int> reverseQueue(queue<int> q)
{
    // Write your code here.
    stack<int>s;

    while(!q.empty())
    {
        s.push(q.front());
        q.pop();
    }
    while(!s.empty())
    {
        q.push(s.top());
        s.pop();
    }
    return q;
}

https://www.naukri.com/code360/problems/reverse-stack-using-recursion_631875

void reverseStack(stack<int> &s) {
    // Write your code here
    if(s.empty()) return;
    int x=s.top();//top reka dici
    s.pop();
    reverseStack(s);
    //reverse hoya gase

    stack<int>cp;
    while(!s.empty())
    {
        cp.push(s.top());
        s.pop();
    }

    cp.push(x);//copy er modde x push kora
    while(!cp.empty())
    {
        s.push(cp.top());
        cp.pop();
    }
}




https://www.naukri.com/code360/problems/implement-stack-with-linked-list_630475?leftPanelTabValue=PROBLEM

/****************************************************************

    Following is the class structure of the Node class:

        class Node
        {
        public:
            int data;
            Node *next;
            Node()
            {
                this->data = 0;
                next = NULL;
            }
            Node(int data)
            {
                this->data = data;
                this->next = NULL;
            }
            Node(int data, Node* next)
            {
                this->data = data;
                this->next = next;
            }
        };


*****************************************************************/

class Stack
{
    //Write your code here
     Node* head;
    int sz;

public:
    Stack()
    {
        head=NULL;
        sz=0;
    }

    int getSize()
    {
        //Write your code here
        return sz;
    }

    bool isEmpty()
    {
        return sz == 0;
        
    }

    void push(int data)
    {
        sz++;
        Node *newNode=new Node(data);
        newNode->next = head;
        head=newNode;
    }

    void pop()
    {
         if (isEmpty()) return;
         Node* temp = head;
         head = head->next;
         delete temp;
         sz--;
    }

    int getTop()
    {
        if (isEmpty()) return -1;
        return head->data;  
    }
};


https://www.naukri.com/code360/problems/kevin-s-stack-problem_1169465?leftPanelTabValue=SOLUTION
{
solve this
}


//same or not hacker_rank_problem
#include <bits/stdc++.h>
using namespace std;
int main()
{
    int n,m;
    cin>>n>>m;
    stack<int>st;
    queue<int>q;
    for(int i=0;i<n;i++)
    {
        int x;
        cin>>x;
        st.push(x);
    }

    for(int i=0;i<m;i++)
    {
        int y;
        cin>>y;
        q.push(y);
    }

    bool flag;
    if(st.size()!=q.size())
    {
        cout<<"NO"<<endl;
    }

    else
    {
        while(!st.empty())
        {
            if(st.top() != q.front())    
            {
                flag=false;
                break;
            }
            else
            {
                flag=true;
                st.pop();
                q.pop();
            }
        }
        if(flag==true) cout<<"YES"<<endl;
        else cout<<"NO"<<endl;
    }


    return 0;
}

[[Is Node Present? - Coding Ninjas 
Node Level - Coding Ninjas 
Left View Of a Binary Tree - Coding Ninjas 
Diameter Of Binary Tree - Coding Ninjas 
(https://docs.google.com/document/d/1UjqSc79POHOPFPt3Xwzpbgi0J4C1IGl0qY1qzJrFGwM/edit)](https://docs.google.com/document/d/1UjqSc79POHOPFPt3Xwzpbgi0J4C1IGl0qY1qzJrFGwM/edit)


https://www.naukri.com/code360/problems/special-binary-tree_920502
#include <bits/stdc++.h> 
/*************************************************************

    Following is the Binary Tree node structure

    class BinaryTreeNode
    {
    public :
        T data;
        BinaryTreeNode<T> *left;
        BinaryTreeNode<T> *right;

        BinaryTreeNode(T data) {
            this -> data = data;
            left = NULL;
            right = NULL;
        }
    };

*************************************************************/

bool isSpecialBinaryTree(BinaryTreeNode<int>* root)
{
    // Write your code here.
    if(root->left==NULL && root->right==NULL) 
        return true;
    if(root->left==NULL || root->right==NULL)
        return false;
    bool l= isSpecialBinaryTree(root->left);
    bool r= isSpecialBinaryTree(root->right);
    if(l==false || r==false) return false;
    return true;
}

https://www.naukri.com/code360/problems/reverse-level-order-traversal_764339?leftPanelTabValue=SUBMISSION
/************************************************************

    Following is the TreeNode class structure:

    template <typename T>

    class TreeNode {
    public:
        T val;
        TreeNode<T> *left;
        TreeNode<T> *right;
        TreeNode(T val) {
            this->val = val;
            left = NULL;
            right = NULL;
        }
    };

************************************************************/
#include<bits/stdc++.h>
vector<int> reverseLevelOrder(TreeNode<int> *root){
    // Write your code here.
    vector<int>v;
    queue<TreeNode<int> *>q;
    if(root) q.push(root);
    while(!q.empty())
    {
        TreeNode<int> * node=q.front();
        q.pop();

        v.push_back(node->val);

        if(node->left) q.push(node->left);
        if(node->right) q.push(node->right);
    }
    reverse (v.begin(),v.end());
    return v; 
}


https://leetcode.com/problems/root-equals-sum-of-children/
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool checkTree(TreeNode* root) {
        if(root->val == root->left->val + root->right->val) 
              return true;
        else
              return false; 
        
        
    }
};
















