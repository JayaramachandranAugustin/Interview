#  Breadth first Search - Graph

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).


Breadth first search is similar to breadth first search of tree, The key difference is graph may contain cycles. That is we may visit the same node again. I have a created video tutorial on breadth first search in tree traversal. The link of which I gave in the description.


Breadth first search uses the queue data structure. Queue is the first in first out data structure. That is the element to enter first is the element come out first. Here queue is used to track which node to visit next.

The algorithm is very simple. The start node added to queue first. Then their nodes are added to queue if they are not already visited. We keep on continue this till the queue becomes empty.

The time complexity of the breadth first search is O(V+E) where v is the vertex or node and E is the edge which connects the nodes.

We will see this with an example. A graph can be represented by the adjacency matrix or adjacency list. Here we are using the adjacency list to represent the graph. Here Adjacency list is the list of list, It contains list of nodes and each node list holds the nodes details which it connects to.

Tasks we can perform with the breadth first search are
Finding the shortest path in the unweighted graph.

We can choose any node. I choose to start from the node 2, So add this node to the queue.

Now check if the queue is empty. The queue has 2 in it. Now remove the top of queue which is 2 and add all the edgeNodes of 2 into the queue, which are node 0 and node 3.

Now remove the top of the queue which is 0 add the edgeNodes of 0 to queue, since 2 and 3 are already visited and added to the queue skip the edge nodes of 0.

Now remove the top of the queue which is 3 and add the edgenodes of 3 which are 4,0 and 2. 4 is not already visited. So we can add it to queue. 0 which is already visited so this node is skipped and 2 is also already visited so this node is also skipped.

Now remove the top of the queue which is 4 and add the edgenodes of 4 which are 5 and 1. 5 is not already visited. So we can add it to the queue. 1 which is also not already visited so add it the queue.

Now remove the top of the queue which is 5 and add the edgenodes of 5 which are 6, 1 and 4. 6 is not already visited so we can add it to the queue. 1 and 4 are already visited or added to the queue. So, no need add 1 and 4 to the queue.

Now remove the top of the queue which is 1 and add the edgenodes of 1 which are 4 and 5. 4 and 5 are already visited so we can skip these nodes.

Now remove the top of the queue which is 6 and add the edgenodes of 6 which are 7 and 8. 7 is not already visited. So we can add it to the queue. 8 which is also not already visited so add it the queue.

Now remove the top of the queue which is 7 and add the edgenodes of 7 which are 6 and 8. 6 and 8 nodes are already visited or added to the queue so we can skip these nodes.

Now remove the top of the queue which is 8 and add the edgenodes of 8 which are 6 and 7. 6 and 7 are already visited so we can skip these nodes.

Now we have the traversed the graph completely using breadth first search.

Pseudo code for the breadth first search is

```python
visited[number of nodes] -> holds whether the node visited or not
queue.enqueue(startNode)
visited[startNode]=true
while queue is not empty
  node=queue.dequeue
  print(node) -> traversing the node here
  for edgenode in (edgenodes of node)
    if !visited[edgenode]
      queue.enqueue(edgeNode)
      visited[edgeNode]=true
```

We will see the breadth first search pseudocode implementation in java

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

  public void bfs(int startNode){
    //The bfs uses queue data structure
    Queue<Integer> bfsQueue=new LinkedList<Integer>();
    //Add the start node to the queue
    bfsQueue.add(startNode);
    //Mark the start node as visited
    visited[startNode]=true;
    //iterate till the queue is empty
    while(!bfsQueue.isEmpty()){
      //remove the top of the queue
      int node=bfsQueue.remove().intValue();
      System.out.print(node+" ");
      for(int edgeNode:adjacencyList.get(node)){
        //If this node is visited skip this node
        if(visited[edgeNode]) continue;
        //If this node is not visited add this node to the queue
        bfsQueue.add(edgeNode);
        //once the node is added to the queue we are marking it as visited
        visited[edgeNode]=true;
      }
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

    graph.bfs(2);
  }
}
```
