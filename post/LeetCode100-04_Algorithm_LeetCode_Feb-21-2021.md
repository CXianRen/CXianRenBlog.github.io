### 题目:
+ 给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

### 解
```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int res=0,tres=0;
        const char* str=s.c_str();
        char alpha[128];
        for(int i=0;i<s.length();i++){ 
            for (int j=0;j<128;j++)alpha[j]=-1;
            tres=1;
            alpha[str[i]]=1;
            for(int j=i+1;j<s.length();j++){
                if(alpha[str[j]]==1){
                    break;
                }
                tres++;
                alpha[str[j]]=1;  
            }
            if(tres>res)res=tres;
        } 
    return res;
    }
};
// 20ms  6.3M
```

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int res=0,start=0,end=0;
        const char* str=s.c_str();
        int alpha[128]={0};
        alpha[*(str+start)]=1;
        while(*(str+end)!=0){
            res=res>(end-start+1)?res:(end-start+1);
            end++;
            while(alpha[(int)*(str+end)]!=0){
                alpha[*(str+start)]=0;
                start++;
            }
            alpha[(int)*(str+end)]=1;
        }
    return res;
    }
};
// 4ms 6.3M 
// 表+划窗, 表的本质也是hash, 通过第2个while来降低要重复处理的字符串
```

### 思考:












