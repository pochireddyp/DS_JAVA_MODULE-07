# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE:26-11-2025
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. Start slow = head and fast = head.
2. Move slow by 1 step and fast by 2 steps until they meet or fast becomes null.
3. If fast becomes null, return null (no cycle).
4. Move slow to head, keep fast at meeting point.
5. Move both one step at a time until they meet — this node is the cycle start.
6. 
## Program:
```PY
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: pochireddy p
RegisterNumber:  212223240115
*/
class DetectCycle {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static Node detectCycle(Node head) {
        if (head == null || head.next == null) 
            return null;

        Node slow = head;
        Node fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;          
            fast = fast.next.next;     

            if (slow == fast) {        
                break;
            }
        }

        if (fast == null || fast.next == null)
            return null;

        slow = head;
        while (slow != fast) {
            slow = slow.next;
            fast = fast.next;
        }

        return slow;   
    }

    public static void main(String[] args) {

        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        head.next.next.next.next.next = head.next.next;

        Node cycleStart = detectCycle(head);

        if (cycleStart != null)
            System.out.println("Cycle starts at node: " + cycleStart.data);
        else
            System.out.println("No cycle detected.");
    }
}
```

## Output:
<img width="798" height="175" alt="image" src="https://github.com/user-attachments/assets/d1822ec8-415e-4040-b0c9-7915d513f19e" />



## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
