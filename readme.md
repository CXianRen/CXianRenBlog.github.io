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
+ 如何实现按时间排序？
+ 最大访问限制问题
+ 增加总共分类
+ 最大显示数

### load_mainpage
+ 请求template/mainpage.html
+ cb: load_all_post_info -> main_page_render(插入一个post)

### load_all_post_info
+ get:https://api.github.com/repos/CXianRen/CXianRen.github.io/contents/post/



