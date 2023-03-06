https://xxilliant.tistory.com/115

```
#include <iostream>
using namespace std;

int n;
int line[15] = {0};
int answer = 0;

bool canGo(int x){
    for (int i = 0; i < x; ++i){
        if(line[x] == line[i]) return false; // y값이 같다?(같은 열이다?) false
        if(abs(line[x]-line[i]) == x-i) return false; // 대각선 라인이다? false
    }
    return true;
}

void queen(int x){
    if(x==n) {
        answer++;
    }
    else{
        for (int i = 0; i < n; ++i){
            line[x] = i; // x행의 i번째 열에 퀸 놓기
            if(canGo(x)) queen(x + 1);
        }
    }
}

int main(){
    cin >> n;
    queen(0);
    cout << answer;
    return 0;
}
