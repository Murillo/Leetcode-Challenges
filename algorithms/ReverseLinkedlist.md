# Reverse Linked List
For this challenge, recursion was used to invert the LinkedList. The function will go to the last node, and then begin the inversion process.

1 -> 2 -> 3 -> 4 -> 5\
1 -> 2 -> 3 -> 5 -> 4\
1 -> 2 -> 5 -> 4 -> 3\
1 -> 5 -> 4 -> 3 -> 2\
5 -> 4 -> 3 -> 2 -> 1


### Code complexity
Time complexity **O(n)** Function will traverse all LinkedList nodes\
Space complexity: **O(n)** The recursion adds the reference of each method to the stack

### Java implementation

``` Java
package reverselinkedlist;

public class ListNode {
    int val;
    ListNode next;

    ListNode() {}

    ListNode(int val) {
        this.val = val;
    }

    ListNode(int val, ListNode next) {
        this.val = val; this.next = next;
    }
}

```

``` Java
package reverselinkedlist;

public class Solution {

    public static void main(String[] args){
        var linked_list = new ListNode(1);
        linked_list.next = new ListNode(2);
        linked_list.next.next = new ListNode(3);
        linked_list.next.next.next = new ListNode(4);
        linked_list.next.next.next.next = new ListNode(5);
        (new Solution()).reverseList(linked_list);
    }

    public ListNode reverseList(ListNode head) {
        if (head == null) {
            return null;
        }
        if (head.next == null) {
            return head;
        }
        var result = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return result;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/reverse-linked-list/)
