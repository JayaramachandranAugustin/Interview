#  Word Ladder 2

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson we will see about the word ladder 2 problem from the leetcode. This is very interesting problem which can be solved with both BFS and DFS combined together.

We will see the problem statement now.
We are given with two words begin word and end word, and a dicitionary' word list, find all shortest transformation sequence(s) from beginWord to endWord, such that:
1.	Only one letter can be changed at a time
2.	Each transformed word must exist in the word list. Note that beginWord is not a transformed word.
Here note is very important. Which makes us to understand the question better.

Note:
* Retum an empty list if there is no such transformation sequence.
* All words have the same length.
* All words contain only lowercase alphabetic characters.
* You may assume no duplicates in the word list.
* You may assume beginWord and endWordare non—empty and are not the same.

```  
Sample input and output.
beginWord = "hit", endWord = "cog",
wordList = ["hot","dot","dog","lot","log","cog"]
```

```
Output:
[
  ["hit","hot","dot","dog","cog"],
  ["hit","hot","lot","log","cog"]
]
```
Here the begin word is hit and the end word is cog. Dictionary word list contains 6 words including the end word.
So how to find the solution to this problem.

Begin word is Hit, If you change one character it will become hot if you change one character it will become dot and if you change one character it will become dog if you change one character it will become cog. Here cog is the end word. Here one more key to note is we need to print all the shortest paths. That if two or more path has the same shortest path we need to print all the paths.

Before seeing about the solution, As I mentioned I am going to solve this problem using bfs and dfs. To learn or revise BFS and DFS check my video tutorial on BFS and DFS. The link of which I gave in the description.

The solution to this problem is, we know the start and end node and we also know the interim nodes which is the dictionary words. Now we need to build a graph and find the list of shortest paths.

We will take this input.
beginWord = "hit", endWord = "cog", wordList — ["hot","dot","dog","lot","log","cog"]


Now we need to build a graph from this begin word and end word as last node and wordlist is the nodes which forms the path from begin to end word. Now we will see how can we build the graph using the breadth first search.


First start with the start node which is the begin node and find the edge nodes of this node. Current node is hot. To find the edge nodes change one character from the word and check whether it is present in the dictionary. We will see how can we do this.

Given the word hot. First change the first character in the word from a to z but not h and check whether the word is present in the dictionary. Example change to aot check whether it is present it is not present Change bot check whether it present continue this till z and there is a match mark this node as edge node and do this for all the characters in the word. Like Hat, Hoa etc.,

While creating the graph we must create a edge only between one level to the next level. Not  between the same level or previous level. By this way we can make sure the we are getting only the shortest path. no need to track the distance and we need to stop building the graph as soon as we find the end node.

First add the begin node, hit into the queue and also add the first node to nodes to visit list. This is to keep track of nodes to visit in the current level.
while the queue is not empty continue with the while loop. Now get the to visit list count and add this nodes to visited list which keeps track of all the visited nodes from the root node to the current node. Then clear the nodes in tovisit list. Now iterate for all the nodes in the current level. remove the top of the queue and get the edgenodes of the currentnode.

As seen before to get the edgenodes get the current word and convert it to char array. for each index value replace it from a to z except the same current index value. If this value is present in the dictionary list then add it to the edge nodes.

Now we found the edgeNodes for the current word
If the edgenode is equal to the endNode then mark the reachedDestination flag as true.

if the edgeNode is not already present in the visited hash set then add it to the graph. If the edgelist is not present in the visited hashset and to visit hashset then add this edgenode to the  queue and add it to the to visit hash set.

If the reachedDestination is true that means we reached endnode so stop building the graph

Now traverse the graph using depth first search and print all the path which connects from start to end node. Here all the path which connects from start to end will have same shortest distance.

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.HashSet;
import java.util.LinkedList;
import java.util.List;
import java.util.Queue;

public class WordLadderII {
	    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
	        HashSet<String> dict=new HashSet<String>(wordList);
	        List<List<String>> result=new ArrayList<>();
	        HashMap<String,ArrayList<String>> graph=new HashMap<>();
	        buildGraph(beginWord,endWord,dict,graph);
	        findShortPathLists(beginWord,endWord,result,new ArrayList<String>(),graph);
	        return result;
	    }


	    public void  buildGraph(String beginWord,String endWord,HashSet<String> dict,HashMap<String,ArrayList<String>> graph){
	        HashSet<String> toVisit=new HashSet<String>();
	        HashSet<String> visited=new HashSet<String>();
	        Queue<String> queue=new LinkedList<String>();
	        boolean reachedDest=false;
	        queue.offer(beginWord);
	        toVisit.add(beginWord);

	        while(!queue.isEmpty()){
	            int currLvlNodeCnt=toVisit.size();
	            visited.addAll(toVisit);
	            toVisit.clear();

	            for(int i=0;i<currLvlNodeCnt;i++){
	                String currWord=queue.poll();
	                ArrayList<String> edgeNodes=getEdgeNodes(currWord,dict);
	                for(String edgeNode:edgeNodes){
	                    if(edgeNode.equals(endWord)) reachedDest=true;
	                    if(!visited.contains(edgeNode)){
	                        if(!graph.containsKey(currWord)){
	                            graph.put(currWord,new ArrayList<String>());    
	                        }
	                        graph.get(currWord).add(edgeNode);
	                    }
	                    if(!visited.contains(edgeNode) && !toVisit.contains(edgeNode)){
	                        toVisit.add(edgeNode);
	                        queue.offer(edgeNode);
	                    }
	                }
	            }
	            if(reachedDest) break;
	        }

	    }

	    public ArrayList<String> getEdgeNodes(String currWord,HashSet<String> dict){
	        char[] charArr=currWord.toCharArray();
	        ArrayList<String> edgeNodes=new ArrayList<String>();

	        for(int i=0;i<charArr.length;i++){
	            for(char c='a';c<='z';c++){
	                if(charArr[i]==c) continue;                
	                char temp = charArr[i];
	                charArr[i]=c;
	                String str=new String(charArr);
	                if(dict.contains(str)) edgeNodes.add(str);
	                charArr[i]=temp;
	            }
	        }
	        return edgeNodes;
	    }

	    public void findShortPathLists(String currWord, String endWord,List<List<String>> result,ArrayList<String> path,HashMap<String,ArrayList<String>> graph){
	        path.add(currWord);
	        if(currWord.equals(endWord)) result.add(new ArrayList<String>(path));
	        else if(graph.containsKey(currWord)){
	            for(String word:graph.get(currWord)){
	                findShortPathLists(word,endWord,result,path,graph);
	            }
	        }
	        path.remove(path.size()-1);
	    }
	    public static void main(String[] args) {
			WordLadderII wl=new WordLadderII();
			List<String> dict=new ArrayList<String>();
			dict.add("hot");
			dict.add("dot");
			dict.add("dog");
			dict.add("lot");
			dict.add("log");
			dict.add("cog");
			wl.findLadders("hit", "cog", dict);
		}
}


```
There is another medium problem word ladder problem 1. In which we need just to find the shortest distance. We can do small modification in the above code. we can increment the counter at each level and once we reached the endword. Increment the counter and assign it to result. This result is the shortest distance.

```JAVA
import java.util.ArrayList;
import java.util.HashSet;
import java.util.LinkedList;
import java.util.List;
import java.util.Queue;

public class WordLadderII {
	    public int findLadders(String beginWord, String endWord, List<String> wordList) {
	        HashSet<String> dict=new HashSet<String>(wordList);
	        return buildGraph(beginWord,endWord,dict);
	    }


	    public int  buildGraph(String beginWord,String endWord,HashSet<String> dict){
	        HashSet<String> toVisit=new HashSet<String>();
	        HashSet<String> visited=new HashSet<String>();
	        Queue<String> queue=new LinkedList<String>();
	        int result=0,count=0;
	        boolean reachedDest=false;
	        queue.offer(beginWord);
	        toVisit.add(beginWord);

	        while(!queue.isEmpty()){
	            int currLvlNodeCnt=toVisit.size();
	            visited.addAll(toVisit);
	            toVisit.clear();
	            count++;
	            for(int i=0;i<currLvlNodeCnt;i++){
	                String currWord=queue.poll();
	                ArrayList<String> edgeNodes=getEdgeNodes(currWord,dict);
	                for(String edgeNode:edgeNodes){
	                    if(edgeNode.equals(endWord)) reachedDest=true;
	                    if(!visited.contains(edgeNode) && !toVisit.contains(edgeNode)){
	                        toVisit.add(edgeNode);
	                        queue.offer(edgeNode);
	                    }
	                }
	            }
	            if(reachedDest) {
	            	result=count+1;
	            	break;
	            }
	        }
	        return result;

	    }

	    public ArrayList<String> getEdgeNodes(String currWord,HashSet<String> dict){
	        char[] charArr=currWord.toCharArray();
	        ArrayList<String> edgeNodes=new ArrayList<String>();

	        for(int i=0;i<charArr.length;i++){
	            for(char c='a';c<='z';c++){
	                if(charArr[i]==c) continue;                
	                char temp = charArr[i];
	                charArr[i]=c;
	                String str=new String(charArr);
	                if(dict.contains(str)) edgeNodes.add(str);
	                charArr[i]=temp;
	            }
	        }
	        return edgeNodes;
	    }

	    public static void main(String[] args) {
			WordLadderII wl=new WordLadderII();
			List<String> dict=new ArrayList<String>();
			dict.add("hot");
			dict.add("dot");
			dict.add("dog");
			dict.add("lot");
			dict.add("log");
			dict.add("cog");
			wl.findLadders("hit", "cog", dict);
		}
}
```
