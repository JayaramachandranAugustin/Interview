# Topological sort


In this lesson we will see about Topological sort, We will see the topics such as What is Topological sort? the applications of the Topological sort and how to perform the Topological sort with code and animation.

What are the real applications of the Topological sort. Lets take you need to learn React framework without any previous knowledge on web development. So what are the pre-requisite to learn the React. Pre-requisites are we need to learn the HTML, CSS and Plain vanilla JavaScript.  What is the order in which we need to learn the pre-requisite. HTML first followed by CSS followed by Plain vanilla JavaScript. Then finally React. Here the Topological sort is used to sort this topics based on these dependency. The Topological sorted list is HTML, CSS, JavaScript and React. Some other examples or topological sort is Handling project dependency. Where one library package is dependent on another and it might be dependent on other. So, Handling package dependency for a project can be done using topological sort.

A very simple analogy is. Now you came here to learn about topologicalSort. To understand topologicalSort you need to know depth first search. Before learning depth first search you need to know about graph data structure and array. So the topologicalSort gives the list in which you need to learn the pre-requisite before learning about topological sort. The link to learn the pre requisite are given in the description.

The given graph must be acyclic. We will see why this is necessity. Let take for a course C, The pre-requisite is A and B. If for the course B the prerequiste is course A. For the course A the pre-requisite is course A. We can't complete both A and B. Eventually we can't complete the course C.


So the definition of the topological sort is, a topological sort or topological ordering of a directed graph is a linear ordering of its vertices such that for every directed edge ab from vertex a to vertex b, a comes before b in the ordering.


We will see topological sort in detail using a graph.
We have this graph, This is directed and acyclic. We have derived the adjacency list from this graph. Adjacency list holds the nodes list  and each node list hold list connecting nodes from this node. For example , The node 1 connects to the node 1. Node 1 connects to the node 8, 7 and 2. So the node 1 list holds the integers 8, 7 and 2.

 Now we will see how to perform the topological sort,  Now Randomly select a node from the graph. Here I am selecting the node 0. Node 0 connects to node 1. So, Traverse from 0 to 1. Now 1 connects to the nodes 8, 7 and 2. Check whether the 8 is visited or not 8 is not visited so, Traverse from 1 to 8. 8 connects to node 7. Node 7 is not already visited so Traverse from node 8 to 7. Node 7 is leaf node. So add this node to the last index in the topological sort array. Now traverse back to 8. check whether node 8 has any other unvisited node. Now node 8 does not have any other unvisited node so add 8 to next available empty index in topological sort array from the left. Now traverse back to Node 1. Next node which connects from node 1 is node 7. Node 7 is already visited. Next available node from node 1 is 2. node 2 is not already visited. So traverse from node 1 to node 2. 2 is leaf node so add it to the next available empty index in topological sort array from the left. Traverse back to 1 There are no more unvisited edge nodes for node 1. So add node 1 to the last available index in the topological sort array. Now traverse back to node 0. Node 0 does not have any unvisited edge nodes. So add 0 to the last empty index in the topologicalSort array. Now we need to pick the next node Randomly I pick 1. 1 is already visited . So picking 2, 2 is also already visited. Picking 3. 3 is not already visited. Now take the edge nodes of node 3. Edge node of node 3 is node 4. So, Traverse from node 3 to node 4. Node 4 doesn't have any unvisited edges so add 4 to the last empty index in the topologicalsort array. Now traverse back to node 3. Node 3 has no more unvisited nodes so add 3 to the last empty index in the topologicalSort array. Now Pick the next node which 3, 3 is visited, 4 is also visited. Next pick the node 5 which is not visited. Node 5 does not have any unvisited nodes. So, add integer 5 to the last empty index in the topologicalSort array. Now pick the next node 6 which is not visited. Node 6 does not have any unvisited nodes.  So, add integer 6 to the first index in the topologicalSort array. Now we have completed the Topological sort. One key thing to note in the topologicalSort is the result topologicalSort array might be different for the same graph. Not all the topologicalSort give the same result for a single graph. It depends on the adjacencyList. Here node 1 edge nodes are 8,7 and 2. If it is 2,7,8. There will be different topologicalSort result. Try it yourself.  



```java
import java.util.ArrayList;
import java.util.List;

class TopologicalSort{

  List<List<Integer>> adjacencyList;

  TopologicalSort(int n){
    adjacencyList=new ArrayList<List<Integer>>(n);
    for(int i=0;i<n;i++){
      adjacencyList.add(i,new ArrayList<Integer>());
    }
  }

  public void addEdge(int startNode, int endNode){
    adjacencyList.get(startNode).add(endNode);
  }

  public int[] topologicalSort(){
    boolean[] visited=new boolean[adjacencyList.size()];
    int[] ordered=new int[adjacencyList.size()];
    List<Integer> list=new ArrayList<>();
    int lastIndex=adjacencyList.size()-1;
    for(int i=0;i<adjacencyList.size();i++){
      list.clear();
      if(!visited[i]){
        dfs(i,visited,list);
        for(int a:list){
          ordered[lastIndex]=a;
          lastIndex--;
        }
      }
    }
    return ordered;
  }

  public void dfs(int index,boolean[] visited,List<Integer> list){
      visited[index]=true;
      List<Integer> edges=adjacencyList.get(index);
      for(int a:edges){
        if(!visited[a]) dfs(a,visited,list);
      }
      list.add(index);
  }
  public static void main(String[] args){
    TopologicalSort topologicalSort=new TopologicalSort(9);
    topologicalSort.addEdge(6,3);
    topologicalSort.addEdge(6,5);
    topologicalSort.addEdge(3,4);
    topologicalSort.addEdge(3,0);
    topologicalSort.addEdge(5,0);
    topologicalSort.addEdge(5,8);
    topologicalSort.addEdge(4,2);
    topologicalSort.addEdge(4,1);
    topologicalSort.addEdge(0,1);
    topologicalSort.addEdge(1,8);
    topologicalSort.addEdge(1,7);
    topologicalSort.addEdge(1,2);
    topologicalSort.addEdge(8,7);
    for(int a:topologicalSort.topologicalSort()){
      System.out.print(a +" ");
    }
  }
}
```
