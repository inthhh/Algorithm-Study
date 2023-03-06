https://xxilliant.tistory.com/111
```
#include <string>
#include <vector>
#include <set>
using namespace std;

int solution(int N, int number) {
    int answer = -1;
    set<int> dp[8];
    
    int tmp=0;
    for(int i=0; i<8; ++i){
        tmp = tmp*10 + N;
        dp[i].insert(tmp);
    }
    
    for(int i=1; i<8; ++i){
        for(int j=0; j<i; ++j){
            for(int a : dp[j]){
                for(int b : dp[i-j-1]){
                    dp[i].insert(a+b);
                    dp[i].insert(a-b);
                    dp[i].insert(a*b);
                    if(b>0) dp[i].insert(a/b);
                }
            }
        }
    }
    
    for(int i=0; i<8; ++i){
        if(dp[i].count(number)){
            answer = i+1;
            break;
        }
    }
    
    return answer;
}
```
