```cpp
int uf[1000]; // <- memset(uf, -1, sizeof(uf)); 등의 연산을 사용해 음수로 초기화 필요

// 경로 압축을 하면서 부모를 find
int find(int a){
    if(uf[a] < 0) return a;
    uf[a] = find(uf[a]);
    return uf[a];
}

void merge(int a, int b){
    a = find(a);
    b = find(b);
    if(a == b) return;
    uf[a] += uf[b]; //<- uf가 음수일 때, -|uf|를 집합의 크기로 봐도 무방, 합치는 경우에는 둘의 크기를 더해줌
    uf[b] = a;
}
```

참고: N을 집합의 크기, M을 연산의 횟수라 할 때, 시간복잡도는 O(Mlog*N) -> O(M)이라 봐도 무방.
집합의 크기를 알고싶을 때 uf의 값을 가져와 사용 가능 (음수일 경우)
