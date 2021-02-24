### 题目:
+ 给你一个字符串 s，找到 s 中最长的回文子串。

### 解
```c++
// DP解法
class Solution {
public:
    string longestPalindrome(string s) {
        string res;
        char dp[s.size()][s.size()];
        //核心方程 P[i,j]=P[i+1,j-1]&&S[i]==S[j]
        //最小的单元长度是0,最长为n,所以从0-n开始
        for(int n=0;n<s.size();n++){
            //遍历所有的元素
            for(int i=0; (i+n)<s.size();i++){
                int j=i+n; //长度为n的字符串, 从i到 i+n
                //边界
                if(n==0){ //字符串间隔为0,即每个字符都是回文的
                    dp[i][j]=1;
                }else if(n==1){ //间隔为1，即相邻的两个字符
                    dp[i][j]=(s[i]==s[j]);
                }else{
                    //核心 判断i到i+n是不是回文
                    dp[i][j]=dp[i+1][j-1]&&s[i]==s[j];
                }
                if(dp[i][j]&&n+1>res.size()){
                    res=s.substr(i,n+1);
                }
                
            }
        }
        return res;
    }
};
// res 480ms 24Mb 
```

### 思考:
> DP的思考: 自定向下找出 递归式, 然后自底向下写, 从最小元素开始, 然后添加边界











