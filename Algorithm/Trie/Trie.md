# Trie data structure

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson we will see about the trie data structure. Trie is a tree based data structure.

In trie, we will arrange the alphabets of an word in tree like data structure, where each node represents the alphabet in the word. So the words or strings can be retrieved by traversing down a branch path of the tree.
Trie data structure gets its name from word retrieval.


If we are considering on the lowercase alphabets, we know the maximum number of characters is 26. So, We can declare an array of size 26.
We will write the pseudocode for this TrieNode
```C
class TrieNode
TrieNode array of length 26
boolean isEndOfWord
```
Now we will modify the trie node to accommodate any character not just the lowercase alphabets. So, For this requirement, we will use a hashmap, where the key is the character and value the TrieNode which it links to.
We will see the pseudocode for this TrieNode
```C
class TrieNode
HashMap [Key=character,value=TrieNode]
boolean isEndOfWord
```

 Now we will see how to insert new words in trie data structure. The list of words are

* JAVASCRIPT
* JAVA
* C
* C++
* SWIFT
* SQL

First we will see how to enter the word JAVASCRIPT in the trie data structure.

Enter the first character J in the root node map. This J is not already present in the root node map, So create a new entry with key as J and new node as value. In this node map create a entry with A as key and new node as value. In this node map create a entry with V as key and new map as value. In this node map create a entry with A as key and new node as value. In this node map create a entry with S as key and new node as value. In this node map create a entry with C as key and new node as value. In this node map create a entry with R as key and new node as value. In this node map create a entry with I as key and new node as value. In this node map create a entry with P as key and new node as value. In this node map create a entry with T as key and new node as value. Now we reached the end of the letter, to mark the end of the letter mark this node's isEndOfWord boolean as true. Now we have inserted the word javascript in the trie data structure.

Now  enter the word JAVA in the trie data structure.

Enter the first character J in the root node map. J is already present in the root node map. So get the node associated with the key J. Check whether this node map has the key A, yes it has, So get the node map associated with this key A. Check whether this node map has the key V, yes it has, So get the node map associated with this key V. Check whether this node map has the key A, yes it has, So get the node map associated with this key A. Now the word is completed so mark the node's isEndOfWord boolean as true. Now we have inserted the word java in the trie data structure.

Now enter the word C in the trie data structure.

Enter the first character C in the root node map. C is not already present in the root node map, So create a new entry with key as J and new node as value.Now we reached the end of the letter, to mark the end of the letter mark this node's isEndOfWord boolean as true. Now we have inserted the word C in the trie data structure.


Now enter the word C++ in the trie data structure.

Enter the first character C in the root node map. C is already present in the root node map. So get the node associated with the key C. Check whether this node map has the key +, No it does not have. So create a new entry with key as + and new node as value. In that node map create a entry with key as + and new node as value. . In this node map create a entry with + as key and new node as value. Now the word is completed so mark the node's isEndOfWord boolean as true. Now we have inserted the word C++ in the trie data structure.

Now enter the word SWIFT in the trie data structure.

Enter the first character S in the root node map. S is not already present in the root node map, So create a new entry with key as S and new node as value. In this node map create a entry with W as key and new node as value. In this node map create a entry with I as key and new map as value. In this node map create a entry with F as key and new node as value. In this node map create a entry with T as key and new node as value. Now we reached the end of the letter, to mark the end of the letter mark this node's isEndOfWord boolean as true. Now we have inserted the word swift in the trie data structure.

Now enter the word SQL in the trie data structure.
