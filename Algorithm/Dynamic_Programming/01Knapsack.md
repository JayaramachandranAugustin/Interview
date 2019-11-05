# 01 KnapSack problem

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson we will see about 01 knap sack problem one of the classical problem which can be solved using dynamic programming.

The problem is we are given with a set of weights and a set of corresponding profits and the bag with a maximum capacity. Here our aim is to get the maximum profit by picking up the items which combines to the weight less than or equal to the maximum capacity.

We will see this with a example.
Here we are given with the weights as 4, 3, 2, 4 and their profits are 6, 4, 5, 6. Maximum capacity of the bag is 7.

Now we need to pick the items which maximizes the profit and its weights also sums up less than or equal to the capacity.

Here we can pick the items with weight such as 4 and 3 which sums the profit to 10 or the items with weight 4 and 2 which sums up the profit and 11 and it is less than the capacity. If we pick the weights 4 and 4 it will exceed our maximum capacity. So the maximum profit we can achieve with these items with the capacity 7 are 11.

First we will see about the recursive solution then we will memorize the interim results of smaller sub problems and then solve it using dynamic programming.

First we will start with the last element in the list which has the index value 3. We can do two things either we can include this element as part of our solution or to exclude so it divides into two steps one including this item and excluding the items in index 3. Now in included index 3 value we can either add index 2 or exclude index 2 value, same for excluded index 3. Here we can continue this recursive loop till we reach the index 0.

At each step we will check the capacity if the capacity is exceeded then we will discard that step and take a note of profit at each step and get the maximum profit at the end.

The time complexity is very obvious if we look at this graphical representation it is 2 to the power of n.

We will see a pseudo code for this recursive solution

```python
recurse(index,capacity)
#base condition if the index is -1 or if the capacity is 0
if index==-1 or capacity = 0;
  return 0;
if wieght[index]<capacity
  #skip this item because this item weight is greater than current capacity
  recurse(index-1,capacity);
else
  return max(recurse(index-1,capacity),
             profit[i]+recurse(index-1,capacity-weight[i]));
```

Now we will see how this pseudo code works in detail.

Recursive solution
```java

public int knapsack(int[] weights,int[] values,int n,int c) {
  if(n==-1 || c==0) {
    return 0;
  }
  if(weights[n]>c) {
    knapsack(weights,values,n-1,c);
  }else {
    int tmp1=knapsack(weights,values,n-1,c);
    int tmp2=values[n]+knapsack(weights,values,n-1,(c-weights[n]));
    return Math.max(tmp1, tmp2);
  }
  return 0;
}
```

Now we will try to apply the dynamic programming by storing the interim results in array so that we will avoid computation for the already computed results.

```java

public int knapsackdp(int[]weights, int[] profits,int[][] mem,int c,int n) {
  int result=0;
  //Here we will check if there is value present for the given number and count in the array if present then return it
  if((n>-1 && c>-1) && mem[n][c]!=Integer.MIN_VALUE) {
    return mem[n][c];
  }
  if(n==-1 || c==0) {
    result = 0;
  }
  else {
    if(weights[n]>c) {
      knapsackdp(weights, profits, mem, c, n-1);
    }else {
      int temp1=knapsackdp(weights, profits, mem, c, n-1);
      int temp2=profits[n]+knapsackdp(weights, profits, mem, c-weights[n], n-1);
      mem[n][c]=Math.max(temp1, temp2);
      //Store the data found for the number and capacity in the array
      result=mem[n][c];
    }
  }
  return result;
}
```
Now we will see another approach using dynamic programming.

We need to create a 2 dimensional array with capacity, starting from 0 to the given capacity and the given items

If the current weight is lesser than the current item weight than find the max of value present in the current item current capacity plus previous item , (current weight -item weight), previous

```java
public int knapsack(int[] weights, int[] profits, int capacity){
    int result[][]=new int[weights.length+1][capacity+1];
  for(int i=0;i<=weights.length;i++){
    for(int j=0;j<=capacity;j++){
      if(i==0||j==0) continue;
      if(j>=weights[i-1]){
        result[i][j]=Math.max(result[i-1][j],(profits[i-1]+(result[i-1][j-weights[i-1]])));
      }else{
        result[i][j]=result[i-1][j];
      }
    }
  }
    return result[weights.length][capacity];
}
```
