### 网页结构
+ header
+ container
    + 总共分类  #todo
    + 文章
    + 列表
+ tail

### 流程
+ ready() 是入口
+ 注册 .post_class 点击
+ 注册 .post_tag 点击
+ 注册 .ti 点击
+ 注册 .previous/ .next点击
+ load_mainpage()

### todo
+ 如何实现按时间排序:https://api.github.com/repos/CXianRen/CXianRen.github.io/commits?path=post/LeetCode100-13_Algorithm_LeetCode_Mar-02-2021.md&page=1&per_page=1

+ 最大访问限制问题

+ 增加总共分类
+ 最大显示数

### load_mainpage
+ 请求template/mainpage.html
+ cb: load_all_post_info -> main_page_render(插入一个post)

### load_all_post_info
+ get:https://api.github.com/repos/CXianRen/CXianRen.github.io/contents/post/

### references
+ https://segmentfault.com/a/1190000015144126


### Q & A
Q: cannot access file from local : 
A: add "--allow-access-file-from-files", can not work in Chrome but edge

Q: get回调函数传自定义参数
A: 匿名函数的方式

Q: win10 vscode 快捷对齐 
A: alt+shift+f

Q: 如何根据时间排序

PS: TOKEN不能出现在代码中, github会自动检测,所以要拆开



