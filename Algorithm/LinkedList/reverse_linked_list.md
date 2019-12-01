#  Reverse Linked list

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

Iterative way
-------------

In this lesson we will see about how to reverse the singly linked list, Reversing the singly linked list is one of the classical problem in linked list.

Here the linked list is 1->2->3->4->5->null. Here each node is an object which holds the reference of the next object in the list. For example. The object node 1 holds the reference of object 2.

Now we need to reverse this list as 5->4->3->2->1-> null

In this lesson we will see how to iteratively solve this problem. I have solved the same problem recursively the link of which I gave in the description.


```JAVA
public ListNode reverseLinkedList(ListNode head){
  ListNode curr=head;
  ListNode reverseList=null;
  while(curr!=null){
    ListNode node=new ListNode(curr.val);
    node.next=reverseList;
    reverseList=node;
    curr=curr.next;
  }
  return reverseList;
}

```
First we will assign the curr ListNode to refer the head. head is the start node of entire list. So now the curr refers to the head. Declare a new reverseList ListNode reference and assign null to it.
If the curr is not null then continue with the while loop. Create a new ListNode node with the value 1 present in the curr ListNode. Now assign the next reference of the node to the reverseList which holds null now. Assign node to the reverseList. ReverseList holds 1 and null. Now point the curr to refer the next node in the linked list.

Now curr holds the nodes starting from 2 to 5. Create a new ListNode node with the value 2 present in the curr ListNode. Now assign the next reference of the node to the reverseList which holds 1 and null now. Assign node to the reverseList. ReverseList holds 2, 1 and null. Now point the curr to refer the next node in the linked list.

Now curr holds the nodes starting from 3 to 5. Create a new ListNode node with the value 3 present in the curr ListNode. Now assign the next reference of the node to the reverseList which holds 2,  1 and null now. Assign node to the reverseList. ReverseList holds 3, 2, 1 and null. Now point the curr to refer the next node in the linked list.

Now curr holds the nodes 4 and 5. Create a new ListNode node with the value 4 present in the curr ListNode. Now assign the next reference of the node to the reverseList which holds 3, 2,  1 and null now. Assign node to the reverseList. ReverseList holds 4, 3, 2, 1 and null. Now point the curr to refer the next node in the linked list.

Now curr holds the node 5. Create a new ListNode node with the value 5 present in the curr ListNode. Now assign the next reference of the node to the reverseList which holds 4, 3, 2,  1 and null now. Assign node to the reverseList. ReverseList holds 5, 4, 3, 2, 1 and null. Now point the curr to refer the next node in the linked list.

Now curr holds the value null so terminate the while loop and return the reverseList which holds the nodes from 5 to 1. Now we have the reversed the linked list.

The time complexity of the above solution is O(n) and the space complexity is O(n). Can we able to improve the space complexity. Yes we can able to do it.

Now we will see how to improve the space complexity to make it O(1).

```java

public ListNode reverseLinkedList(ListNode head){
  ListNode curr=head;
  ListNode reverseList=null;

  while(curr!=null){
    ListNode temp=curr.next;
    curr.next=reverseList;
    reverseList=curr;
    curr=temp;
  }
  return reverseList;

}
```


Here instead of creating a new object we will just change the next reference of each node so that it points in the reverse direction.
First we will assign the curr ListNode to refer the head. head is the start node of entire list. So now the curr refers to the head. Declare a new reverseList ListNode reference and assign null to it.

Now we need we need only the first object in the list and need to store the remaining objects. So create a temp reference which hold the curr.next. So temp holds the nodes from 2 to 5 now. Now point the curr.next to the reverseList reference which holds null now. Now assign the curr to the reverseList. Here curr holds 1 and null. Now assign the temp to the curr ListNode.

Now curr holds the nodes starting from 2 to 5. Point the temp to refer the curr.next. Now temp holds node from 3 to 5. Now refer the curr.next to hold the reverseList which the nodes 1 and null. Now assign the curr to the reverseList, curr holds 2,1 and null. Now assign the temp to the curr ListNode.

Now curr holds the nodes starting from 3 to 5. Point the temp to refer the curr.next. Now temp holds nodes 4 which refer to node 5. Now refer the curr.next to hold the reverseList which the nodes 2, 1 and null. Now assign the curr to the reverseList, curr holds 3, 2,1 and null. Now assign the temp to the curr ListNode.

Now curr holds the nodes starting from 4 to 5. Point the temp to refer the curr.next. Now temp hold node 5. Now refer the curr.next to hold the reverseList which the nodes 3, 2, 1 and null. Now assign the curr to the reverseList, curr holds 4, 3, 2, 1 and null. Now assign the temp to the curr ListNode.

Now curr hold  the node  5. Point the temp to refer the curr.next. Now temp holds null. Now refer the curr.next to hold the reverseList which the nodes 4, 3, 2, 1 and null. Now assign the curr to the reverseList, curr holds 5, 4, 3, 2, 1 and null. Now assign the temp to the curr ListNode.

Now the curr is null so we will terminate the while loop.

The time complexity of this solution is O(n) and the space complexity is O(1).

Recursive way
--------------

In this lesson we will see about how to reverse the singly linked list, Reversing the singly linked list is one of the classical problem in linked list.

Here the linked list is 1->2->3->4->5->null. Here each node is an object which holds the reference of the next object in the list. For example. The object node 1 holds the reference of object 2.

Now we need to reverse this list as 5->4->3->2->1-> null

In this lesson we will see how to recursively solve this problem. I have solved the same problem iteratively the link of which I gave in the description.



```JAVA
public ListNode reverseLinkedList(ListNode head){
  if(head==null ||head.next=null) return head;
  ListNode reverseList=reverseLinkedList(head.next);
  head.next.next=head;
  head.next=null;
  return reverseList;
}

```
The base case if the node is null or node's next reference is null. Here node null check just to make sure the input is not empty linked list.


 The input list contains 1, 2, 3, 4, and 5. It will recursively call the reverseLinkedList again with the list 2, 3, 4 and 5. Again, It recursively calls the reverseLinkedList again with the list 3, 4 and 5.
Again, It recursively calls the reverseLinkedList with the list 4 and 5. Again It recursively calls the reverseLinkedList function with the node 5. Here the node 5's next is null so return the head and assign its reference to reverseList ListNode and assign head.next.next as 5 and head.next as null. The recursive calls will be stored in the form the stack. Now the next in the stack holds the list 4 and 5. Now the head is 4 and assign it to the head.next.next so the reverseList is now 5, 4 and null. Now the next in the stack holds the list 3, 4 and 5. Now the head is 3 and assign it to the head.next.next so the reverseList is now 5, 4, 3 and null. Now the next in the stack holds the list 2, 3, 4 and 5. Now the head is 2 and assign it to the head.next.next so the reverseList is now 5, 4, 3, 2 and null. Now the next in the stack holds the list 1, 2, 3, 4 and 5. Now the head is 1 and assign it to the head.next.next so the reverseList is now 5, 4, 3, 2, 1 and null. Now we have reversed the Singly linked list recursively using recursion.

The time complexity of this algorithm is 0(n) and the space complexity is O(n) because the recursive solution uses stack to store the steps so it takes O(n) space  complexity.
