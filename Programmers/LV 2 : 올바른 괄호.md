- **내 풀이** : (가 들어오면 +1, )가 들어오면 -1을 해서 마지막 값이 0이면 true.
- 처음에 )가 들어오거나 ) 갯수가 더 많아지면 중간에 false 리턴으로 컷.

```cpp
bool solution(string s) {
    int cnt = 0;
    for(auto i : s){
        if(i=='(') cnt ++;
        if(i==')'){
            if(cnt > 0) cnt --;
            else return false;
        }
    }
    if(cnt==0) return true;
    return false;
}
```

- 다른사람의 풀이 : stack을 사용하여 아래와 같이 해결가능.
- (일때 push, )일때 pop

```cpp
bool solution(string s) {
    bool answer = true;
    stack <char> st;
    for(int i =0; i < s.size(); i ++){
        if(s[i]== '(') st.push(s[i]);
        else if(s[i]==')'){
            if(st.empty() || st.top()!='('){
                answer = false; break;
            }
            st.pop();
        }
    }
    if(!st.empty()) answer =false;
    return answer;
}
```

.
