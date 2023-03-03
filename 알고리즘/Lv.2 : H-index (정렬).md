https://xxilliant.tistory.com/108
```
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> citations) {
    int answer = 0;
    int cnt=0;
    sort(citations.begin(), citations.end());
    // for(int h=0; h<citations.size(); ++h){
    for(int h=0; h<10001; ++h){
        for(int i=0; i<citations.size(); ++i){
            if(citations[i] >= h) cnt++;
        }
        if(cnt < h) {
            answer = h-1;
            break;
        }
        cnt=0;
    }
    return answer;
}
```
