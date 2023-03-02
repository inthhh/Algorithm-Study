https://xxilliant.tistory.com/104

```
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

int main(){
    int n;
    int k;
    cin >> n >> k;
    queue<int> q;
    vector<int> v;
    for (int i = 1; i <= n; ++i){
        q.push(i);
    }
    int cnt = 1;
    while (!q.empty()){
        int tmp = q.front();
        q.pop();
        if(cnt%k == 0){
            v.push_back(tmp);
        }
        else q.push(tmp);
        cnt++;
    }
    cout <<'<';
    for (int i = 0; i < n; ++i){
        if(i==n-1) cout << v[i] <<'>';
        else cout << v[i] << ", ";
    }
    
}
```
