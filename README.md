# Ablog - Another Blog System By Abbey


## 说明
Ablog是通过Flask写的博客系统，由Abbey通过[YuBlog](https://github.com/Blackyukun/YuBlog)二开完成

对比原项目，Ablog主要做了以下改进：

1. 新增多用户系统
    - 用户可购买付费文章
    - 用户可修改密码
    - more...
2. 新增付费阅读功能
    - 通过[payjs.cn](https://payjs.cn/ref/KZVNLZ)对接微信支付
    - 通过购买积分的方式付费
    - 不同文章可设置不同的积分要求
3. 改进评论系统
    - 评论由**问答式**改为**盖楼式**显示；
    - 后台可直接回复评论
    - 用户必须注册才可评论
    - 普通用户评论需审批，管理员评论直接显示
4. 改进后台功能
    - 后台可设置网站更多的信息：域名、博客名、简介、统计代码等
    - 后台新增对接sm.ms图床
5. 改进缓存系统

...

因Abbey只是想找一个现成的Flask写的博客，再进行二开，会做很多的改进和功能，因此Abbey另开了一个repo


## 安装
### 写在安装前
1. 本博客基于Python3.7.4写的，因此2.7版本肯定运行不了，Python版本最好在3.5以上！
2. 本博客，数据库可选择：`MySQL`和`sqlite`两种方式，缓存方式可选择：`redis`和`sample`两种方式，其中`sample`是文件缓存，性能上比redis会差一些

### 一键安装
本博客提供一键安装脚本，适应：`Centos 7、Ubuntu 16+、Debian 8+`，安装方式：

1. 先安装`Git`
    - Ubuntu/Debian
```
apt-get update -y
apt-get upgrade -y
apt-get install git
```
    - Centos
```
yum install git
```

2. 下载源码
```
git clone https://github.com/abbeyokgo/ABlog.git
```

3. 切换到源码目录
```
cd ABlog
```

4. 运行一键安装脚本
```
bash install.sh
```
安装过程中，会要求输入：
    - 数据**储存**方式：`MySQL`或`sqlite`
        - 如果是`MySQL`，会继续要求输入：MySQL用户名、密码、数据库名。_ps. 请提前安装MySQL_
        - 如果是`sqlite`，会使用sqlite储存数据
    - 数据**缓存**方式：`redis`和`sample`
        - 如果是`redis`，则使用redis做缓存，请提前安装redis
        - 如果是`sample`，则使用文本做缓存，性能不如redis
    - 管理员账号、密码、简介
    - 网站名称、标题、协议、域名
    - 最后是payjs的商户号和密钥。如果没有payjs账号可跳过

5. 运行完之后根据提示访问即可

### 手动安装
动手能力强的可以参考一键安装脚本安装


## wordpress迁移脚本
**因不同的wordpress主题生成的文章格式不同，该脚本是基于dux主题生成的文章写的脚本，因此如果是其他主题生成的文章，可能不兼容**

### 脚本：`wp_to_blog.py`
本脚本会将wordpress的：标签、分类目录、评论、文章、友链、文章阅读次数等信息迁移过来

### 使用方法
1. 修改`wp_to_blog.py`配置：
    - `source_db`里面的是wordpress数据库的信息
    - `store_db`里面的是本博客数据库的信息
2. 运行脚本：
```
python wp_to_blog.py
```

## 预览
### 前端
![1.png](https://i.loli.net/2019/08/08/cvQZYT6ou7kEaJj.png)

### 后台
![2.png](https://i.loli.net/2019/08/08/yvqpJQOUaRCdlsW.png)
_ps. 别问我后台首页的图标干嘛的_

### 文章编辑
![3.png](https://i.loli.net/2019/08/08/AoXEYDnCmdbzH8K.png)

### 付费阅读功能
![4.png](https://i.loli.net/2019/08/08/26Wg5FMIXCsEn7T.png)


## Q&A

1. 如何修改收款码？
- 支付宝收款码路径：app/static/images/alipay.jpg
- 微信收款码路径：app/static/images/wechatpay.jpg

2. 如何修改头像？
可以在`后台-站点-编辑站点`编辑

更多问题请访问[https://www.abbeyok.com/archives/394](https://www.abbeyok.com/archives/394)并在评论区提问
