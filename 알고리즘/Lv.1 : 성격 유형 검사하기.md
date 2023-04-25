https://xxilliant.tistory.com/151
```
#include <string>
#include <vector>
#include <map>
using namespace std;

string solution(vector<string> survey, vector<int> choices) {
    string answer = "";
    map<char,int> mbti;
    mbti['R']=0; mbti['T']=0;
    mbti['C']=0; mbti['F']=0;
    mbti['J']=0; mbti['M']=0;
    mbti['A']=0; mbti['N']=0;
    // [0]:비동의 3점, [1]:동의 3점
    for(int i=0; i<survey.size();++i){
        int ch = choices[i];
        if(ch==4) continue;
        if(ch<4){ // 비동의
            char c = survey[i][0];
            mbti[c] += (4-ch);
        }
        if(ch>4){ // 동의
            char c = survey[i][1];
            mbti[c] += (ch-4);
        }
    }
    if(mbti['R']>=mbti['T']) answer+="R";
    else answer+="T";
    if(mbti['C']>=mbti['F']) answer+="C";
    else answer+="F";
    if(mbti['J']>=mbti['M']) answer+="J";
    else answer+="M";
    if(mbti['A']>=mbti['N']) answer+="A";
    else answer+="N";
    return answer;
}
