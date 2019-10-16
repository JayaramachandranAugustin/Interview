# Two Sum

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

Leet code [`Link`](https://leetcode.com/problems/two-sum/).



In this lesson we will see, how to solve this two sum problem. The problem statement is given an array of integers and a target value, return the indices of two numbers which sums up to this value.

The brute force solution to this problem is to use two for loops. With first loop starts from 0 to n-1 where n is length of the array and the inner loop starts from i+1 to n-1. Now add both these indexes value, if it is equal to the target value then return the i and j index value.

```java
public static int[] twoSum(int[] nums, int target) {
        int[] res={0,0};
        if(nums==null || nums.length==0) return res;

        for(int i=0;i<nums.length;i++){
          for(int j=i+1;j<nums.length;j++){
              if(nums[i]+nums[j]==target){
                res[0]=i;
                res[1]=j;
                return res;
              }
          }
        }
        return res;
}
```

The time complexity of this algorithm is O(n^2) and the space complexity is O(1).


We will try to improve the solution time complexity. The Key thing to note here are

1. The problem will have exactly one solution
2. The same index must not be used twice

We will use the hash map to first load all the values. Here the value is key and the index is value.

Once we loaded all the value. Now we iterate from the index value 0 to n-1 again. Now we will check whether the target minus the value present at that index is present in the hashmap. If present then check whether the current index is not equal to the value present in the hashmap.

If these values are not equal then return the current index value and value present in the hashmap


```java
 public int[] twoSum(int[] nums, int target){
  int[] res={0,0};
  if(nums==null || nums.length==0) return res;
  Map<Integer,Integer> dict=new HashMap<Integer,Integer>();

  //Here we are adding the elements to the hashmap
  //Here we should not check for the duplicates because,
  //if we have a value like [3,3] and target as 6 if we exclude the duplicates
  //second time the index wont be overriden
  for(int i=0;i<nums.length;i++){
    dict.put(nums[i],i);
  }
  for(int i=0;i<nums.length;i++){
    if(dict.containsKey(target-nums[i])){
      //if the current is equal to the value present in the hashmap skip
      //This is because if we have the array like [3,4,2] and the target as 6
      //target-3 gives us 3 which is the value present in the same index
      if(i==dict.get(target-nums[i])) continue;
        res[0]=i;
        res[1]=dict.get(target-nums[i]);
        return res;
    }
  }
  return res;
}
```
The time complexity of this solution is O(n) and the space complexity is O(1)
Boundary test cases
```
Input
{4,4} target=8   

Output
[0,1]
```

```
Input
{-1,3,10} target=9   

Output
[0,2]
```

```
Input
{3,4,2} target=6   

Output
[1,2]
```
