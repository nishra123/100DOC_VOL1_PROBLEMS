Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.

Each node in the graph contains a value (int) and a list (List[Node]) of its neighbors.

class Node {
    public int val;
    public List<Node> neighbors;
}
 

Test case format:

For simplicity, each node's value is the same as the node's index (1-indexed). For example, the first node with val == 1, the second node with val == 2, and so on. The graph is represented in the test case using an adjacency list.

An adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a node in the graph.

The given node will always be the first node with val = 1. You must return the copy of the given node as a reference to the cloned graph.

 

Example 1:


Input: adjList = [[2,4],[1,3],[2,4],[1,3]]
Output: [[2,4],[1,3],[2,4],[1,3]]
Explanation: There are 4 nodes in the graph.
1st node (val = 1)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
2nd node (val = 2)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
3rd node (val = 3)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
4th node (val = 4)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
Example 2:


Input: adjList = [[]]
Output: [[]]
Explanation: Note that the input contains one empty list. The graph consists of only one node with val = 1 and it does not have any neighbors.
Example 3:

Input: adjList = []
Output: []
Explanation: This an empty graph, it does not have any nodes.
 

Constraints:

The number of nodes in the graph is in the range [0, 100].
1 <= Node.val <= 100
Node.val is unique for each node.
There are no repeated edges and no self-loops in the graph.
The Graph is connected and all nodes can be visited starting from the given node.
  
INSIGHTS - A simple graph question solved in simpler way - had to refer solution once for it though!
  
```cpp
class Solution {
public:
    Node* cloneGraph(Node* node) {
        // If the given node is null, return null
        if (!node) {
            return nullptr;
        }
        
        // Create an unordered map to keep track of visited nodes in the original graph and their corresponding clones in the new graph
        unordered_map<Node*, Node*> visited;
        
        // Call the recursive clone function with the first node of the original graph and the visited map
        return clone(node, visited);
    }
    
    // Recursive helper function that clones a node and its neighbors
    Node* clone(Node* node, unordered_map<Node*, Node*>& visited) {
        // If the node is already cloned, return the clone
        if (visited.count(node)) {
            return visited[node];
        }
        
        // Create a new clone of the current node
        Node* cloneNode = new Node(node->val);
        
        // Mark the current node as visited in the visited map
        visited[node] = cloneNode;
        
        // Clone the neighbors of the current node recursively and add them to the neighbor list of the clone
        for (Node* neighbor : node->neighbors) {
            cloneNode->neighbors.push_back(clone(neighbor, visited));
        }
        
        // Return the clone of the current node
        return cloneNode;
    }
};
 ```
  
