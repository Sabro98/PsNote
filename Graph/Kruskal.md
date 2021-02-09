```cpp
//UNION-FIND
int uf[100];

int find(int n) {
    if (uf[n] < 0) return n;
    return uf[n] = find(uf[n]);
}

bool merge(int a, int b) {
    a = find(a);
    b = find(b);
    if (a == b) return false;
    uf[b] = a;
    return true;
}
//
struct Edge {
    int u, v, w;

    Edge(int u, int v, int w) : u{u}, v{v}, w{w} {}

    Edge() : Edge(-1, -1, 0) {}

    bool operator<(const Edge &other) const { // 오름차순 정렬
        return w < other.w;
    }
};

int kruskal(vector<Edge> E) {
    sort(E.begin(), E.end());
    int result = 0, cnt = 0;
    for (int i = 0; i < E.size(); i++) {
        if (merge(E[i].u, E[i].w)){
            result += E[i].w;
            if(cnt == N - 1) break;
        }
    }
    return result; //value of MST
}
```
