```cpp
vector<int> topological_sort(){
    queue<int> q;
    //if q is empty -> impossible
    //if q's size >= 2 -> more than one case
    vector<int> ans; //result of topological-sort
    for(int i=0; i<N; i++){
        if(inDegree[i] == 0) {
            q.push(i);
        }
    }
    
    for(int i=0; i<N; i++){
        int curr = q.front();
        q.pop();
        ans.push_back(curr);
        for(int g : G[curr]){
            if(--inDegree[g] == 0) q.push(g);
        }
    }
    return ans;
}
```
O(ElgE)
