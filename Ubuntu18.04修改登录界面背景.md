## Ubuntu18.04修改登录界面背景
0. Ubuntu通过 **设置** 只能修改锁屏界面和桌面背景，无法修改登录界面的紫色背景。
![before](https://raw.githubusercontent.com/b31jsc/img/master/Ubuntu18.04%E4%BF%AE%E6%94%B9%E7%99%BB%E5%BD%95%E7%95%8C%E9%9D%A2%E8%83%8C%E6%99%AF/Ubuntu18.04%E4%BF%AE%E6%94%B9%E7%99%BB%E5%BD%95%E7%95%8C%E9%9D%A2%E8%83%8C%E6%99%AF1-%E4%BF%AE%E6%94%B9%E5%89%8D.jpg)

   可通过如下步骤修改：

1. 准备一张背景图片
2. 修改 "**/etc/alternatives/gdm3.css**" 文件（注意需要使用超级用户权限），搜索关键字 "**lockDialogGroup**"，将 **url** 修改为文件所在的路径，格式为 **file://绝对路径**。同时分别修改或添加字段 **background-repeat**、**background-size** 和 **background-position**。示例如下：

    修改前：
    ```
    #lockDialogGroup {
      background: #2c001e url(resource:///org/gnome/shell/theme/noise-texture.png);
      background-repeat: repeat; }
    ```

    修改后：
    ```
    #lockDialogGroup {
      background: #2c001e url(file:///usr/share/backgrounds/Manhattan_Sunset_by_Giacomo_Ferroni.jpg);
      background-repeat: no-repeat;
      background-size: cover;
      background-position: center; }
    ```

    我的背景图片绝对路径： /usr/share/backgrounds/Manhattan_Sunset_by_Giacomo_Ferroni.jpg

3. 修改后重启电脑，登录界面背景如下：
![after](https://raw.githubusercontent.com/b31jsc/img/master/Ubuntu18.04%E4%BF%AE%E6%94%B9%E7%99%BB%E5%BD%95%E7%95%8C%E9%9D%A2%E8%83%8C%E6%99%AF/Ubuntu18.04%E4%BF%AE%E6%94%B9%E7%99%BB%E5%BD%95%E7%95%8C%E9%9D%A2%E8%83%8C%E6%99%AF2-%E4%BF%AE%E6%94%B9%E5%90%8E.jpg)




