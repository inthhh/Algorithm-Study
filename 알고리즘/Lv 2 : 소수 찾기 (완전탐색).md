https://xxilliant.tistory.com/106
```
#include <string>
#include <vector>
#include <algorithm>
#include <set>
#include <cmath>
using namespace std;

bool isPrime(int n){
    if(n<2) return false;
    for(int i=2; i<=sqrt(n); ++i){ // 소수 확인
        if(n%i == 0) return false;
    }
    return true;
}

int solution(string numbers) {
    int answer = 0;
    int n=0;
    set<int> s;
    sort(numbers.begin(), numbers.end());
    do{
        for(int i=0; i<numbers.length(); ++i){
            n = stoi(numbers.substr(0,i+1));
            if(isPrime(n)) s.insert(n);
        }
    } while(next_permutation(numbers.begin(), numbers.end()));
    answer = s.size();
    return answer;
}
```
