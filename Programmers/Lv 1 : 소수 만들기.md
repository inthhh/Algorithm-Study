// comments : 예전에 풀었던 문제 복습

### **문제 설명**

주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- nums에 들어있는 숫자의 개수는 3개 이상 50개 이하입니다.
- nums의 각 원소는 1 이상 1,000 이하의 자연수이며, 중복된 숫자가 들어있지 않습니다.

```
#include <vector>
#include <iostream>
using namespace std;


int solution(vector<int> nums) {
    int answer = 0;
    int n[100000] = { 0, };
    int c = 0;

    for (int i = 0; i < nums.size() - 2; i++) {
        for (int j = i + 1; j < nums.size() - 1; j++) {
            for (int k = j + 1; k < nums.size(); k++) {
                n[c] = nums[i] + nums[j] + nums[k];
                c++;
            }
        }
    }

    for (int i = 0; i < c - 1; i++) {
        for (int cnt = 2; cnt <= n[i]; cnt++) {
            if (n[i] % cnt == 0) {
                if (cnt == n[i]) {
                    answer++;
                }
                break;
            }
        }
    }
    return answer;
}
```
