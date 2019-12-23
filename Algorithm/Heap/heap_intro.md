#  Heap

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).


In this lesson, we will see about heap data structure. Heap is a specialized tree-based data structure which is essentially an almost complete tree that satisfies this condition, If A is a parent of B then A is ordered with respect to B for all nodes A, B in the heap. We will see this definition in detail with the max and min heap.

When we say tree, it is undirected and acyclic. That is, Tree should not have directed edges and it should not contain cycle.

what is complete and full binary tree.

When ever we are creating a heap, we need add elements level by level starting from the root node and from left to right in each level. If the nodes are filled in this way, then it is said to be complete.
A binary tree is said to be full if the all the levels are completely filled.

Now we will see some binary tree and determine whether full or complete or incomplete.
This tree is complete because in all the levels the nodes are filled from left to right. This is not full because the last level is not completely filled, it still has two vacant nodes.

This tree is complete because in all the levels the nodes are filled from left to right and it is full because all the levels are completely filled, So this tree is complete and full.

This tree is incomplete because in level 3 the nodes not are filled from left to ri ght so it is incomplete. Heap need to be a complete binary tree.

What is important application of heap?

Priority queue is the abstract data type. In priority queue higher priority elements are placed at the top of the queue. Priority queue can be effectively implemented using the heap. To know more about priority queue refer my video tutorial on priority queue. The link of which I gave in the description

Now we will see how to represent the data in the heap.
The most important part of heap is we will use the array data structure to represent the heap. Now you may be curious how can we represent a binary tree using the array data structure. This is done by using the index positions
Here we will use the array whose index starts from position 0.
So, The Root node of the heap is at index 0.

For the node at index i. The immediate parent is at index (i-1)/2. Here this is integer division and we need to truncate the decimal value.
For example for the immediate parent of index 2 is 2-1 which is 1 and 1 divide by 2 is 0.5. We need to truncate the decimal value so the immediate parent for the element at index 2 is index 0.
Likewise the immediate parent of element at index 3 is 3-1 which is 2 and 2 divide by 2 which is 1. So the immediate parent for the element at the index 3 is index 1

The left child for the element at the index i is at index 2*i+1. So for the element at the index 4 the left child element is at the index 2*4 which is 8 and 8 +1. So the left child for the element at the index 4 is at index 9.

The right child for the element at the index i is at the index 2*i+2. So for the element at the index 1 the right child element is at the index 2*1 which is 2 and 2 + 2. So the right child for the element at the index 1 is at index 4.

The height of the complete binary tree is log(n)

By the definition, There are two kinds of heap they min heap and max heap.
First we will see about min-heap.
In min heap, The all the parent nodes in the tree must be lesser than its child node. So we will check whether this tree is min-heap.

First we need to check whether it is tree, There should not be any cycle, here there are no cycles so it is tree. In min heap all the parent node's value must be lesser than its child node. Here we will start from the last non leaf node, which is 5, here its child nodes are 12 and 18 which are greater than its parent 5, So this node satisfies this condition. next move the next non-leaf node from the last which is 4,  here its child nodes are 9 and 10 which are greater than its parent 4, So this node satisfies this condition. Next is the root node the child node of the root node are 4 and 5 which are greater then the root node 2, So the root node satisfies this condition. So as a whole this binary tree is min heap.

Now we will see about Max-heap. We have seen what is min-heap
In max heap, The all the parent nodes in the tree must be greater than its child node. So we will check whether this tree is max-heap.
First we need to check whether it is tree, There should not be any cycle, here there are no cycles so it is tree. In max heap all the parent node's value must be greater than its child node. Here we will start from the last non leaf node, which is 6, here its child nodes are 4 and 1 which are lesser than its parent 6, So this node satisfies this condition. next move the next non-leaf node from the last which is 5,  here its child nodes are 2 and 3 which are lesser than its parent 5, So this node satisfies this condition. Next is the root node the child node of the root node are 5 and 6 which are lesser then the root node 8, So the root node satisfies this condition. So as a whole this binary tree is max heap.

Adding a element to the minheap. We know, in min-heap all the parent node must have values lesser than its child nodes.
Now we will see how to add an element to the min heap. We will check whether it is min heap. The root node 5 is less than its child node  8 and 9. Then the left node 8 is less than its child nodes 12 and 15. The right node 9 is less than its child nodes 10 and 11.So, This is min heap. In this example we will add 3 to this min heap. We know a heap must be complete, since the level 3 is already filled we need to start filling the level 4 starting from the left side. Now we need to perform sift up. We need to check the parent of 3 which is 12. 12 is greater than 3 so swap 12 with 3. Now check the parent of 3 which is 8. 8 is greater than 3 so swap 8 with 3. Now the root node is 3.Now check whether this tree for min heap. Yes, it is min heap.

So the procedure to all an element in the heap is add the element at the last and check for its parent if it is lesser than its parent then swap continue this till it is greater than the parent node or till the root node. This process is called is sift up. The time complexity of adding an element in the heap is depends on the height of the tree. The height of the tree is log n. So Time complexity of adding an element in the heap is log n.


Removing the element from the heap. We can remove only the top of the heap. which is root node. In case of min heap the root node is always lesser than equal to all other nodes in the heap. So keeping this in mind remove the top of the heap which is 3. Now we need to replace this empty root node with the last node in the heap. Here the last element is 12. Now we need to perform the sift to make this tree as minheap. Sift down starts from the root node. Need to compare the child nodes, since it is min heap need to find the smallest among the both and compare it with the root node if it is lesser than the root node then replace that child node with the parent node. Here the root node is 12. Compare its child nodes 5 and 9. 5 is lesser than the both compare 5 with 12. 12 is greater than 5 so swap 12 and 5. Now the check the node 12's child nodes. 12's child are 8 and 15, out of this 8 is smallest. So compare this 8 with 12, 12 is greater than 8 so swap the parent with left child. Now the 12 is the leaf node. This tree is min heap now. The time complexity of removing an element in the heap is depends on the height of the tree. The height of the tree is log n. So Time complexity of removing an element in the heap is log n.


Adding a element to the maxheap. We know, in max-heap all the parent node must have values greater than its child nodes.
Now we will see how to add an element to the max heap. We will check whether it is max heap. The root node 12 is less than its child node  8 and 9. Then the left node 8 is greater than its child nodes 7 and 5. The right node 9 is greater than its child nodes 4 and 6. So, This is max heap. In this example we will add 15 to this max heap. We know a heap must be complete, since the level 3 is already filled we need to start filling the level 4 starting from the left side. Now we need to perform sift up. We need to check the parent of 15 which is 7. 15 is greater than 7 so swap 15 with 7. Now check the parent of 15 which is 8. 8 is lesser than 15, so swap 8 with 15. Now the root node is 15. Now check whether this tree for max heap. Yes, it is min heap.

So the procedure to all an element in the heap is add the element at the last and check for its parent if it is lesser than its parent then swap continue this till it is lesser than the parent node or till the root node. This process is called is sift up.


Removing the element from the max heap. We can remove only the top of the heap. which is root node. In case of max heap the root node is always greater than or equal to all other nodes in the heap. So keeping this in mind remove the top of the heap which is 15. Now we need to replace this empty root node with the last node in the heap. Here the last element is 7. Now we need to perform the sift down to make this tree as maxheap. Sift down starts from the root node. Need to compare the child nodes, since it is max heap need to find the largest among the both and compare it with the root node if it is greater than the root node then replace that child node with the parent node. Here the root node is 7. Compare its child nodes 12 and 9. 12 is greater than 9, compare 12 with 7. 12 is greater than 7 so swap 12 and 7. Now the check the node 7 child nodes. 7 child are 8 and 5, out of this 8 is largest. So compare this 8 with 7, 8 is greater than 7 so swap the parent with left child. Now the 7 is the leaf node. This tree is max heap.



```JAVA
import java.util.ArrayList;
import java.util.List;

public class Heap{
    List<Integer> heap;

    Heap(){
      heap=new ArrayList<>();
    }

    public int getLeftIndex(int index){
      int leftIndex=2*index+1;
      if(leftIndex<heap.size()){
          return leftIndex;
      }
      return -1;
    }
    public int getRightIndex(int index){
      int rightIndex=2*index+2;
      if(rightIndex<heap.size()){
        return rightIndex;
      }
      return -1;
    }

    public int getParentIndex(int index){
      int parentIndex=(index-1)/2;
      if(index!=0){
        return parentIndex;
      }
      return -1;
    }


    public void swap(int index1,int index2){
        int temp=heap.get(index2);
        heap.set(index2,heap.get(index1));
        heap.set(index1,temp);
    }

    public void maxSiftDown(int index){
      int leftIndex=getLeftIndex(index);
      int rightIndex=getRightIndex(index);

      int largerIndex=-1;
      if(leftIndex != -1 && rightIndex !=-1){
        largerIndex=heap.get(leftIndex)<heap.get(rightIndex)?rightIndex:leftIndex;
      }
      else if(leftIndex !=-1){
        largerIndex=leftIndex;
      }
      else if(rightIndex !=-1){
        largerIndex=rightIndex;
      }
      else{
        return;
      }

      if(heap.get(largerIndex)>heap.get(index)){
        swap(index,largerIndex);
        maxSiftDown(largerIndex);
      }
    }

    public void maxSiftUp(int index){
      int parentIndex=getParentIndex(index);
      if(parentIndex==-1) return;
      else if (heap.get(parentIndex)<heap.get(index)){
        swap(parentIndex,index);
        maxSiftUp(parentIndex);
      }
    }

    public void minSiftDown(int index){
      int leftIndex=getLeftIndex(index);
      int rightIndex=getRightIndex(index);

      int smallerIndex=-1;
      if(leftIndex != -1 && rightIndex !=-1){
        smallerIndex=heap.get(leftIndex)>heap.get(rightIndex)?rightIndex:leftIndex;
      }
      else if(leftIndex !=-1){
        smallerIndex=leftIndex;
      }
      else if(rightIndex !=-1){
        smallerIndex=rightIndex;
      }
      else{
        return;
      }

      if(heap.get(smallerIndex)<heap.get(index)){
        swap(index,smallerIndex);
        minSiftDown(smallerIndex);
      }
    }

    public void minSiftUp(int index){
      int parentIndex=getParentIndex(index);
      if(parentIndex==-1) return;
      else if (heap.get(parentIndex)>heap.get(index)){
        swap(parentIndex,index);
        minSiftUp(parentIndex);
      }
    }
    public int remove() throws Exception{
      if(heap.isEmpty()) throw new Exception("List is empty");
      int result=heap.get(0);
      swap(0,heap.size()-1);
      heap.remove(heap.size()-1);
      minSiftDown(0);
      return result;
    }
    public void add(int value){
      heap.add(value);
      minSiftUp(heap.size()-1);
    }
    public static void main(String args[]) throws Exception{
      Heap hp=new Heap();
      hp.add(14);
      hp.add(10);
      System.out.println(hp.remove());
      System.out.println(hp.remove());
    }
}
```

Now you know how to insert an element and remove an element from both maxheap and min heap. Now learn the heap sort. The idea is first to convert the given set of numbers to max-heap. Then remove elements one by one from top and add it at the end of the array. We will see this with an example and graphical representation.

We will take an unsorted array as an input. We will do in place swap to make this as max-heap. 0th index is root element. We will start from the index position 1. Now enter the index 1 into the max heap. The parent of index 1 is index 0. The index 0 value is already greater than index 1 value. Move to the next index 2. Here index 2 value is greater than its parent index 0 so swap both the values. So the index 2 value 10 is swapped with the index 0 value 9. Now move to the next index 3 and check its value with its parent. Parent index can be found by  (i-1)/2. So the parent index of 3 is index 1. The current index 3 value is 14 which is less than its parent index 1 value 4 so swap the index value 1 and 3.  Now check the parent index of index 1. Here the parent index value 10 is less than the current index value 14, So swap 10 and 14. Now move to the next index which is 4. Current index value 5 is already less than its parent value 10. So move to the next index value which is 8 and it is already less than its parent 9. Move to the last index value which is 9 it is not greater than its parent. So, We have made this array to max-heap.

The time complexity for this heapify is, We know the sift up time complexity is based on the tree height. The tree height of binary tree is O(logn) and we are performing this for all the elements in the array so the time complexity of this heapify is O(nlogn).

Now we need to remove the value from the top of the heap and need to store it empty place at the end of the array. Now we will see how to do this in graphical representation. Remove the top of the heap which is 14. and perform siftdown. Now there will be one vacant position in the end of the array. Store the removed value here. So 14 placed in the end of the array and mark the array end index as n-1 where n is the number of elements in the array.  
Remove the top of the heap which is 10 and perform siftdown. Now there will be one vacant position in the end of the array. Store the removed value here. So 10 and 14 placed in the end of the array and mark the array end index as n-2.
Remove the top of the heap which is 9 and perform siftdown. Now there will be one vacant position in the end of the array. Store the removed value here. So 9, 10 and 14 placed in the end of the array and mark the array end index as n-3.
Remove the top of the heap which is 9 and perform siftdown. Now there will be one vacant position in the end of the array. Store the removed value here. So 9, 9, 10 and 14 placed in the end of the array and mark the array end index as n-4.
Remove the top of the heap which is 8 and perform siftdown. Now there will be one vacant position in the end of the array. Store the removed value here. So 8, 9, 9, 10 and 14 placed in the end of the array and mark the array end index as n-5.
Remove the top of the heap which is 5 and perform siftdown. Now there will be one vacant position in the end of the array. Store the removed value here. So 5, 8, 9, 9, 10 and 14 placed in the end of the array and mark the array end index as n-6.
Remove the top of the heap which is 4 and perform siftdown. Now we have sorted the array.

The time complexity for this sorting is, We know the sift down time complexity is based on the tree height. The tree height of binary tree is O(logn) and we are performing this for all the elements in the array so the time complexity of this sorting is O(nlogn).

```JAVA
public class Heap{
    int arr[];

    Heap(int... inputArr){
      arr=inputArr;
    }

    public int getLeftIndex(int index, int endIndex){
      int leftIndex=2*index+1;
      if(leftIndex<endIndex){
          return leftIndex;
      }
      return -1;
    }
    public int getRightIndex(int index, int endIndex){
      int rightIndex=2*index+2;
      if( rightIndex<endIndex){
        return rightIndex;
      }
      return -1;
    }

    public int getParentIndex(int index){
      int parentIndex=(index-1)/2;
      if(index!=0){
        return parentIndex;
      }
      return -1;
    }

    public void heapify(){
      for(int i=1;i<arr.length;i++){
        maxSiftUp(i);
      }
    }

    public void swap(int index1,int index2){
        int temp=arr[index2];
        arr[index2]=arr[index1];
        arr[index1]=temp;
    }

    public void maxSiftDown(int index, int endIndex){
      int leftIndex=getLeftIndex(index,endIndex);
      int rightIndex=getRightIndex(index,endIndex);

      int largerIndex=-1;
      if(leftIndex != -1 && rightIndex !=-1){
        largerIndex=arr[leftIndex]<arr[rightIndex]?rightIndex:leftIndex;
      }
      else if(leftIndex !=-1){
        largerIndex=leftIndex;
      }
      else if(rightIndex !=-1){
        largerIndex=rightIndex;
      }
      else{
        return;
      }

      if(arr[largerIndex]>arr[index]){
        swap(index,largerIndex);
        maxSiftDown(largerIndex,endIndex);
      }
    }

    public void maxSiftUp(int index){
      int parentIndex=getParentIndex(index);
      if(parentIndex==-1) return;
      else if (arr[parentIndex]<arr[index]){
        swap(parentIndex,index);
        maxSiftUp(parentIndex);
      }
    }

    public void heapSort(){
      heapify();
      for(int i=arr.length-1;i>=0;i--){
        swap(0,i);
        maxSiftDown(0,i);
      }
    }
    public static void main(String args[]){
      int a[]={9,4,10,14,5,8,8};
      Heap heap=new Heap(a);
      heap.heapSort();
      for(int i:heap.arr) {
    	  System.out.print(i+" ");
      }
    }
}
```

__Priority queue__
