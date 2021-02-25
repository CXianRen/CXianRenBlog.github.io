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
```


### 思考:
>









