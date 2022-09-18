# Graph
## Topics one must know
*** BFS Traversal ***
[## BFS for Connected Graph
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
```](bfs-traversal)
## BFS for Disconnected Graph
```
class BfsForDisconnectedGraph {
    public ArrayList<Integer> bfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        ArrayList<Integer> res = new ArrayList<>();
        boolean[] visited = new boolean[V];
        for(int i=0; i<V; i++){
            if(!visited[i])
            bfs(adj, visited, i, res);
        }
        return res;
    }
    
    private void bfs(ArrayList<ArrayList<Integer>> adj, boolean[] visited, int K, ArrayList<Integer> res){
        Queue<Integer> q = new ArrayDeque<>();
        visited[K] = true;
        q.offer(K);
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
    }
}
```
*We can use the disconnected code in connected scenario also, we just need to remove for loop in bfsOfGraph method.*

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
