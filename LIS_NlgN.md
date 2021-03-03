```cpp
void LIS() {
    int N;
    vector<int> ans;
    vector<pair<int, int>> records;
	cin >> N;
    ans.push_back(-1);
    for(int i=0, val; i<N; i++){
        cin >> val;
        if(ans[ans.size() - 1] < val) {
			records.emplace_back(ans.size(), val);
			ans.push_back(val);
		}	
        else{
			int idx = lower_bound(ans.begin(), ans.end(), val) - ans.begin();
            ans[idx] = val;
			records.emplace_back(idx, val);
        }
    }
    cout << ans.size() - 1 << '\n'; //length of LIS
	
	//backtracking
	int start = ans.size() - 1;
	stack<int> st;
	for(int i=records.size() - 1; i>=0; i--){
		if(records[i].first == start){
			st.push(records[i].second);
			start--;
		}
		if(start == -1) break;
	}
	while(!st.empty()){
		cout << st.top() << ' ';
		st.pop();
	}
}
```
