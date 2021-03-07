
### 冒泡排序
![](https://www.runoob.com/wp-content/uploads/2019/03/bubbleSort.gif)

+ 从0到i,j-i
+ 相邻相比较
+ 5行成冒泡

```c++
#include<iostream>
template<typename T>
void bubble_sort(T arr[],int len){
    for(int i=0;i<len-1;i++){
        for(int j=0;j<len-1-i;j++>){
            if(arr[j]>arr[j+1])
                swap(arr[j],arr[j+1]);
        }
    }
}
```

### 选择排序
![](https://www.runoob.com/wp-content/uploads/2019/03/selectionSort.gif)
+ 选择排序0到n,j是i,分左右
```c++
template<typename T>
void select_sort(T arr[],int len){
    int min_index;
    for(int i=0;i<len-1;i++){
        min_index=i;
        for(int j=i;j<len;j++){
            min_index=arr[min_index]>arr[j]?j:min_index;
        }
        swap(arr[i],arr[min_index]);
    }
}
```

### 插入排序
![](https://www.runoob.com/wp-content/uploads/2019/03/insertionSort.gif)
```c++
+ 反向比较交换位
template <typename T>
void insert_sort(vector<int> list){
    int temp;
    for(int i=0;i<list.size();i++){
        temp=list[i];
        for(int j=i-1;j>=0;j--){
           if(list[j]>temp){
               list[j+1]=list[j];
               list[j]=temp;
           }else{
               break;
           }
        }
    }
}
```



