### 题目:
+ 将一个给定字符串 s 根据给定的行数 numRows ，以从上往下、从左到右进行 Z 字形排列。

### 解
```c++
//第一思路,直接行排列

class Solution {
public:
    string convert(string s, int numRows) {
        string res(s.size(),'\0'); //不支持从char 数组构建
        int res_i=0;
        int groups=0;
        int nums_in_group=numRows*2-2;
        if(numRows<2){             // 0和1 的边界问题
            nums_in_group=1;
        }
        groups=s.size()/nums_in_group;
        if(s.size()%nums_in_group)groups++; //尾部边界问题

        for(int i=0;i<numRows;i++){
            for(int j=0;j<groups;j++){
                //头行&&尾行
                if((i==0 || i==numRows-1) && j*nums_in_group+i<s.size()){
                    res[res_i]=s[j*nums_in_group+i];
                    res_i++;
                }else{
                    //中间行
                    if(j*nums_in_group+i<s.size()){
                        res[res_i]=s[j*nums_in_group+i];
                        res_i++;
                    }
                    if(j*nums_in_group+nums_in_group-i<s.size()){
                        res[res_i]=s[j*nums_in_group+nums_in_group-i];
                        res_i++;
                    }
                }
            }
        }
        return res;
    }
};
// 12 ms 7.9m
```
```c++
//优雅点的解法
class Solution {
public:
    string convert(string s, int numRows) {
        if(numRows==1)return s;

        string res; 
        int nums_in_group=numRows*2-2;
        int n=s.size();

        for(int i=0;i<numRows;i++){
            for(int j=0;j+i<n;j+=nums_in_group){
                    //头行&&尾行
                res+=s[j+i];
                    //中间行需要加一个
                if(i!=0 && i!=numRows-1 && j+nums_in_group-i<n)
                    res+=s[j+nums_in_group-i];
            }
        }
        return res;
    }
};
// 优化了==1的情况，直接返回，不用判断
// 使用偏移的思想,就不需要多一个变量了
// 中间的行只多一个，所以只要判断一次
// res 8ms 8Mb
```

### 思考:
>









