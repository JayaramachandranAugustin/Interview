# Find Median from Data Stream

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).


In this lesson we will see how to find the median from data stream. The problem statement is Median is the middle value in an ordered integer list. If the size of the list is even, there is no middle value. So the median is the mean of the two middle value.

For example,
[2,3,4], the median is 3

[2,3], the median is (2 + 3) / 2 = 2.5

Design a data structure that supports the following two operations:

void addNum(int num) - Add a integer number from the data stream to the data structure.
double findMedian() - Return the median of all elements so far. This is a leetcode problem the link of which I gave in the description. This problem can be effectively solved using heap data structure. I strongly recommend you to understand or refresh heap data structure before proceeding with this question. I have posted a video on heap data structure the link of which, I gave in the description.

Before understanding the two heap data structure. we will see brute force solution to solve this problem.

Create a list and whenever we get a need new element to be added to the data stream. Add it to the list. When you need to find the median, sort the list and return median value. The time complexity of this solution is O(nlogn) for each find median operation, because we need to sort the list before finding the median.
The space complexity is O(n).

Now we will see about the two heap solution. The base idea is to divide the list into two part. So first list holds the values less than the median and the second list holds all the larger values than the median. We can implement this idea with max and min heap. In max heap all the parent nodes hold the value greater than its child nodes.  In the min heap all the parent nodes the value lesser than its child node.

We will create two heap one is max heap, Which holds the first part of the list. That is, All the small values than the median and another one is min heap, Which holds the second part of the list. That is, All the large values than the median.

The pseudocode for this algorithm is
First add the value to the max heap Then remove the top of the max heap and add it to the min heap. Now we need to perform the balancing. If the maxheap size is less than the min heap then remove the top of the min heap and add it to the max heap.

The median is found by checking the size of the maxheap. If the maxheap size is greater than the min heap size, Then the total number of elements is odd, then peek the top of the maxheap and this is the median.  If the maxheap size is equal to the min heap size, Then the total number of elements is even, then peek the top of the maxheap and peak the top of the minheap add and divide it by 2, this is the median.  

We will see this with an example. Add the value 8. First add the value 8 to the maxheap. Then remove the top of the maxheap which is 8 and add it to the minheap. Now we need to perform the balancing if the size of the max heap is less than then the min heap. Then remove the top of the min heap and add it to the max heap.

Now max heap holds the value 8 and the size of the max heap is 1 and size of the min heap is 0.

Now enter the value 10. Add this to the max heap 10 is added to child of 8. Check the parent of 10 which is 8. The parent is lesser than the root so swap 8 with 10. Now 10 is the root node. To know more about how to add value to max heap refer to my video tutorial on heap. The link of which I gave in the description. Now remove the top of the max heap which is 10 and add it to the min heap. Now we need to perform the balancing. Check the size of the max heap. it is equal to the size of the min heap. So we don't need to do anything.

Now to calculate the median, Check the size of max and min heap. both size are 1. so peek the top of max heap and top of min heap. Add those two value and divide it by 2. which is the median. 8+10/2 which is 9

Now enter the value 9. Add this to the max heap, 9 is added to child of 8. Check the parent of 9 which is 8. The parent is lesser than the root so swap 8 with 9. Now 9 is the root node. Now remove the top of the max heap which is 9 and add it to the min heap. In the min heap check parent of node 9 which is 10 swap 10 with 9 in the minheap. Now we need to perform the balancing. Check the size of the max heap. it is less than the minheap so remove the top of minheap which is 9 and add it to the maxheap.

Now to calculate the median, Check the size of max and min heap. maxheap size is greater than minheap size, so peek the top of max heap which is 9 this is the median.


Now enter the value 7. Add this to the max heap, 7 is added to child of 9. Check the parent of 7 which is 9. The parent is already greater than the root node. Now 9 is the root node. Now remove the top of the max heap which is 9 and add it to the min heap. In the min heap check the parent of node 9 which is 10 swap 10 with 9 in the minheap. In the max heap fill the root node with the last node in the heap which is 7 and check child of 7 which is 8 and it is less than root node. So swap 7 and 8. Now we need to perform the balancing. Check the size of the max heap. it is equal to the size of the min heap. So we don't need to do anything.

Now to calculate the median, Check the size of max and min heap. both size are 2. so peek the top of max heap and top of min heap. Add those two value and divide it by 2. which is the median. 8+9/2 which is 8.5.


Now enter the value 12. Add this to the max heap, 12 is added to child of 8. Check the parent of 12 which is 8. The parent is lesser than the root so swap 12 with 8. Now 12 is the root node. Now remove the top of the max heap which is 12 and add it to the min heap. In the min heap check parent of node 12 which is 9 which is already less than 12. Now we need to perform the balancing. Check the size of the max heap. it is less than the minheap so remove the top of minheap which is 9 and add it to the maxheap. The parent of 9 is 8, it is less than root node so swap 8 with 9.

Now to calculate the median, Check the size of max and min heap. maxheap size is greater than minheap size, so peek the top of max heap which is 9 this is the median.
Time complexity of adding a number is O(log n) and finding the median is O(1)

```JAVA
class MedianFinder {

    PriorityQueue<Integer> maxQ;
    PriorityQueue<Integer> minQ;

    public MedianFinder() {
        maxQ=new PriorityQueue<>((a,b) -> b-a);
        minQ=new PriorityQueue<>();
    }

    public void addNum(int num) {
        maxQ.offer(num);
        minQ.offer(maxQ.poll());
        if(maxQ.size()<minQ.size()) maxQ.offer(minQ.poll());
    }

    public double findMedian() {
        if(maxQ.size()==0) return 0;
        return maxQ.size()>minQ.size()?maxQ.peek():(double)(maxQ.peek()+minQ.peek())/2;

    }
}
```
