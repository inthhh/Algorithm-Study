블로그 : https://xxilliant.tistory.com/102

```
#include <string>
#include <vector>
#include <queue>
#include <algorithm>
using namespace std;

int solution(vector<int> priorities, int location) {
    int answer = 0;
    queue<int> q;
    int ps = priorities.size();
    for(int i=0; i<ps; ++i){
        q.push(priorities[i]);
    }
    sort(priorities.begin(), priorities.end());
    int maxe=priorities[ps-1];
    int lo = location;
    while(!q.empty()){
        int tmp=q.front();
        
        if(tmp < maxe) {
            q.pop();
            q.push(tmp);
            if(lo>0) lo--;
            else lo=q.size()-1;
        }
        else{
            answer++;
            priorities.erase(priorities.begin()+priorities.size()-1);
            maxe=priorities[priorities.size()-1];
            q.pop();
            if(lo>0) lo--;
            else break;
        }
    }
    return answer;
}
```
