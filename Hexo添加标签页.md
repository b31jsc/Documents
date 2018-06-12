## Hexo添加标签页
### 0. 准备工作
* 操作系统: Ubuntu 18.04
* Hexo版本号: Hexo 3.7.1
  ```
  $ hexo version
  hexo: 3.7.1
  hexo-cli: 1.1.0
  os: Linux 4.15.0-22-generic linux x64
  http_parser: 2.8.0
  node: 10.3.0
  v8: 6.6.346.32-node.9
  uv: 1.20.3
  zlib: 1.2.11
  ares: 1.14.0
  modules: 64
  nghttp2: 1.29.0
  napi: 3
  openssl: 1.1.0h
  icu: 61.1
  unicode: 10.0
  cldr: 33.0
  tz: 2018c
  $
  ```
* 主题NexT版本号: hexo-theme-next 6.3.0
  ```
  $ cat themes/next/package.json
  {
    "name": "hexo-theme-next",
    "version": "6.3.0",
    "description": "Elegant and powerful theme for Hexo",
    ......
  $
  ```

### 1. 建立tags页面
打开Hexo目录，输入命令`hexo new page tags`，新建 **tags** 页面
```
$ hexo new page tags 
INFO  Created: ~/git/github/hexo.github.io/source/tags/index.md
$
```
输入命令后，source目录下会多一个文件夹 tags，文件夹中有一个文件 index.md

### 2. 编辑文件 index.md
编辑文件 **source/tags/index.md**，添加字段 **type: "tags"**   
修改前：
```
---
title: tags
date: 2018-06-12 11:25:16
---
```
修改后：
```
---
title: tags
date: 2018-06-12 11:25:16
type: "tags"
---
```

### 3. 确认站点配置文件
打开 Hexo 目录，编辑站点配置文件_config.yml，搜索关键字 "**Directory**"，确认有字段 "**tag_dir: tags**"  
默认状态无需修改，如下：
```
# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:
```

### 4. 确认主题配置文件
编辑主题配置文件 **themes/next/_config.yml**，搜索关键字 "**menu**"，确认开启字段 "**tags: /tags/ || tags**"  
修改前：
```
menu:
  home: / || home
  #about: /about/ || user
  #tags: /tags/ || tags
  #categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```
修改后：
```
menu:
  home: / || home
  #about: /about/ || user
  tags: /tags/ || tags
  #categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```
### 5. 查看 标签页 是否打开
* 完成上述修改后，输入命令`hexo s`  
* 打开浏览器，输入网址  [http://localhost:4000/](http://localhost:4000/)，进入 **Hexo** 首页，可以看到主菜单多了一个选项 **标签**，下方提示标签数量为 0
![home](https://raw.githubusercontent.com/b31jsc/img/master/Hexo%E6%B7%BB%E5%8A%A0%E6%A0%87%E7%AD%BE%E9%A1%B5/Hexo%E6%B7%BB%E5%8A%A0%E6%A0%87%E7%AD%BE%E9%A1%B51-%E9%A6%96%E9%A1%B5.png)


* 点击 **标签**，打开页面，提示 “暂无标签”
![tags0](https://raw.githubusercontent.com/b31jsc/img/master/Hexo%E6%B7%BB%E5%8A%A0%E6%A0%87%E7%AD%BE%E9%A1%B5/Hexo%E6%B7%BB%E5%8A%A0%E6%A0%87%E7%AD%BE%E9%A1%B52-%E6%A0%87%E7%AD%BE%E9%A1%B50.png)


经过上述步骤，标签页已经开启，接下来在文章中添加自定义标签，需要修改每一篇文章，上述文件不必再修改

### 6. 添加自定义标签
* 修改每一篇文章开头的 **tags** 字段  
例如，在文章 “**WIN10和Ubuntu18.04双系统的安装**” 中添加标签 “**从零折腾Ubuntu**”  
修改前：
  ```
  ---
  title: WIN10和Ubuntu18.04双系统的安装
  date: 2018-06-07 15:11:08
  tags:
  ---
  ```
  修改后：
  ```
  ---
  title: WIN10和Ubuntu18.04双系统的安装
  date: 2018-06-07 15:11:08
  tags: [从零折腾Ubuntu]
  ---
  ```
* 完成修改后，再次查看标签页，可以看到已经有内容了
![tags1](https://raw.githubusercontent.com/b31jsc/img/master/Hexo%E6%B7%BB%E5%8A%A0%E6%A0%87%E7%AD%BE%E9%A1%B5/Hexo%E6%B7%BB%E5%8A%A0%E6%A0%87%E7%AD%BE%E9%A1%B53-%E6%A0%87%E7%AD%BE%E9%A1%B51.png)

注意："**tags:**"冒号后要有一个空格 ！！！  
注意：如果需要添加多个标签，标签之间应通过英文逗号"**,**"分割。例如`tags: [从零折腾Ubuntu,Ubuntu]` ！！！





