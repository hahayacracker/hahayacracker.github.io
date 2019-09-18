---
title: yilia加入prettify高亮插件
date: 2019-06-04 07:54:41
tags: [hexo]
---



1.禁用hexo默认高亮插件
打开主目录的_config.yml文件，将highlight插件禁用
```
highlight:
  enable: false
  line_number: false
  auto_detect: false
  tab_replace:
```

2.引用prettify高亮插件
2.1 下载插件
下载[prettify](https://raw.githubusercontent.com/google/code-prettify/master/distrib/prettify-small.zip)源码后解压，拷贝纸博客的source目录，我简历了一个新的plugins目录专门存放第三方插件（必须放在source目录下，这样生成静态文章时才能输出到public目录），此时文件目录为![prettify目录结构](https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/Her/prettify_src.jpg)
2.2 跳过渲染
因为prettify目录只是个插件，不需要hexo进行渲染否则会报错，所以我们需要跳过prettifys整个目录的渲染，打开主目录下的_config.yml并做如下修改
![](https://hahaya-1259297687.cos.ap-beijing.myqcloud.com/Her/skip_render.jpg)
3 引用插件
3.1 引入样式
打开yilia\layout\_partial\head.ejs文件。在其中引入样式
```
  <!--prettify代码高亮主题css引入-->
  <link href="/plugins/prettify/src/prettify.css" rel="stylesheet">
```
3.2 引入脚本
打开yilia\layout\_partial\after-footer.ejs文件。在其中引入样式

4 测试高亮
```
import sys

def test():
pass

if __name__=='__main__':
    test()
```

