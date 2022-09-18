# Graph
Topics one must know
=====================
- [BFS Traversal](#bfs-traversal)
    - [BFS for Connected Graph](#bfs-for-connected-graph)
    - [BFS for Disconnected Graph(#bfs-for-disconnected-graph)
- [DFS Traversal](#dfs-traversal)
    - [DFS Iterative](#dfs-iterative)
    - [DFS Recursive](#dfs-recursive)
- [Find cycle in a graph using BFS](#find-cycle-in-a-graph-using-bfs)
    - [Cycle in undirected graph using BFS](#cycle-in-undirected-graph-using-bfs)
    - [Cycle in directed graph using BFS](#cycle-in-directed-graph-using-bfs)
 - [Find cycle in a graph using DFS](#find-cycle-in-a-graph-using-dfs)
    - [Cycle in undirected graph using DFS](#cycle-in-undirected-graph-using-dfs)
    - [Cycle in directed graph using DFS](#cycle-in-directed-graph-using-bds)
- [Topological Sort](# topological-sort)
- [Bipartate Graph](#bipartate-graph)
- [Minimum Spanning Tree](#minimum-spanning-tree)
- Shortest distance
### BFS Traversal
#### BFS for Connected Graph
```
class BFS {
    public ArrayList<Integer> bfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        // Code here
        ArrayList<Integer> res = new ArrayList<>();
        Queue<Integer> q = new ArrayDeque<>();
        boolean[] visited = new boolean[V];
        q.offer(0);
        visited[0] = true;
        while(!q.isEmpty()){
            int vertex = q.poll();
            res.add(vertex);
            for(int i=0; i<adj.get(vertex).size(); i++){
                int nextVertex = adj.get(vertex).get(i);
                if(!visited[nextVertex]){
                    q.offer(nextVertex);
                    visited[nextVertex] = true;
                }
            }
        }
        return res;
    }
}
```
#### BFS for Disconnected Graph
* Use the code as (#bfs-for-connected-graph), instead of offering first vertex, make a for loop and call bfs for all unvisited vertexes. *
```
for(int i=0; i<V; i++){
    if(!visited[i])
    bfs(adj, visited, i, res);
}
```

## DFS for Connected/Disconnected Graph
```
class DfsForDisconnectedGraph {
    public ArrayList<Integer> dfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        
        ArrayList<Integer> res = new ArrayList<>();
        boolean[] visited = new boolean[V];
        
        //For Connected Component of Graph
        dfs(adj, visited, 0, res);
        
        //For Disconnected Graph
        for(int i=0; i<V; i++){
            dfs(adj, visited, i, res);
        }
        return res;
    }
    
    private void dfs(ArrayList<ArrayList<Integer>> adj, boolean[] visited, int K, ArrayList<Integer> res){
        visited[K] = true;
        res.add(K);
        for(int i=0; i<adj.get(K).size(); i++){
            int nextVertex = adj.get(K).get(i);
            if(!visited[nextVertex]){
                dfs(adj, visited, nextVertex, res);
            }
        }
    }
}
```
