https://xxilliant.tistory.com/128

```
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int main(){
    ios::sync_with_stdio(false);
    cin.tie(0); cout.tie(0);
    int t;
    int n;

    cin >> t;
    for (int i = 0; i < t; ++i){
        vector<int> dots;
        int dot;
        cin >> n;
        for (int j = 0; j < n;++j){
            cin >> dot;
            dots.push_back(dot);
        }
        sort(dots.begin(), dots.end());

        int cnt = 0;
        for (int m = 1; m < n-1; ++m){
            int left = 0;
            int right = n - 1;
            while(left<right){
                if(left==m || m==right) break;
                
                int l_to_m = dots[m] - dots[left];
                int m_to_r = dots[right] - dots[m];
                
                if(l_to_m == m_to_r) {
                    cnt++;
                    left++;
                }
                else if(l_to_m > m_to_r) left++;
                else right--;
            }
        }
        cout << cnt << "\n";
    }
}
