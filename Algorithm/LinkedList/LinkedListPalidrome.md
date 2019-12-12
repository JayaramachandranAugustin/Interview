#  Find Palindrome in Linked list

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson, we will see how to check if the linked list is Palindrome or not.
Palindrome sequence is a sequence that reads the same backward as forward. For example: Madam. This string reads both Madam from forward as well as backwards.

Let's take a linked list example 1 -> 2 -> 3 -> 2 -> 1. It reads both same from forward and backward.

One easy solution is to reverse the linked list and store it as a new copy and compare it with the original linked list. If both the reversed linked list and original list matches then the given list is Palindrome.
This is simple and straight forward.
The time complexity of this solution is O(n) and the space complexity is O(n).

To reverse a Linked list you can refer to my video tutorial, The link of which I gave in the description. You can use the approach 1 in the iterative way and get a copy of the linked list and compare the values of the original linked list and reversed linked list.

There is another approach to get the solution for this problem. The idea is to divide the list into two parts and reverse the second half and compare it with the first part. If both are same then it is palindrome.

 This can be achieved by using two pointers. First point two pointers at the head of the list. we will mark one as fast and one as slow, for each iteration move the fast pointer two steps and slow pointers one step towards right. Continue this till fast is not pointing to null or next reference of fast is not null.

 When the fast reaches null or next of fast is null the slow pointer will be in center for odd count of list and the slow pointer will be pointing to first element of second half if the count is even.

In this example the there are odd number of nodes in the linked lists so the slow pointers point the center which is node 3.
 Now we will reverse the list starting from the slow pointer. Here I am using the itera0tive approach to reverse the Linked list. Here I following the approach 2 in the iterative way from my video . The link of which I gave in the description. The time complexity of this reversing algorithm is O(n) and the space  complexity is O(1)

Once you reverse the second half the next reference of the second half starting will become null. So here the next reference of the 3 becomes null.

Now point the fast pointer to head and starting comparing both the pointer values if the values are matching then continue if not return false.

The time complexity of this algorithm is O(n) and the space complexity of this algorithm is O(1).

Now we will see the java implementation of this approach


```java

class PalindromeList{
  static class ListNode{
      int val;
      ListNode next;
      ListNode (int x){
        val=x;
        next=null;
      }
  }
  public boolean checkPalindrome(ListNode head){
      ListNode fast=head;
      ListNode slow =head;

      if(fast!=null && fast.next!=null){
        fast=fast.next.next;
        slow=slow.next;
      }

      slow=reverseLinkedList(slow);
      fast=head;

      while(fast!=null){
        if(fast.val!=slow.val) return false;
        fast=fast.next;
        slow=slow.next;
      }
      return true;
  }

  public ListNode reverseLinkedList(ListNode head){
    ListNode curr=head;
    ListNode revList=null;
    while(curr!=null){
      ListNode temp=curr.next;
      curr.next=revList;
      revList=curr;
      curr=temp;
    }
    return revList;
  }

  public static void main(String[] args) {
    PalindromeList palindromeList=new PalindromeList();
    ListNode head=new ListNode(1);
    head.next=new ListNode(2);
    head.next.next=new ListNode(3);
    head.next.next.next=new ListNode(2);
    head.next.next.next.next=new ListNode(1);

    System.out.println(palindromeList.checkPalindrome(head));
  }
}
```
