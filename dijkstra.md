```cpp
vector<int> dijkstra(int src){
    vector<int> dist(N+1, INF);
    priority_queue<pair<int, int>> pq;
    previous.assign(N+1, -1);
    dist[src] = 0;
    pq.push({0, src});

    while(!pq.empty()){
        int cost = -pq.top().first, curr = pq.top().second;
        pq.pop();
        if(dist[curr] < cost) continue;
        for(auto g : G[curr]){
            int next = g.first, nextDist = cost + g.second;
            if(dist[next] > nextDist){
                dist[next] = nextDist;
                pq.push({-nextDist, next});
                previous[next] = curr;
            }
        }
    }
    return dist;
}
```

참고: O(|E|lg|V|)의 시간복잡도로 **한 정점** 에서 출발해 다른 모든 정점까지의 최단거리를 구해줌
previous 배열은 최소 비용을 찾는데 사용한 간선의 정보를 저장
ex) previous[u] = v -> u - v 를 연결하는 간선을 사용
