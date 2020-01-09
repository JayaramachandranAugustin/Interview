# Median of two sorted array

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson we will see how to find the median of two sorted array. I really like the wikipedia definition of the Median
>The median is the value separating the higher half from the lower half of a data sample

This definition is key to solve this problem, we will see how shortly
Let take a single sorted array and the median will be at the index n/2 if the n is odd and If the n is even take the two middle values and divide it by 2 will give the answer.

Here the key thing to note is median is the one which separates the higher half from the lower half. The higher half is at the right hand side and the lower half is at the left hand side of the median.

Now we will see a very easy solution which is merge sort. Merge this two array by comparing the index values of both array from left to right.


Once the two array are merged then find the median. Straight forward. Here the time complexity is O(m+n). Where m is the length of the first array and the n is the length of the second array.

Can we improve the time complexity, yes. Just by using the median definition and binary search. Now we came to the main picture. we will see this how.

Divide the two array by a single separator which divides this two array to two equal length parts in case of even number of m+n. In case of odd m+n, first part contains one element more than the second part.

While dividing we need to divide in such a way than maximum element in the first part is less than or equal to  the minimum element in the second part.

Once divided following this rule. Then the median is max of left part if the m+n is odd. If the m+n is even then the median the max of left part plus min of right part divide by 2.
Sounds simple the real question is how to actually divide. Use the binary search to divide.

The same separator separates the array 1 and array 2. Lets name the divider which divides the array 1 as i and the divider which divides the array 2 as j. I can be anywhere between 0 to m. Here we start from the mid value of m. We will take mini as 0 and maxi as m and i is the sum of both these values divide by 2. j can be mid point - i. Here the j divides n. Here the m must be less than n, Than is the length of array 1 must be less than array 2 because if the array 2 size is greater than array 1. It leads to the minus value of j. so array 1 length must be lesser than or equal to array 2.

Now we have found the divider i and j. Now we will see how we will validate the condition - max of first part is less than or equal to min of second part -  with a example.

Here the array 1 is 2, 3, 7, 8, 10 and array 2 is 4, 5, 9, 13, 15 and 18. First we need check the length of array 1 is less than or equal to the length of array 2. array 1 length is already less than the array 2 length.

Now we need to find the i and j initial value. i can be between 0 to 5 which is the array 1 length.
We will calculate the mid by taking the adding the mini which is 0 and the maxI which is 5. So, the i value is min1+maxi/2, which is 0+5/2. 2. 


how we will do this using binary search.
