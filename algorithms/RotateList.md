# Rotate List

The first step of the code is to count the number of nodes in the Linked List. Once this value is determined, the algorithm will determine how many nodes from the end of the list need to be moved to the beginning. Next, the algorithm will traverse the list to the node just before the inversion point, set its 'next' value to null, and then move the subsequent node to the beginning of the list by making it reference the old first node.

### Code complexity
Time complexity **O(n)** \
Space complexity: **O(1)**

### Java implementation

``` Java
package rotatelist;

public class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) {
        this.val = val;
    }
    ListNode(int val, ListNode next) {
        this.val = val;
        this.next = next;
    }
}
```

``` Java
package rotatelist;

public class Solution {
    public static void main(String[] args){
        var linkedList = new ListNode(1);
        linkedList.next = new ListNode(2);
        linkedList.next.next = new ListNode(3);
        linkedList.next.next.next = new ListNode(4);
        linkedList.next.next.next.next = new ListNode(5);
        (new Solution()).rotateRight(linkedList, 0);
    }

    public ListNode rotateRight(ListNode head, int k) {
        if (head == null) {
            return null;
        }

        var counter = head;
        var lengthNodes = 0;
        while (counter != null) {
            lengthNodes += 1;
            counter = counter.next;
        }

        k = k % lengthNodes;
        if (k > 0) {
            var temp = head;
            for (int i = 0; i < lengthNodes - k; i++) {
                if (i == lengthNodes - k - 1) {
                    var next = temp.next;
                    temp.next = null;
                    temp = next;
                    break;
                }
                temp = temp.next;
            }
            counter = temp;
            while (counter != null) {
                if (counter.next == null) {
                    counter.next = head;
                    break;
                }
                counter = counter.next;
            }
            head = temp;
        }
        return head;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/rotate-list/)
