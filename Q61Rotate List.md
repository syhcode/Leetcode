## Q61[ Rotate List  ](https://leetcode.com/problems/rotate-list/) 

### Solution 1 
#### Idea:
Since k may be bigger than length of the list, thus count length of the list first and then get the "i-k%i" pointer and do rotation.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode rotateRight(ListNode head, int k) {
   
    if (head==null||head.next==null||k==0) return head;
    ListNode fake=new ListNode(0);
    fake.next=head;
    ListNode fast=fake,slow=fake;
    int i=0;
    for (i=0;fast.next!=null;i++)//get the total length and rear
        fast=fast.next;

    for (int j=i-k%i;j>0;j--) //get the former part rear
        slow=slow.next;

    fast.next=fake.next; // rotate list
    fake.next=slow.next;
    slow.next=null;

    return fake.next;
    }

}
```
#### Reference:

---

