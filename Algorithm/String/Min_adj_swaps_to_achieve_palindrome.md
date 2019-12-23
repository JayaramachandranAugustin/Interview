#  Minimum adjacent swaps to convert a string to palindrome

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).



Lets See can we make this as palindrome. Since we know palindrome reads same from forward and backward, So every characters except one in case of odd number of characters must be in pairs. What that mean! Every character except one need to be completely divisible by 2.

Now we will see how to perform this in code. If the questions states only the lowercase alphabets are considered we can create a Integer array of length 26 to represent the 26 characters in the alphabets and we will traverse through all the characters in the string and For every character we will increment the corresponding integer in the array. Once we traversed the string completely then traverse through the array check if all the integers in the array are divisible by 2 except one. If there is more than one integer which is not completely divisible by 2 then we can't convert this string to palindrome return -1.

We will see this with example. Lets take a string CBBAAA. Now the traverse all the characters in the string. First is C which is 2nd integer in the array. Here the array starts from the index 0. So, C is at the index 2. So increment index 2 integer with 1. So index 2 integer holds 1. Next is B, Which corresponds to integer at index 1. So increment it by 1. Next is B, Which corresponds to integer at index 1. So increment it by 1. It already holds 1, So the value of the integer at the index 1 is 2. Next is A, Which corresponds to integer at index 0. So increment it by 1. Next is A, Which corresponds to integer at index 0. So increment it by 1. It already holds 1, So the value of the integer at the index 0 is 2.  Next is A, Which corresponds to integer at index 0. So increment it by 1. It already holds 2, So the value of the integer at the index 0 is 3.  Next is A, Which corresponds to integer at index 0. So increment it by 1. It already holds 3, So the value of the integer at the index 0 is 4.

Now loop through all the integers in the array. If there are more than one integer which is not divisible by 2 then this is not palindrome. index 0 is 4 which is divisible by 2. Now move to next integer which is 2 which is also divisible by 2. Next integer is 1 which is okay since we can have one odd character which can be placed in the center of the palindrome. There are no more integers which is non-divisible by 2. So the String CBBAAA is palindrome. Now for your practice check whether CAABBD is palindrome or not. Pause the video and do it yourself.
 There are more than one odd number of characters in the string (C and D), So this is not palindrome.


Now if problem statement says string can contain any character not only the lowercase alphabets we can make use of the hashmap. Here the logic is, for every character in the string insert into the hash map if it is not already present. If it is already present then remove the character from the hashmap. Do this for all the characters in the string. Once  we performed this for all the characters in the string. Check the size of the hashmap if it is greater than 1 then return false. If it is lesser than or equal to 1 then return true.


Now we will perform the same for the string CBBAAAA. Here first character in the string is C, which is not already present in the HashMap. So, Enter this character into the hashmap. Next character in the string is B. Which is not already present in the hashmap so add it to the hashmap. Next character in the string is B, Now B is present in the hashmap so remove the entry B from the hashmap. Next character in the string is A, Which is not already present in the hashmap so add it to the hashmap. Next character in the string is A, Now A is present in the hashmap so remove the entry A from the hashmap. Next character in the string is A, Which is not already present in the hashmap so add it to the hashmap. Next character in the string is A, Now A is present in the hashmap so remove the entry A from the hashmap.

Now the size of the hashmap is 1. So the string CBBAAAA is Palindrome.


Now we will see the java coding for this.




Now we know whether we can convert the given string to palindrome or not. Now if we can able to convert the given string to palindrome then we can calculate the minimum number of adjacent swaps required to convert the string to palindrome.


Here we will use the two pointer approach. left pointer pointing at the start of the string and right pointing at the end of the string. This can be better explained with an example so I am taking the example CBBAAAA.

First the left pointer pointing at the zeroth index, which is starting character of the string.

Fix the left pointer to the zeroth index and check the right index value is matching with the left index value. Here left index value is C which is not matching with the right index value A. So move the right index one step towards left and check again. Still C is not matching with A. So move the right index one step towards left and check again. Still C is not matching with A. So move the right index one step towards left and check again. Still C is not matching with A. So move the right index one step towards left and check again. Still C is not matching with B. So move the right index one step towards left and check again. Still C is not matching with B. Now the right index is not greater than the left index so break here and check if the left and right index are equal. if both are equal then swap the left index value with leftIndex+1 index value. So swap C and A and don't move the left and right index. Still the left index at 0 and right index at last character in the string. 
