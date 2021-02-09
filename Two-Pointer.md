```cpp
int TwoPointer(int N, int M, int arr[]){
    int l=0, r=0, sum = 0, cnt = 0;
    while(true){
        if(sum >= M) sum -= arr[l++];
        else if(r == N) break;
        else if(sum < M) sum += arr[r++];
        if(sum == M) cnt++;
    }

	return cnt;
}

```
