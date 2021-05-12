```cpp
vector<int> Bellman_Ford(int src) {
	vector<int> dist(N, INF);
	dist[src] = 0;
	
	int update = N - 1;

	//update
	while(update--){
		for (int i = 0; i < N; i++) {
			if (dist[i] != INF) {
				for (const auto& g : G[i]) {
					dist[g.first] = min(dist[g.first], dist[i] + g.second);
				}
			}
		}
	}

	//check negative cycle
	for (int i = 0; i < N; i++) {
		if (dist[i] != INF) {
			for (const auto& g : G[i]) {
				if (dist[g.first] > dist[i] + g.second) {
					cout << "negative!";
					exit(0);
				}
			}
		}
	}

	return dist;
}
```
