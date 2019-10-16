# Maximum Subarray

In this lesson we will learn about how to solve the maximum subarray problem using kadane algorithm.
We will look into the problem statement now.
Given an array of size n we need to find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.
Now, we take an array which comprises both negative and positive integers.
First, given a problem try to find a brute force solution then try to optimize it. In this process try to think out loud.
The brute force solution is, first to start with the index position 0 and try to add it with all the preceding indexes value one by one and keep track of maximum sum. Next move the index position to 1 and add it with all the preceding indexes value and carry out till the index n.

Here the space complexity is constant value, but the time complexity is O(n2 ).
Here we will use the kadane algorithm.
The kadane algorithm helps us to compute the maximum sum at each index position. The core of kadane algorithm is, the maximum sum at any given index position is either the value at that index or the sum of value at current index position and the maximum sum at the previous index position.
Let’s see the pseudo code of kadane algorithm,
Step 1: Assign the zeroth index value to the current index maximum sum and overall maximum sum.
Step 2: Start from the index position one and iterate till n and find the max value between the current index position value and sum of current index position value and last index maximum sum.
Step 3: if the current index maximum value is greater than overall maximum value, then replace the overall maximum value with the current index maximum value.

Now let’s dive deep into this algorithm with an example. I believe this will make the things.

Assign the zeroth index value to the current index max value and overall maximum sum. This is very obvious because there is no element present before this index so the maximum sum at this index position is the value present in this index itself.
Next move to the next index position, the value present in this index position is 2, the max value at this index is either this value itself or this value plus the last index max sum. So max of 2 and 1+2 is 1+2 which is 3. So, the maximum sum at this index position is 3. Now, we need to find the max value between the current index max sum and overall max value. Here the current index sum is greater than overall max value so we need to replace the overall max value with the current index max value.

Next index position 2, the max of -1 and 3-1 is 3-1 which is 2. So, the maximum sum at this index position is 2. Which is less than the overall max value so we no need to replace the overall max value.

Next index position is 3, the max of -2 and 2-2 is 2-2 which is 0. So, the maximum sum at this index position is 0. Which is less than the overall max value so we no need to replace the overall max value.

Next index position is 4, the max of 2 and 2+0, Here both are same. So, the maximum sum at this index position is 2. Which is less than the overall max value so we no need to replace the overall max value.

Next index position is 5, the max of 1 and 1+2 is 1+2 which is 3. So, the maximum sum at this index position is 3. Which is equal to the overall max value so we no need to replace the overall max value.

Next index position is 6, the max of -2 and 3-2 is 3-2 which is 1. So, the maximum sum at this index position is 1. Which is less than the overall max value so we no need to replace the overall max value.

Next index position is 7, the max of 1 and 1+1 is 1+1 which is 2. So, the maximum sum at this index position is 2. Which is less than the overall max value so we no need to replace the overall max value.
Next index position is 8, the max of 4 and 4+2 is 4+2 which is 6. So, the maximum sum at this index position is 6. Here the current index sum is greater than overall max value so we need to replace the overall max value with the current index max value.

Next index position is 9, the max of -5 and 6-5 is 6-5 which is 1. So, the maximum sum at this index position is 1. Which is less than the overall max value so we no need to replace the overall max value.


Next index position is 10, the max of 5 and 4+1 is 4+1 which is 5. So, the maximum sum at this index position is 5. Which is less than the overall max value so we no need to replace the overall max value.

Here the overall maximum value is 6. This is the answer

Now we will see this logic in a java program

```java
public int maximumSubarray(int a[]){
	int currentIndexMaxSum=a[0];
	int overallMaxSum=a[0];
	for(int i=1;i<n;i++){
        currentIndexMaxSum=Math.max(a[i],a[i]+currentIndexMaxSum);
        overallMaxSum=Math.max(currentIndexMaxSum,overallMaxSum);
  }
  return overallMaxSum;
}
```

Time complexity O(n) and space complexity is O(1)
