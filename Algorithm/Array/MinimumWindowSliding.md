# Minimum Window Substring

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

Leet code [Link](https://leetcode.com/problems/minimum-window-substring/).

In this lesson we will see about Minimum Window Substring problem, This is the leet code problem the link of which I gave in the description. Given a string S and string T, Find the minimum window in string S which will contain all the characters in T in the time Complexity of O(n).
For example:

Lets take a string S, ABBAACDBCAB and the T is ABC. We need to find the minimum substring which will contain all the characters of T in the string s.

In this string S the substrings which contains all the characters in T are

  * BAAC
  * ACDB
  * BCA
  * CAB

In this minimum window substring which contains all the characters are BCA or CAB.

This problem can be easily solved using the brute force solution with O(n^2) time complexity. In this problem it is asked deliberately to solve in O(n).

This can be achieved using the two pointers.

First load all the characters of T in hash table named window. Where the characters denote the key and value denote the character occurrence count and we will count the number of entries in the hash table.

First point the left and right pointers to the zeroth index position in the String S. Get the character value from the right pointer index position and add it to the new hash table named minimum Window. Check whether the all the character and their count in window hash table are matching with the minimum Window hash table. if there is no match then increment the right index value till all the characters and their count in the window hash table are matching with the minimumWindow hash table. If there is a match then note this substring and now remove the left index position value from this substring and increment the left index and check whether the hash table still matches, if it still matches then note this substring. If it is not matching now then increment the right index position value and add it to the hash table, minimumWindow and continue the above step again till the right index is less than string length.

We will see this with an example.

String t is ABC, load it to the hash table window. Now the window hash table contains three entries A, B and C, with each count 1.

Now assign the left and right index position to the zeroth index. Get the right index value which is A and add it to the hash table minimumwindow and check whether this hash table contains all the characters



```java
public String minWindow(String s, String t){
  //Hash map to store the t string
  Map<Character,Integer> window=new HashMap<Character,Integer>();

  for(int i=0;i<t.length();i++){
    //Get the current index position
    char c=t.charAt(i);
    //load it to the window hash table, Here the key is the character value and the value is
    //character count, if the character is already present get the value if not return and increment
    //with 1
    window.put(c,window.getOrDefault(c,0)+1);
  }
 // Required the count of the entries in the window hashtable
  int required=window.size();
  //Create a result array with three value -1 to the length, 0 to the left and right index values
  int[] res={-1,0,0};
  //current left index is 0 and right index is 0 and expected is the minimumWindow hashtable
  int l=0,r=0,expected=0;
  //This is the minimumwindow hash table
  Map<Character,Integer> minimumWindow=new HashMap<Character,Integer>();
  //if right index is less than the string length
  while(r<s.length()){
    //Get the right index position value character
    char c=s.charAt(r);
    //add it to the minimumWindow hash table
    minimumWindow.put(c,minimumWindow.getOrDefault(c,0)+1);
    //If this character is present in the window hashtable then check whethe the count is matching
    if(window.containsKey(c) && minimumWindow.get(c).intValue()==window.get(c).intValue()){
      //if the count is matching then increment the expected value by 1
      expected++;
    }
    // If left index is less than the right index and all the characters and their count in the window
    //hash table matches with the minimumWindow hash table then take a note of this substring
    while(l<r && expected == required){
        if(res[0]==-1 || res[0]>(r-l)+1 ){
          res[0]=(r-l)+1;
          res[1]=l;
          res[2]=r;
        }
        //Now remove the left character from the substring and decrement the index value in the
        // minimumWindow hash table by 1
        c=s.charAt(l);
        minimumWindow.put(c,minimumWindow.get(c)-1);
        //If the minimumWindow does not contain all the characters and their count after removal then
        //decrement the expected
        //here we need to use the .intValue function to avoid the caching issue during auto unboxing
        if(window.containsKey(c)&& minimumWindow.get(c).intValue()<window.get(c).intValue()){
          expected--;
        }
        //move the left index one step to right
        l++;
    }
    //move the right index one step right.
    r++;
  }
//If the no result then
return res[0]==-1?null:s.substring(res[1],res[2]+1);
}
```
The time complexity of this problem is O(n)
