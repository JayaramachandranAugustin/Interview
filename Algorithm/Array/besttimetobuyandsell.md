# Best time to buy and sell

Leet code [Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/).



```java
public int maxProfit(int[] nums){
  if(nums==null ||nums.length==0) return 0;
  int max=0,current=0,min=nums[0];
  for(int i=0;i<nums.length;i++){
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
