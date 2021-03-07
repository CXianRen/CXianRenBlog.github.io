### 题目:
```md
输入一个字符串，打印出该字符串中字符的所有排列。
你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。
示例:

输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]

```

### 解
```c++
class Solution {
public:

/*
      b - c
 a  < 
      c - b
      a - c
 b  <
      c - a
*/
    vector<string> res;

    void dfs(string s,int x){
        // mark
        if(x==s.size()-1){
            res.push_back(s);
            return ;
        } 
        // for
        set<int> st;
        for(int i=x;i<s.size();i++){
            //剪枝
            if(st.find(s[i])!=st.end())continue; 
            st.insert(s[i]);

            swap(s[x],s[i]); //每层深搜都固定一个位置,然后通过交换产生新的字符串给
            dfs(s,x+1);
            swap(s[x],s[i]);
        }
    }
    vector<string> permutation(string s) {
        dfs(s,0);
        return res;
    }
};
```

### 思考:
> inception 的面试题目,没做出来，虽说暴力解。
> c++ set find()成员：该函数返回一个迭代器，该迭代器指向在集合容器中搜索的元素。如果找不到该元素，则迭代器将指向集合中最后一个元素之后的位置









