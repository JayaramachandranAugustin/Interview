#  Depth first Search - Graph

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson we will see about depth first search in graph.

Depth first search is similar to depth first search of tree, The key difference is graph may contain cycles. That is we may visit the same node again. I have a created video tutorial on depth first search in tree - Preorder, Inorder and PostOrder traversal. The link of which I gave in the description.


DFS algorithm is a recursive algorithm that uses backtracking. Select a path and move forward and if there are no more node or new node along the current path, you move backwards on the same path to find nodes to traverse. All the nodes will be visited on the current path till all the unvisited nodes have been traversed after which the next path will be selected.

DFS is can be very handy in lot of situation some of them are finding the connected components and determine the connectivity.

Whenever you are given with a graph check whether it can be solved using DFS.
The time complexity of the Depth first search is O(V+E) where v is the vertex or node and E is the edge which connects the nodes.

We will see the depth first search with an example. Here this graph has 8 nodes. A graph can be represented by the adjacency matrix or adjacency list. Here we are using the adjacency list to represent the graph.

Here Adjacency list is the list of list, It contains list of nodes and each node list holds the nodes details which it connects to.

Here the node 0 connects to the nodes 2 and 3 so the node 0 holds the node 2 and 3.<br/>
We can start with any node. I am starting with node 2. <br/>

Node 2 connects to the node 0 and 3. I am traversing from node 2 to node 0.<br/>

Node 0 connects to node 2 and 3. I traverse from node 0 to node 2, Node 2 is already traversed. So, backtracking to node 0 trying with another edge which connects to node 3.<br/>

Node 3 connects to node 4, 0 and 2. Traverse from node 3 to node 4. 4 is not already visited so this path is fine.<br/>

Now node 4 connects to node 5 and 1. Traverse from node 4 to 5. Node 5 is not already visited so this path is fine. <br/>

Node 5 connects to node 6, 1 and 4. Traverse from node 5 to 6. 6 is not already visited.<br/>

Node 6 connects to 7 and 8. Traverse from node 6 to node 7. 7 is not already visited.<br/>

Node 7 connects to the node 6 and 8. Traverse from node 7 to 6. 6 is already visited. so backtrack to node 7. Now traverse the next edge in 7 which traverses to 8. 8 is not already visited.<br/>

Node 8 connects to the node 6 and 7. Traverse from the node 8 to 6. Node 6 is already visited. So, backtrack to node 8. Now try the next edge from 8 which is 7. Traverse from node 8 to 7. Node 7 is already visited, So,backtrack to node 8. There are no more edges from node 8 so backtrack to node 7. <br/>

There are no more edges from node 7 so backtrack to node 6 <br/>

Now try the next edge from node 6 which connects to node 8. Traverse from node 6 to 8. Node 8 is already visited. So backtrack to node 6. There are no more edges from node 6. So backtrack to node 5.<br/>

Now try the next edge from node 5 which connects to node 1. Traverse from node 5 to 1. Node 1 is not visited. Now we have visited all the nodes in the graph.<br/>

Pseudocode for dfs
```python
 dfs( node)
  visited[node]=true;
  Iterate all the edge nodes of current node
    Get the current edge node
    If the node is not already visited then
    recursively call dfs with current edge node
```

```java
class Graph{
  //First we will create an adjancency list. As I mentioned adjacency list is the list of list.
  ArrayList<ArrayList<Integer>> adjacencyList=new ArrayList<>();
  //We will create a array of boolean which is used to denote if the node is visited or not.
  boolean[] visited;

  Graph(int n){
    visited=new boolean[n];
    for(int i=0;i<n;i++){
      adjacencyList.add(new ArrayList<Integer>());
    }
  }

  public void addEdge(int node,int edgeNode){
    adjacencyList.get(node).add(edgeNode);
  }

  public void dfs(int node){
    //mark the node as visited
    visited[node]=true;
    System.out.println(node);
    //get all the edgeNodes of current node
    Iterator<Integer> itr=adjacencyList.get(node).iterator();
    while(itr.hasNext()){
      int nextNode=itr.next();
      //If the node is already visited then skip
      if(visited[nextNode]) continue;
      //If the node is not already visited then recursively call the dfs with current edge node
      dfs(nextNode);
    }
  }
  public static void main(String args[]){
    Graph graph=new Graph(9);
    graph.addEdge(0,2);
    graph.addEdge(0,3);

    graph.addEdge(1,4);
    graph.addEdge(1,5);

    graph.addEdge(2,0);
    graph.addEdge(2,3);

    graph.addEdge(3,4);
    graph.addEdge(3,0);
    graph.addEdge(3,2);

    graph.addEdge(4,5);
    graph.addEdge(4,1);

    graph.addEdge(5,6);
    graph.addEdge(5,1);
    graph.addEdge(5,4);

    graph.addEdge(6,7);
    graph.addEdge(6,8);

    graph.addEdge(7,6);
    graph.addEdge(7,8);

    graph.addEdge(8,6);
    graph.addEdge(8,7);

    graph.dfs(2);
  }
}
```
