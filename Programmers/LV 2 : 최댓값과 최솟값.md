**10:54 pm**

- int형 벡터….이 좋은걸 쓸 생각을 왜 못했을까
- 공백이 나오기 전까지 문자열을 쌓아놨다가, 공백이 나오면 쌓아놨던 문자열을 int로 바꿔서 벡터에 집어넣기.
- 정렬 후 최솟값 & 최댓값 형식에 맞게 리턴

```cpp
string solution(string s) {
    string answer = "";
    string number = "";
    vector<int> v;
    for(int i=0; i<s.length(); ++i){
        if(s[i]!=' ') {
            number += s[i];
        }
        else {
            v.push_back(stoi(number));
            number = "";
        }
    }
    v.push_back(stoi(number));
    sort(v.begin(), v.end());
    answer += to_string(v[0]);
    answer += " ";
    answer += to_string(v[v.size()-1]);
    return answer;
}
```

**10:33 pm**

- 여러자릿수, 음수도 TC에 넣어서 실행 후 정상작동하는 거 확인하고 제출했는데도 테스트 7, 11, 12 실패가 뜬다

```cpp
string solution(string s) {
    int min, max;
    
    for(int i=0; i<s.length(); ++i){
        if(s[i]==' ') continue;
        string num = "";
        int number=0;
        
        if(s[i]=='-'){
            i++;
            num += s[i];
            while(1){
                if(s[i+1]!=' ') {
                    num+=s[i+1];
                    i++;
                }
                else break;
            }
            number = (-1)*(stoi(num));
            if(i==1) {
                min = number;
                max = number;
            }
            if(min > number) min=number;
            if(max < number) max=number;
        }
        else{
            num += s[i];
            
            while(1){
                if(s[i+1]!=' ') {
                    num+=s[i+1];
                    i++;
                }
                else break;
            }
            
            number = stoi(num);
            if(i==1) {
                min = number;
                max = number;
            }
            if(min > number) min=number;
            if(max < number) max=number;
        }
    }
    string answer = to_string(min);
    answer += " ";
    answer += to_string(max);
    return answer;
}
```

