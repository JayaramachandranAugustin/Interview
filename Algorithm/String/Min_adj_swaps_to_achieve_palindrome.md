#  Minimum adjacent swaps to convert a string to palindrome

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson we will see about one of the interesting problem, Which is Minimum adjacent swaps to convert a string to palindrome. Palindrome is a sequence of characters which reads same as forward and backward. Example is NOON which reads same from forward and backward.

The problem statement is given the string DAAMM. We need to find minimum number of adjacent swaps to convert this string to palindrome. If we can't convert the given string to palindrome then return -1. Here there may be two variant one is the input contains only lowercase alphabets and another is input contains any character.

So we will how to convert this String

DAAMM - Convert DAAMM to ADAMM, then convert to ADMAM, then convert to ADMMA, then convert to AMDMA. 4 swaps. Here the problem asks about the minimum number of swaps.  

Frist See can we make a string as palindrome. Since we know palindrome reads same from forward and backward, So every characters except one in case of odd number of characters must be in pairs. What that mean! Every character except one need to be completely divisible by 2.

Now we will see how to perform this in code. If the questions states only the lowercase alphabets are considered we can create a Integer array of length 26 to represent the 26 characters in the alphabets and we will traverse through all the characters in the string and For every character we will increment the corresponding integer in the array. Once we traversed the string completely then traverse through the array check if all the integers in the array are divisible by 2 except one. If there is more than one integer which is not completely divisible by 2 then we can't convert this string to palindrome return -1.

We will see this with an example. Lets take a string CBBAAA. Now the traverse all the characters in the string. First is C which is 2nd integer in the array. Here the array starts from the index 0. So, C is at the index 2. So increment index 2 integer with 1. So index 2 integer holds 1. Next is B, Which corresponds to integer at index 1. So increment it by 1. Next is B, Which corresponds to integer at index 1. So increment it by 1. It already holds 1, So the value of the integer at the index 1 is 2. Next is A, Which corresponds to integer at index 0. So increment it by 1. Next is A, Which corresponds to integer at index 0. So increment it by 1. It already holds 1, So the value of the integer at the index 0 is 2.  Next is A, Which corresponds to integer at index 0. So increment it by 1. It already holds 2, So the value of the integer at the index 0 is 3.  Next is A, Which corresponds to integer at index 0. So increment it by 1. It already holds 3, So the value of the integer at the index 0 is 4.

Now loop through all the integers in the array. If there are more than one integer which is not divisible by 2 then this is not palindrome. index 0 is 4 which is divisible by 2. Now move to next integer which is 2 which is also divisible by 2. Next integer is 1 which is okay since we can have one odd character which can be placed in the center of the palindrome. There are no more integers which is non-divisible by 2. So the String CBBAAA is palindrome. Now for your practice check whether CAABBD is palindrome or not. Pause the video and do it yourself.
 There are more than one odd number of characters in the string (C and D), So this is not palindrome.


Now if problem statement says string can contain any character not only the lowercase alphabets we can make use of the hashmap. Here the logic is, for every character in the string insert into the hash map if it is not already present. If it is already present then remove the character from the hashmap. Do this for all the characters in the string. Once  we performed this for all the characters in the string. Check the size of the hashmap if it is greater than 1 then return false. If it is lesser than or equal to 1 then return true.


Now we will perform the same for the string CBBAAAA. Here first character in the string is C, which is not already present in the HashMap. So, Enter this character into the hashmap. Next character in the string is B. Which is not already present in the hashmap so add it to the hashmap. Next character in the string is B, Now B is present in the hashmap so remove the entry B from the hashmap. Next character in the string is A, Which is not already present in the hashmap so add it to the hashmap. Next character in the string is A, Now A is present in the hashmap so remove the entry A from the hashmap. Next character in the string is A, Which is not already present in the hashmap so add it to the hashmap. Next character in the string is A, Now A is present in the hashmap so remove the entry A from the hashmap.

Now the size of the hashmap is 1. So the string CBBAAAA is Palindrome.

The time complexity for checking whether a string is palindrome or not.


Now we will see the java coding for this.

```java
public boolean isPalindrome(String str){
  HashSet<Character> hs=new HashSet<Character>();
  for(char c:str.toCharArray()){
    if(hs.contains(c)){
      hs.remove(c);
    }else{
      hs.add(c);
    }
  }
  return hs.size()<2;
}
```
```java
public boolean isPalindrome(String str){
  int[] charArr=new int[26];
  for(char c:str.toCharArray()){
    charArr[c-'a']++;
  }
  boolean flag=false;
  for(int i: charArr){
    if(i%2!=0){
      if(!flag){
        flag=true;
      }else{
        return false;
      }
    }
  }
  return true;
}
```


Now we know whether we can convert the given string to palindrome or not. Now if we can able to convert the given string to palindrome then we can calculate the minimum number of adjacent swaps required to convert the string to palindrome.


Here we will use the two pointer approach. left pointer pointing at the start of the string and right pointing at the end of the string. This can be better explained with an example so I am taking the example CBBAAAA.

First the left pointer pointing at the zeroth index, which is starting character of the string.

Declare the swaps integer variable to 0. Fix the left pointer to the zeroth index,  make a copy of right pointer and check the right index value is matching with the left index value. Here left index value is C which is not matching with the right index value A. So move the right index one step towards left and check again. Still C is not matching with A. So move the right index one step towards left and check again. Still C is not matching with A. So move the right index one step towards left and check again. Still C is not matching with A. So move the right index one step towards left and check again. Still C is not matching with B. So move the right index one step towards left and check again. Still C is not matching with B. Now the right index is not greater than the left index so break here and check if the left and right index are equal. if both are equal then swap the rightIndex index value with rightIndex+1 index value. So swap C with A and increment the swaps counter with 1. Now the string become BCBAAAA. Don't move the left and right index because we didn't found the match for this character.


 Still the left index is at 0 and right index is at last character in the string, make a copy of the right index. Now compare the last character A with the first character B in the string. Which is not matching. Now move the right pointer one step towards left. So the left pointer points to the value B and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left. So the left pointer points to the value B and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left. So the left pointer points to the value B and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left. So the left pointer points to the value B and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left. So the left pointer points to the value B and the right pointer points to the value B. It is matching and now make adjacent swaps till current right index value swaps to the saved right index. swap the current right index with right index + 1 value. So the String now become BCABAAA and increment the swaps variable value. swap the current right index with right index + 1 value. So the String now become BCAABAA and increment the swaps variable value. swap the current right index with right index + 1 value. So the String now become BCAABAA and increment the swaps variable value. swap the current right index with right index + 1 value. So the String now become BCAAABA and increment the swaps variable value. swap the current right index with right index + 1 value. So the String now become BCAAAAB and increment the swaps variable value.  Now increment the left value and decrement the right index value.

 Now the let index is at 1 and right index is at 5. Make a copy of the right index. So the left pointer points to the value C and the right pointer points to the value A. It is not matching. Now move the right pointer one step towards left. So the left pointer points to the value C and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left. So the left pointer points to the value C and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left. So the left pointer points to the value C and the right pointer points to the value A. Still it is not matching. Now move the right pointer one step towards left.  Now both left and right index are equal then swap the rightIndex index value with rightIndex+1 value. So swap C with A and increment the swaps counter with 1 and don't increment the left and right index. Now the string is BACAAAB.

 Now the left index is at 1 and right index is at 5. Make a copy of the right index. The left pointer points to the value A and the right pointer points to the value A. It is matching. Current right index and copied right index are same so no swaps needed. Increment the left and decrement the rightindex value.

 Now the let index is at 2 and right index is at 4. Make a copy of the right index. So the left pointer points to the value C and the right pointer points to the value A. It is not matching. Now move the right pointer one step towards left. So the left pointer points to the value C and the right pointer points to the value A. It is not matching. Now move the right pointer one step towards left. Now both left and right index are equal then swap the rightIndex  value with rightIndex+1 value. So swap C with A and increment the swaps counter with 1 and don't increment the left and right index. Now the string is BAACAAB.

 Now the left index is at 2 and right index is at 4. Make a copy of the right index. The left pointer points to the value A and the right pointer points to the value A. It is matching. Current right index and copied right index are same so no swaps needed. Increment the left and decrement the rightindex value.  Now the left index is at 3 and right index is at 3. Here the left index is not less than the right index. So we arrived at the result.


The time complexity of this swap is O(n2). So the overall time complexity is O(n2+n) which is n2. If you use the hashmap to check it is palindrome then it is O(k) space complexity where K is the distinctive character present in the string. If the problem deals only with lowercase alphabets you can use the chararray in which the space complexity is O(1).

 ```java
 public int makeSwaps(char[] charArr){
     int leftIndex=0, rightIndex=charArr.length-1;
     int rightIndexCopy=rightIndex, swaps=0;


     while(leftIndex<rightIndex){
       rightIndexCopy=rightIndex;
       while(charArr[leftIndex]!=charArr[rightIndexCopy] && rightIndexCopy > leftIndex){
         rightIndexCopy--;
       }
       if(charArr[leftIndex]==charArr[rightIndexCopy] && rightIndexCopy !=leftIndex){
         while(rightIndexCopy<rightIndex){
           swap(charArr,rightIndexCopy,rightIndexCopy+1);
           swaps++;
           rightIndexCopy++;
         }
         leftIndex++;
         rightIndex--;
       }
       else{
         swap(charArr,rightIndexCopy,rightIndexCopy+1);
         swaps++;
       }
     }
     return swaps;
   }

   //helper method to swap
   public void swap(char[] charArr,int leftIndex,int rightIndex){
     char c=charArr[leftIndex];
     charArr[leftIndex]=charArr[rightIndex];
     charArr[rightIndex]=c;
   }
   //main method
   public int minimumAdjSwapForPalindrome(String str) {
		if(str==null || !isPalindrome(str)) return -1;
		if(str.length()==0) return 0;

		return makeSwaps(str.toCharArray());
	}
 ```
