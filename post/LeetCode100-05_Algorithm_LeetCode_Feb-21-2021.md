### 题目:
+ 给定两个大小为 m 和 n 的正序（从小到大）数组 nums1 和 nums2.请你找出并返回这两个正序数组的中位数。

+ 进阶：你能设计一个时间复杂度为 O(log (m+n)) 的算法解决此问题吗？

### 解
```c++
class Solution {
public:
    //log级别的复杂度,基本上就是二分思想
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        //2个序列中找第K个数
        //理论上最优状态是每边前K/2个
        /*
            A[k/2-1] B[k/2-1]   ?为什么时k/2-1个数 因为输入的是第K个 第K/2 下标就是K/2-1
            (1)A[k/2-1] > B[k/2-1] ->  最多有k/2-1(减去A[k/2-1]本身)+k/2-1(减去B[k/2-1]本身)=k-2个数 < B[k/2-1]，则可以排除B的前k/2个数(0--[K/2-1])
            (2)A[k/2-1] <= B[k/2-1] ->  同理排除掉A的前k/2个数

        */
        int k=nums1.size()+nums2.size();
        if(k%2)
            return get(nums1,nums2,(k+1)/2);
        else
            return (get(nums1,nums2,k/2)+get(nums1,nums2,k/2+1))/2;
    }
    
    double get(vector<int>& nums1,vector<int> nums2, int k){
        int A,B,Ai=0,Bi=0,nAi,nBi;
        while(true){
            //边界
            if(Ai==nums1.size()){
                //A用完了，但是还没找到
                return nums2[Bi+k-1];
            }
            if(Bi==nums2.size()){
                //B用完了，但是还没找到
                return nums1[Ai+k-1];
            }
            if(k==1){
                return min(nums1[Ai],nums2[Bi]);
            }
            //正常
            nAi=nums1.size()-1>(k/2-1+Ai)?(k/2-1+Ai):nums1.size()-1;
            nBi=nums2.size()-1>(k/2-1+Bi)?(k/2-1+Bi):nums2.size()-1;
            A=nums1[nAi];
            B=nums2[nBi];
            if(A>B){
                //排除B的,更新k
                k-=nBi-Bi+1;
                Bi=nBi+1;    
            }else{
                //排除A的,更新k
                k-=nAi-Ai+1;
                Ai=nAi+1;
            }
        }
    }
};
```

### 思考:
+ [归并排序](https://www.runoob.com/w3cnote/merge-sort.html)












