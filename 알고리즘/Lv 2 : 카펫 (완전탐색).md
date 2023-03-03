https://xxilliant.tistory.com/107

```
#include <string>
#include <vector>
#include <cmath>
using namespace std;

vector<int> solution(int brown, int yellow) {
    vector<int> answer;
    for(int i=1; i<=sqrt(yellow); ++i){
        if(yellow%i == 0){
            int x = i; int y = yellow/i;
            if(brown == 2*x + 2*y + 4) {
                answer.push_back(y+2);
                answer.push_back(x+2);
            }
        }
    }
    return answer;
}
```
