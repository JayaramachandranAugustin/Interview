#  Find cycle in Linked list

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson, we will see how to check if the linked list contains or not.


 This can be achieved by using two pointers. First point two pointers at the head of the list. we will mark one as fast and one as slow, for each iteration move the fast pointer two steps and slow pointers one step towards right. Continue this till fast is not pointing to null or next reference of fast is not null.
