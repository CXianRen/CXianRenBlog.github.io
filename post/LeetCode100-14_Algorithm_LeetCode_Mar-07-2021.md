### 题目:
```md
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。答案可以按 任意顺序 返回。
给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

```

### 解
```c++
/*
    算是dfs吧
    确定第一个字符
    进入下一层确定第二个字符
    ...
    最后一层确定整个字符串
    返回上一层,确定上一层的第二个可能
    ...
    
    example:
    digits="234"
    a -> d -> g
    a -> d -> h
    a -> d -> i
    a -> e -> g
    a -> e -> h
    ...
    c -> d -> g
    ...
    c -> f -> i

*/
class Solution {
public:
    
    vector<string> map{
        " ",    //0
        "!@#",  //1
        "abc",  //2
        "def",  //3
        "ghi",  //4
        "jkl",  //5
        "mno",  //6
        "pqrs", //7
        "tuv",  //8
        "wxyz", //9
    };
    vector<string> res;
    void dfs(string digits,string tres,int x){
        // mark
        if(x==digits.size()){
            res.push_back(tres);   //遍历到最后一个数字之后
            return;
        }
        // for
        for(int i=0;i<map[digits[x]-0x30].size();i++){ 
                //确定下一个字符
            dfs(digits,tres+map[digits[x]-0x30][i],x+1);
        }
    }
    
    vector<string> letterCombinations(string digits) {
        if(digits.size()==0)return res;
        dfs(digits,"",0);
        return res;
    }
};
```

### 思考:
> 与第13题(上一题)一样,且是简化版的。所以直接dfs既可以。不需要剪枝








