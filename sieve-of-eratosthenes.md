```cpp
const int MAX = 1000001;
vector<bool> isPrime(MAX, true);
vector<int> prime(1, 2);
isPrime[0] = false;
isPrime[1] = false;
for(int i=4; i<=MAX; i+=2) isPrime[i] = false;
for(int i=3; i<=MAX; i++){
    if(isPrime[i]){
        prime.push_back(i);
        for(int j=i*i; j<=MAX && 1ll * i * i <= MAX; j+=2*i)
            isPrime[j] = false;
    }
}
```
참고: *O(nlglgn)*의 시간복잡도로 2~(MAX-1) 사이의 소수들을 모두 구해줌
