### 题目:
```md
编写一个函数来查找字符串数组中的最长公共前缀。
如果不存在公共前缀，返回空字符串 ""。
```

### 解
```c++
//没什么好的解法,硬算就是了
//y轴扫描法
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size()==0|| strs[0].size()==0)return "";
        int finish=1,index=0;
        char compared;
        while(finish){
            compared=strs[0][index];
            for(string str:strs){
                if(index>=str.size()||str[index]!=compared){
                    finish=0;
                    break;
                }   
            }
            index++;
        }
        return strs[0].substr(0,index-1);
    }
};
```


### 思考:
> revers 反转字符串









