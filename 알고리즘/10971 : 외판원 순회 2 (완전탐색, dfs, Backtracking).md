https://xxilliant.tistory.com/116
```
#include <iostream>
#include <algorithm>
#include <climits>
using namespace std;

int n;
int w[10][10] = {0};
int visited[10] = {0};
int answer = INT_MAX;

void travel(int start, int now, int cnt, int sum){
    if(cnt == n){
        if(w[now][start] == 0) return; // 마지막 마을에서 출발지로 못 돌아갈때
        if(answer > sum + w[now][start]) answer=sum+w[now][start]; // 최솟값 대체
        return;
    }

    for (int i = 0; i < n; ++i){
        if(visited[i]==1 || w[now][i]==0) continue; // 마을방문 or 길없을때
        visited[i] = 1;
        travel(start, i, cnt + 1, sum + w[now][i]);
        visited[i] = 0; // 탐색 종료 후 다른경로로 탐색을 위해 되돌려놓기
    }
}

int main(){
    ios::sync_with_stdio(false);
    cin.tie(0);
    cout.tie(0);

    cin >> n;
    for (int i = 0; i < n; ++i){
        for (int j = 0; j < n; ++j){
            cin >> w[i][j];
        }
    }

    for (int i = 0; i < n; ++i){
        visited[i] = 1;
        travel(i, i, 1, 0);
        visited[i] = 0; // 다음 반복을 위해 되돌려놓기
    }
    cout << answer;
}
```
