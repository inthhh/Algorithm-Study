https://xxilliant.tistory.com/150
```
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

vector<int> solution(string today, vector<string> terms, vector<string> privacies) {
    vector<int> answer;
    vector<char> termA; // 약관 종류
    vector<int> term1; // 약관 유효기간 달 수
    
    int todayY = stoi(today.substr(0,4));
    int todayM = stoi(today.substr(5,2));
    int todayD = stoi(today.substr(8,2));
    
    for(int i=0; i<terms.size();++i){ // 약관 종류와 기간 분리
        termA.push_back(terms[i][0]);
        terms[i].replace(0,2,"");
        term1.push_back(stoi(terms[i]));
    }
    
    for(int i=0; i<privacies.size(); ++i){
        char kindof=privacies[i][11];
        int pY = stoi(privacies[i].substr(0,4));
        int pM = stoi(privacies[i].substr(5,2));
        int pD = stoi(privacies[i].substr(8,2));
        
        int index = 0;
        int year = 0;
        int month = 0;
        for(int j=0; j<termA.size(); ++j){
            if(termA[j] == kindof) {
                index = j;
                break;
            }
        }
        year = term1[index]/12;
        month = term1[index]%12;
        year += pY;
        month += pM;
        if(month > 12){ // 24
            year += month/12; // +2
            month = month%12; // 0
        }
        if(month==0) month += pM;
        cout <<year<<" "<<month<<"\n";
        if(year < todayY) answer.push_back(i+1);
        else if(year == todayY){
            if(month< todayM) answer.push_back(i+1);
            else if(month==todayM){
                if(pD-1 < todayD) answer.push_back(i+1);
            }
        }
        
    }
    return answer;
}
