https://xxilliant.tistory.com/109

```
#include <string>
#include <vector>
#include <queue>
#include <algorithm>
using namespace std;

int mat[20001][20001]={0};
int visited[20001]={0};
int answer[20001]={0};
int cnt=0;

bool canGo(int a, int i){
    if(visited[i]==1) return false;
    if(mat[a][i]==0) return false;
    return true;
}

void bfs(int n){
    queue<int> q;
    q.push(1);
    visited[1] = 1;
    answer[1] = 1;
    while(!q.empty()){
        int a = q.front();
        q.pop();
        for(int i=1; i<=20000; ++i){
            if(canGo(a,i)){
                visited[i] = 1;
                q.push(i);
                answer[i] = answer[a]+1;
            }
        }
    }
    sort(answer, answer+20001);
    int amax = answer[20000];
    for(int i=20000; i>=0; --i){
        if(answer[i] == amax) cnt++;
        else break;
    }
}

int solution(int n, vector<vector<int> > edge) {
    int ES = edge.size();
    for(int i=0; i<ES; ++i){
        mat[edge[i][0]][edge[i][1]] = 1;
        mat[edge[i][1]][edge[i][0]] = 1;
    }
    bfs(n);
    return cnt;
}
```
