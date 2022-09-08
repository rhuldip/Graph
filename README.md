# Graph
## BFS
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
