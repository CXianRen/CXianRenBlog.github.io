
### 深度优先搜索算法
![](https://www.runoob.com/wp-content/uploads/2020/10/deep-01.png)

+ 一标
+ 二for
+ 三递归
```c++

void dfs(int v){

    visited[v] = true; // 标记
    id[v] = ccount;   
    for( int i: G.adj(v) ){ //遍历同级别
        if( !visited[i] )  //向下找
            dfs(i);
    }
}
```

### 广度优先算法
+（1）使用一个辅助队列 q，首先将顶点 v 入队，将其标记为已访问，然后循环检测队列是否为空。
+（2）如果队列不为空，则取出队列第一个元素，并将与该元素相关联的所有未被访问的节点入队，将这些节点标记为已访问。
+（3）如果队列为空，则说明已经按照广度优先遍历了所有的节点。

```c++
+ 入队
+ 二while
+ 三for

```


### 实战题目-简单难度 
+ [leetcode原题](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)
```
输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。
例如：
给定二叉树 [3,9,20,null,null,15,7]，

    3
   / \
  9  20
    /  \
   15   7
返回它的最大深度 3 。

```

```c++
// dfs
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int dfs(TreeNode* root,int depth){
        //mark
        depth++;
        int l=0,r=0;
        //for
        if(root->left !=NULL){
            //dfs
            l=dfs(root->left,depth);
        }
        if(root->right !=NULL){
            r=dfs(root->right,depth);
        }
        return max(depth,max(l,r));
    }

    int maxDepth(TreeNode* root) {
        if(root==NULL) return 0;
        return dfs(root,0);
    }
};
```c++
//bfs
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    queue<TreeNode*> que;
    int max_depth=0;
    void bfs(queue<TreeNode*>& que){
        while(!que.empty()){
            int size=que.size();
            for(int i=0;i<size;i++){
                TreeNode* temp=que.front();que.pop();
                if(temp!=NULL && (temp->left!=NULL || temp->right !=NULL)){     
                    que.push(temp->left);
                    que.push(temp->right);
                }
            }
            max_depth++;
        }
    }

    int maxDepth(TreeNode* root) {
        if(root==NULL) return 0;
        que.push(root);
        bfs(que);
        return max_depth;
    }
};
```





