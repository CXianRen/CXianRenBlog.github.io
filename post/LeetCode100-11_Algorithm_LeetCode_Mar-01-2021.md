### 题目:
```md
罗马数字包含以下七种字符： I， V， X， L，C，D 和 M。

字符          数值
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。
```

### 解
```c++
class Solution {
public:
    /*
    1   2   3   4   5   6   7   8   9   10
    I   II  III IV  V  VI  VII VIII IX  X
    */
    char table[4][3]={
        {'I','V','X'}, 
        {'X','L','C'},
        {'C','D','M'},
        {'M',' ',' '}};
    string intToRoman(int num) {
        string res;
        int i=0,temp=0;
        while(num>0){
            temp=num%10;
            num/=10;
            // temp 转换
            switch(temp){
                case 1:
                case 2:
                case 3:
                    while(temp>0){
                        res+=table[i][0];
                        temp--;
                    }break;
                case 4: res=res+table[i][1]+table[i][0];break; // IV -> VI 
                case 5: res+=table[i][1];break;
                case 6: 
                case 7:
                case 8:
                    while(temp>5){
                        res+=table[i][0];
                        temp--;
                    }
                    res+=table[i][1];break;
                case 9: res=res+table[i][2]+table[i][0];break;
            };
            i++;
            i%=4;
        }
        reverse(res.begin(),res.end());
        return res;
    }
};
```
```c++
//贪心算法
struct RomanInt{
    int value;
    string key;
};

class Solution {
public:
    /*
        1   5   4   9   10  40  50  90  100 400 500 900 1000
        I   V   IV  IX  X   XL  L   XC  C   CD   D   CM  M
    */
    RomanInt map[13]={
        {1000,"M"},{900,"CM"},{500,"D"},{400,"CD"},
        {100,"C"},{90,"XC"},{50,"L"},{40,"XL"},
        {10,"X"},{9,"IX"},{5,"V"},{4,"IV"},{1,"I"}};

    string intToRoman(int num) {
        int count=0;
        string res;
        for(RomanInt i : map){
            count=num/i.value;
            num%=i.value;
            for(int j=0;j<count;j++){
                res+=i.key;
            }
        }
        return res;
    }
};

```

### 思考:
> revers 反转字符串









