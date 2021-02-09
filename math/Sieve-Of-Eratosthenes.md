```cpp
vector<int> getPrime(int MAX){
	vector<bool> isPrime(MAX + 1, true);
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
	return prime;
}
```
참고: O(nlglgn)의 시간복잡도로 2~(MAX-1) 사이의 소수들을 모두 구해줌
