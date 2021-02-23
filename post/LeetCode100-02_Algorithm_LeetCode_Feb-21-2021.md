### 题目:
+ 给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 的那 两个 整数，并返回它们的数组下标。你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

### 解
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int a;
        vector<int> res;
        for(int i=0;i<=nums.size()-1;i++){
            a=nums[i];
            for(int j=i+1;j<=nums.size()-1;j++){
                if(a+nums[j]==target){
                    res.push_back(i);
                    res.push_back(j);
                    return res;
                }
            }
        }
        return res;
    }
};
// res 8ms 8.7m 暴力解
```

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> t; // 0:值  1:下标
        vector<int> res(2,-1);
        for(int i=0;i<=nums.size()-1;i++){
            if(t.count(target-nums[i])){
                res[0]=i;
                res[1]=t[target-nums[i]];
                break;
            }
            t[nums[i]]=i;
        }
        return res;
    }
};
// res 4ms 8.7m  一遍hash
```

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        t={}
        for i in range(len(nums)):
            if((target-nums[i]) in t):
                return [t[target-nums[i]],i]
            else:
                t[nums[i]]=i
        return None
    # res 24ms 12.9m
```

### 思考:
> hash 快了许多,且内存没变大

