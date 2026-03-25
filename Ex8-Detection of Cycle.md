# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. Start the program.
2. Define a Node class containing data and next.
3. Create a linked list and manually introduce a cycle for testing.
4. Use Floyd’s Cycle Detection Algorithm (Tortoise and Hare method):
5. Move one pointer (slow) one step and another (fast) two steps.
6. If they meet, a cycle exists.
7. To find the start node of the cycle, reset one pointer to the head and move both one step at a time until they meet again.
8. Display the starting node of the cycle, or print “No cycle detected.” if none exists.
9. Stop the program.

## Program:
```
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: Reshma C
RegisterNumber:  212223040168
*/


class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class DetectCycleLinkedList {
    static Node detectCycle(Node head) {
        Node slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                Node entry = head;
                while (entry != slow) {
                    entry = entry.next;
                    slow = slow.next;
                }
                return entry;
            }
        }
        return null;
    }

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        head.next.next.next.next.next = head.next.next; // Create cycle

        Node cycleStart = detectCycle(head);
        if (cycleStart != null)
            System.out.println("Cycle detected at node with value: " + cycleStart.data);
        else
            System.out.println("No cycle detected.");
    }
}
```

## Output:

<img width="1292" height="397" alt="image" src="https://github.com/user-attachments/assets/dbc4067b-f61f-4a95-a0c3-ea0d47a16ab6" />


## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
