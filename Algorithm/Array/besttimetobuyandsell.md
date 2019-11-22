# Best time to buy and sell

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

Leet code [Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/).

In this lesson we will see about best time to buy and sell. Given an array of integers which depicts the cost of the share, each element i depicts the cost on the day i.

We were permitted to buy and sell only once. We need to return the maximum profit that be can be achieved

For example given the input array
{10,2,3,6,8,9,1} , Here the maximum profit can be achieved by buying it for the cost 2 and selling it for the profit 9, to the maximum profit that can be achieved in this share for the n days is 7

The brute force solution for this problem is

```java
public int maxProfit(int[] nums){
  if(nums==null ||nums.length==0) return 0;
  int max=0;
  //create two for loops
  for(int i=0;i<nums.length;i++){
    for(int j=i+1;j<nums.length;j++){
        max=Math.max(nums[j]-nums[i],max);
    }
  }
  return max;
}
```
The time complexity of this problem is O(n^2) and the space complexity is O(1)

We can able to improve the time complexity of this algorithm by analyzing the input data, The maximum profit can be achieved only if buy a share for less price and sell it for high price. So the max profit is maximum difference between high value and low value.

Here one thing to note is high value must come after the low value.

We can get a clear picture by looking at this bar graph

The pseudocode for this solution is

```python
  maxProfit=0, minimumValue= nums[i]
  for value in nums:
    if minimumValue>value:
      minimumValue=value
    else
      maxprofit = max(maxProfit,value-minimumValue)
  return maxProfit
```


Implementing the above pseudocode in java

```java
public int maxProfit(int[] nums){
  if(nums==null ||nums.length==0) return 0;
  int max=0,current=0,min=nums[0];
  for(int i=1;i<nums.length;i++){
    if(nums[i]<min){
      min=nums[i];
    }else{
      current=nums[i]-min;
      max=Math.max(current,max);
    }
  }
  return max;
}
```

The time complexity of this problem is O(n) and the space complexity is O(1)

Boundary test cases
```
Input
{1,15,2,17,10,11}    

Output
15
```

```
Input
{10,2,3,6,8,9,1}  

Output
7
```
