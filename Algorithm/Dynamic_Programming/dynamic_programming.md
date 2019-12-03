# Dynamic Programming

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).


In this lesson we will see about Dynamic programming. Dynamic programming is one of the important key topic when you are preparing for the interview. Dynamic programming might be challenging at the first once you practice good amount of problems in the Dynamic programming you will find it really easy.

To understand dynamic programming better, I personally recommend to have some understanding in recursion before proceeding with dynamic programming. Refer to my video tutorial on recursion the link of which I gave in the description. Dynamic programming is an optimizing strategy for a recursive solution.

This reduces the time complexity from exponential to polynomial. We will see this in depth while analyzing how Dynamic programming improves the recursive solution time complexity.
We will see this in depth using the Fibonacci series example.
Fibonacci series at a index is found by adding values present in the index-1 and index-2. The series starts with the elements 0 and 1.

0,1,1,2,3,5,... etc.,

Here the Fibonacci series starts with 0 and 1. The third element is calculated by adding this 0 and 1. So the third element is 1. The fourth element is found by adding the values present in the index 2 and 3. So the fourth element is 1 + 1 which is 2.

When can we use this Dynamic programming.

__Property 1__. When you find a problem which can be split into overlapping subproblems.   

For example. Find the 5 th element in the Fibonacci series.

Solution can be achieved by adding the element at index 3 and index 4. To get the index 3 value add index 1 and index 2 value, This is one subproblem. Index 4 value can be found by adding the value at index 2 and index 3 This is another subproblem here if you notice these subproblems overlap.

If you find overlapping subproblems in your problem then you can use dynamic programming.


__Property 2__. When you find a problem which is said to have optimal substructure, That is, if an optimal solution can be constructed from optimal solutions of its subproblems.   

For example. Dijkstra's algorithm. In Dijkstra's algorithm if you want to find the optimal path from node 1 to node 4. We will find the optimal solution from node 1 to node 2. then from node 1 to node 3. Then from node 1 to node 4. Here this problem is divided into optimal substructure. So if you find optimal substructure in your problem then you can use dynamic programming.


Now we know when to use the dynamic programming. We will see how to optimize the recursive solution with dynamic programming.
There are two ways to do it. They are
  1. Memoization or Top down approach.
  2. Tabulation or Bottom up approach

We will understand these approaches with the Fibonacci series problem.



  __1. Memoization or Top down approach__

We will write a simple function which finds the element at nth index position of the Fibonacci series using recursion. Whenever we are handing the recursion, you need to understand the base case . The base case is if the N is less than or equal to 1 return n that means for the index position 0 the value is 0 and the value at the index position 1 the value is 1.  So the base case is if n is less than or equal to 1 then we need to return the N here. To find the element at the index position n we need to add the two preceeding element. That is, return Fibonacci n minus 1 plus Fibonacci n minus 2. We'll just return Fibonacci n minus 1 plus Fibonacci n minus 2 here.

 ```JAVA
 public int fib(int n){
   if (n<=1)return n;
   return fib(n-1)+fib(n-2);
 }

 ```
 The time complextiy of this solution is exponential and space complexity is O(n) if we consider the space occupied by the stack in recursive solution.

We will see how this recursion works with this tree structure explanation.

So here we want to find the value of the element at the fifth index position. So we are calling this you Fibonacci function with the input value 5,Fibonacci function calls itself with the input value 3 and this it calls itself again with the input value 2, which in turn calls itself again with the input value 1. So when it reaches one it reaches the base case. fibonacci of 1 is 1 and then it moves to the left side, which is 2 minus 2  gives us zero. So here this returns zero. For the value 3 the right hand expression is fibonacci 1, we reach the base case for fibonacci 1 which gives us 1. For the value 4 the right hand expression is fibonacci 2. It divides into fib of 1 which gives us 1 because this makes the base case and the right hand expression is fib of 0 which gives us 0. Here we got the value at the index position 4 which is 2+1, 3.

The right hand expression for the input value 5 is fibonacci 3 and this it calls itself again with the input value 2 and it calls itself with the input value 1 which meets the base case and returns 1 and the right hand expression for the input value 2 is fibonacci (0) which returns 0. So the fib 2 is 1 and the fib 3 is 1+1, which is 2. So the final answer is fib(4) which is 3 and fib(3) which is 2. So the output is 3+2,5

Here if you see this tree. we are repeating the same subproblems and computing it again. For example fib(3) is computed twice and fib(2) is computed thrice. This is where the memoization approach comes into the picture.

That is whenever we are coming up with a sub problems. We need to store the results of the subproblems and if you see the same subproblem again, then we can use that subproblem result directly rather than computing it again from the scratch,  This is the main motive behind the memoization. So we will see how this tree changes after we store the subproblem results.


So here we need to find the value of the element present at the index position 5 in the Fibonacci series. So we are calling the fib function with the value 5. So this fib(5) calls itself again with the value 4 and this again cards itself with the value 3 and this again calls itself with the value 2 and this again calls itself with the value 1 here fib(1) gives us the value of 1 because it meets the base case. So it gives us 1 and the right and expression for the value 2 is fib(0), FIB of 0 gives us 0. so fib of 2 is 1 plus 0 so FIB of 2 is 1. Now we have computed the result for this subproblem fib of 2 so the store its value 1. and  the right hand expression of 3 is fib(1) which is 1. So FIB of 3 is 1 plus 1 which gives the result 2. Now we have computed the result for this subproblem fib of 3 so the store its value 1. For the value 3 the right expression is fib(2). We already stored the value FIB of 2, which is 1. Fib of 4 gives us 2 plus 1 which is 3, store this subproblem result and the right and expression of 5 is fib of 3, we already stored the value of fib of 3 which is 2. So 3 plus 2 gives you the value 5, this is How the tree looks After we have applied the memorization. So here we no need to repeat the computation. So this is memoization. Memoization is storing the subproblems values and using it when we see the same subproblem again. This reduces the time complexity. The memoization is also known as top down approach because we are starting from the root node and going to the leaf node. So this is top down approach.

The java implementation of this memoization. Here we are using additional array which holds the subproblem results.

```java
public class Fibonacci {
	public int fib(int n,int[] f){
      //base case for the recursive loop
      if(n<=1){
		    return n;
		  }
      //This will be initially Integer.MIN_VALUE
      //Return the result of already computed subproblem
		  if(f[n]!=Integer.MIN_VALUE) return f[n];
		  else{
        //compute the subproblem results and store it in array
		    f[n]=fib(n-1,f)+fib(n-2,f);
		  }
      //return subproblem result
		  return f[n];
		}

	public static void main(String[] args) {
		int[] f=new int[6];
		for(int i=0;i<6;i++) {
			f[i]=Integer.MIN_VALUE;
		}
		Fibonacci fibo=new Fibonacci();
		System.out.println(fibo.fib(5, f));
	}
}

```

The time complexity of the above solution is O(n) and the space complexity is O(n) for the additional hash map

__2. Tabulation or Bottom up approach__

Tabulation means instead of using the recursive solution use Table start from the subproblem results we know and build the subproblems on top of it.
