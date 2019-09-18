---
title: 搭建hexo博客
date: 2019-05-30 12:56:30
categories: hexo
tags: [hexo, web]
toc: true
---
很久之前使用GitPage+jelly搭建过博客，后来由于种种原因停更，现在搭建了一个新的博客代表新的开始吧，加油~
<!-- more -->



# 一 准备账号
注册一个[github](https://github.com)账号,然后新建一个名为*用户名.github.io(如:hahaya.github.io)*的仓库

# 二 Hexo安装
1.安装git,然后设置git信息,最后生成ssh密钥文件,

```shell
    brew install git
    git config --global user.name "你的GitHub用户名"
    git config --global user.email "你的GitHub注册邮箱"
    ssh-keygen -t rsa -C "你的GitHub注册邮箱"(直接三个回车即可，默认不需要设置密码)
```

打开Settings->SSH and GPG keys 页面，新建new SSH Keym,找到生成的.ssh的文件夹中的id_rsa.pub密钥，将内容全部复制
![add ssh key](https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/my_blog/add_ssh_key.png)

Title为标题，任意填即可，将刚刚复制的id_rsa.pub内容粘贴进去，最后点击Add SSH key。
在终端中检测GitHub公钥设置是否成功，输入 ssh git@github.com ：
![test ssh](https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/my_blog/test_ssh.jpg)
如上则说明成功

# 三.安装node.js
[https://nodejs.org/en/download/](https://nodejs.org/en/download/ "Node.js下载地址") 下载后进行安装m,在终端终输入npm -v检测是否安装成功
![test Node.js]( https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/my_blog/test_node.jpg)
如上显示Node.js版本则说明成功

# 四、 安装Hexo
```shell
    mkdir my_blog
    cd my_blog
    npm install hexo 
    hexo init
    sudo npm install -g hexo
    sudo npm install hexo --save
    npm install hexo-deployer-git --save
    cd my_blog
    hexo init
```
修改_config.yml 最后面添加

    deploy:
      type: git
      repository: git@github.com:hahayacracker/hahayacracker.github.io.git (hahayacracker修改成自己的用户名)
      branch: master

修改完成后我们就可以推送到git了
```shell
    hexo clean
    hexo g
    hexo d
```
    
# 五 绑定阿里云域名
ping自己的Github Page得到ip
![ping](https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/my_blog/ping.jpg)
在阿里云控制台中点击解析，添加如下两条记录，保存后等待几分钟生效
![阿里云](https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/my_blog/aliyun.jpg)
