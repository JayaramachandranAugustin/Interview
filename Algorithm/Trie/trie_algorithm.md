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

Enter the first character C in the root node map. C is already present in the root node map. So get the node associated with the key C. Check whether this node map has the key +, No it does not have. So create a new entry with key as + and new node as value. In that node map create a entry with key as + and new node as value.  Now the word is completed so mark the node's isEndOfWord boolean as true. Now we have inserted the word C++ in the trie data structure.

Now enter the word SWIFT in the trie data structure.

Enter the first character S in the root node map. S is not already present in the root node map, So create a new entry with key as S and new node as value. In this node map create a entry with W as key and new node as value. In this node map create a entry with I as key and new map as value. In this node map create a entry with F as key and new node as value. In this node map create a entry with T as key and new node as value. Now we reached the end of the letter, to mark the end of the letter mark this node's isEndOfWord boolean as true. Now we have inserted the word swift in the trie data structure.

Now enter the word SQL in the trie data structure.

Enter the first character S in the root node map. S is already present in the root node map. So get the node associated with the key S. Check whether this node map has the key Q, No it does not have. So create a new entry with key as Q and new node as value. In that node map create a entry with key as L and new node as value .Now the word is completed so mark the node's isEndOfWord boolean as true. Now we have inserted the word SQL in the trie data structure.


We have seen how to enter the word in trie data structure. Now we will see how to search for the words in Trie data structure. We can do two kind of search in the trie data structure one is prefix based search or whole word search.

Prefix based search checks whether the words with the given prefix is present in the trie data structure or not.
Now we will if the prefix java SQ or GO SCALA present in the trie data structure or not.

Now we will start with the prefix based search. First we will start with java.

First start with the root node. Check if the character J is present in the root node. Here J is present so get the node associated with the key J. Check whether A is present in this node map. Yes A is present in the node map. Get the node associated with the key A in this node. Check whether V is present in this node map. Yes V is present in the node map. Get the node associated with the key V in this node. Check whether A is present in this node map. Yes A is present in the node map. Get the node associated with the key A in this node. The prefix JAVA is present in the Trie data structure.

Check whether the prefix SQ is present in the Trie data structure.

First start with the root node. Check if the character S is present in the root node. Here S is present so get the node associated with the key S. Check whether Q is present in this node map. Yes Q is present in the node map. So, the prefix SQ is present in the Trie data structure.

Check whether the prefix GO is present in the Trie data structure.

First start with the root node. Check if the character G is present in the root node. Here G is not present, So return this prefix is not present in the Trie data structure.

Check whether the prefix SCALA is present in the Trie data structure.

First start with the root node. Check if the character S is present in the root node. Here S is present so get the node associated with the key S. Check whether C is present in this node map. Here C is not present in the node map. So, we no need to search the remaining characters and this prefix SCALA is not present in the Trie data structure.

Now check whether the complete word is present in the trie data structure or not.
Now we will see if the words java, C, C++, SQ, C# present in the trie data structure or not.
Check whether the word JAVA is present in the Trie data structure.

First start with the root node. Check if the character J is present in the root node. Here J is present so get the node associated with the key J. Check whether A is present in this node map. Yes A is present in the node map. Get the node associated with the key A in this node. Check whether V is present in this node map. Yes V is present in the node map. Get the node associated with the key V in this node. Check whether A is present in this node map. Yes A is present in the node map. Get the node associated with the key A in this node. Now check whether the isEndOfWord boolean is true in this node. The word JAVA is present in the Trie data structure.

Check whether the word C is present in the Trie data structure.

First start with the root node. Check if the character C is present in the root node. Here C is present so get the node associated with the key C. Now check whether the isEndOfWord boolean is true in this node. The word C is present in the Trie data structure.

Check whether the word C++ is present in the Trie data structure.

First start with the root node. Check if the character C is present in the root node. Here C is present so get the node associated with the key C. Check whether + is present in this node map. Yes + is present in the node map. Get the node associated with the key + in this node. Check whether + is present in this node map. Yes + is present in the node map.  Now check whether the isEndOfWord boolean is true in this node. The word C++ is present in the Trie data structure.




```java
class Trie {

    TrieNode rootNode;

    /** Initialize your data structure here. */
    public Trie() {
        rootNode=new TrieNode();
    }

    /** Inserts a word into the trie. */
    public void insert(String word) {
        TrieNode node=rootNode;
        for(int i=0;i<word.length();i++){
            char element=word.charAt(i);
            if(node.nextNode[element-'a']==null){
                node.nextNode[element-'a']=new TrieNode();
            }
            node=node.nextNode[element-'a'];
        }
        node.isWordEnd=true;

    }

    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        TrieNode node=rootNode;
        for(int i=0;i<word.length();i++){
            char element=word.charAt(i);
            if(node.nextNode[element-'a']==null) return false;
            else{
                node=node.nextNode[element-'a'];
            }

        }
         return node.isWordEnd;
    }

    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        TrieNode node=rootNode;
        for(int i=0;i<prefix.length();i++){
            char element=prefix.charAt(i);
            if(node.nextNode[element-'a']==null) return false;
            else{
                node=node.nextNode[element-'a'];
            }
        }
         return true;
    }

    class TrieNode{
        TrieNode[] nextNode=new TrieNode[26];
        boolean isWordEnd;
    }
}
```
