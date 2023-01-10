- 대문자를 소문자로 바꾸되, 0번째나 단어 맨 앞의 대문자는 그대로 두어야 함.
- 모든 예외사항 고려하기!

```cpp
string solution(string s) {
    for(int i=0; i<s.length(); ++i){
        if(s[i]==' ') continue;
        if('z'>=s[i] && s[i]>='a'){
            if(i==0) s[i]-=32;
            if(s[i-1]==' ') s[i]-=32; // 대문자로 바꾸기
            continue;
        }
        if('Z'>=s[i] && s[i]>='A'){
            if(i==0) continue;
            if(s[i-1]!=' ') s[i]+=32; // 소문자로 바꾸기
        }
    }
    return s;
}
```
