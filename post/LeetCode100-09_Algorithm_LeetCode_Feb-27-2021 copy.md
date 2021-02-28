### 题目:
```md
请你来实现一个 myAtoi(string s) 函数，使其能将字符串转换成一个 32 位有符号整数（类似 C/C++ 中的 atoi 函数）。

函数 myAtoi(string s) 的算法如下：

读入字符串并丢弃无用的前导空格
检查下一个字符（假设还未到字符末尾）为正还是负号，读取该字符（如果有）。 确定最终结果是负数还是正数。 如果两者都不存在，则假定结果为正。
读入下一个字符，直到到达下一个非数字字符或到达输入的结尾。字符串的其余部分将被忽略。
将前面步骤读入的这些数字转换为整数（即，"123" -> 123， "0032" -> 32）。如果没有读入数字，则整数为 0 。必要时更改符号（从步骤 2 开始）。
如果整数数超过 32 位有符号整数范围 [−231,  231 − 1] ，需要截断这个整数，使其保持在这个范围内。具体来说，小于 −231 的整数应该被固定为 −231 ，大于 231 − 1 的整数应该被固定为 231 − 1 。
返回整数作为最终结果。
注意：

本题中的空白字符只包括空格字符 ' ' 。
除前导空格或数字后的其余字符串外，请勿忽略 任何其他字符。
```

### 解
```c++
class Solution {
public:
    // ' ' - 0 1 2 3 e 5 6 7 8 9 
    //   0x30             0x39
    int myAtoi(string s) {
        int flag=0;
        long res=0;
        for(int i=0;i<s.size();i++){
            switch(s[i]){
                case ' ': {
                    if(flag!=0)i=s.size();
                }break;
                case '-':{
                    if(flag!=0)i=s.size();
                    else
                        flag=-1;
                }break;
                case '+':{
                    if(flag!=0)i=s.size();
                    else
                        flag=1;
                }break;
                default:{
                    if(s[i]-0x30>=0 && s[i]-0x30<=9){
                        
                        res=res*10+(s[i]-0x30);
                        if(res>=INT_MAX)i=s.size();
                        if(flag==0)flag=1;
                    }else{
                        i=s.size();
                    }
                }break;
            }
        }
        res= flag>=0?res:-res;
        res= res>INT_MAX?INT_MAX:res;
        res= res<INT_MIN?INT_MIN:res;
        return res;
    }
};
// res 4ms 6.9M 
```
```c++
// 状态机分析
/*
            0   1    2   3  4
            +   -   0-9 ' ' a
    0   +   e   e    2   e  e
    1   -   e   e    2   e  e
    2   0-9 e   e    2   e  e
    3   ' ' 0   1    2   3  4
    4   a   4   4    4   3  4
*/
#define e 5
class Solution {
public:
    char map[e][e]={
        {e,e,2,e,e},
        {e,e,2,e,e},
        {e,e,2,e,e},
        {0,1,2,3,4},
        {4,4,4,4,4}
    };
    int myAtoi(string s) {
        int status=3,flag=1;
        long long res=0;
        for(int i=0;i<s.size();i++){
            switch(s[i]){
                case '+':status=map[status][0];break;
                // "123-" "-5-"
                case '-':flag=status!=2?-1:flag;status=map[status][1];break;
                case ' ':status=map[status][3];break;
                default:{
                    if(s[i]-0x30>=0 &&s[i]-0x30<=9){
                        status=map[status][2];break;
                    }
                    else {
                        status=map[status][4];break;
                    }
                }
            }
            if(status==2){
                // "20000000000000000000"
                if(res>INT_MAX)break;
                res=res*10+s[i]-0x30;
            }
            if(status==e){
                break;
            }
        } 
        res= flag*res;
        res= res>INT_MAX?INT_MAX:res;
        res= res<INT_MIN?INT_MIN:res;
        return res;
    }
};
//res 4ms 6.9M 没快多少
```

### 思考:
> 对于一些常量： INT_MAX INT_MIN









