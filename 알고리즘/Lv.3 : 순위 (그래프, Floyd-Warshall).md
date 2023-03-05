https://xxilliant.tistory.com/110
```
#include <string>
#include <vector>
using namespace std;

bool mat[101][101];

int solution(int n, vector<vector<int>> results) {
    int answer = 0;
    for(int i=0; i<results.size();i++){
        mat[results[i][0]][results[i][1]] = true;
    } // 매트릭스 그래프 만들기

    for(int k=1; k<=n;k++){
        for(int i=1; i<=n;i++){
            for(int j=1; j<=n; j++){
                if(mat[i][k] && mat[k][j]){ // i가 k를 이기고, k는 j를 이겼을 때
                    mat[i][j] =true; // i는 j를 이길 것임
                }
            }
        }
    }
    for(int i=1; i<=n;i++){
        int count =0;
        for(int j=1; j<=n;j++){
            if(mat[i][j] || mat[j][i]){ // 승부 횟수 카운트
                count++;
            }
        }
        if(count == n-1) answer++; // 승부가 n-1일때 순위 확정
    }
    return answer;
}
```
