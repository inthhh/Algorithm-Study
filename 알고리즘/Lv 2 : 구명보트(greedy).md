https://xxilliant.tistory.com/105

```
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int solution(vector<int> people, int limit) {
    int answer = 0;
    int i=0;
    int j=people.size()-1;
    sort(people.begin(), people.end());
    while(i<=j){
        if(people[j]+people[i] <= limit){
            i++; j--;
            answer++;
        }
        else {
            j--;
            answer++;
        }
    }
    return answer;
}
```
