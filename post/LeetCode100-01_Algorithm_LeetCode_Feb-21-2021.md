### 题目:
+ 给你一个字符串 S，请你删去其中的所有元音字母（ 'a'，'e'，'i'，'o'，'u'），并返回这个新字符串。

### 解
```python
class Solution(object):
    def removeVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        return re.sub(r"[aeiou]","",s)
    # 结果：28ms 12M
```
```python
    return "".join(i for i in s if i not in "aeiou")
    # 结果: 24ms 13M
```

```c++
class Solution {
public:
    string removeVowels(string s) {
        const char* t=s.c_str();
        char r[1024];
        int index=0;
        for(int i=0;i<s.length();i++){
            switch(t[i]){
                case 'a':
                case 'e':
                case 'i':
                case 'o':
                case 'u':break;
                default:{
                    r[index]=t[i];
                    index++;
                }
            }
        }
        r[index]='\0';
        return r;
    }
};
// 结果 0ms 6.3M
```
### 思考:
