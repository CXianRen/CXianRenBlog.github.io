### 题目:
```md
给你一个整数 x ，如果 x 是一个回文整数，返回 true ；否则，返回 false 。

回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。例如，121 是回文，而 123 不是。
```

### 解
```c++
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0)return false;
        long res=0,t=x;
        while(x!=0){
            res=res*10+x%10;
            x/=10;
        }
        return res<INT_MAX&&res==t?true:false;
    }
};
```

### 思考:
> 负数一定不是,回文数一定不会溢出,理论上可以只判断一半 如：1221  12=12.但是需要解决多少是一半的问题,这样子还是需要疯狂/10,不知道速度会不会快点。









