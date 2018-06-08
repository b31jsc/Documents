## WIN10和Ubuntu18.04双系统的安装
### 0. 准备工作
#### 0.1 电脑配置  
* 型号: 联想IdeaPad-Y400
* CPU: Intel® Core™ i5-3230M CPU @ 2.60GHz × 4
* 硬盘: 1TB
* 内存: DDR3 4G

#### 0.2 WIN10和Ubuntu镜像
* WIN10镜像  
下载网站: MSDN [https://msdn.itellyou.cn/](https://msdn.itellyou.cn/)  
文件名: cn_windows_10_consumer_editions_version_1803_updated_march_2018_x64_dvd_12063766.iso
如下图:  
![MSDN](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/MSDN_WIN10%E9%95%9C%E5%83%8F%E4%B8%8B%E8%BD%BD.png)

* Ubuntu镜像  
下载网站: Ubuntu官网  [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)  
文件名: ubuntu-18.04-desktop-amd64.iso

#### 0.3 U盘一个  16G

#### 0.4 额外准备一台电脑  
安装过程中，笔记本可能需要全盘格式化，导致无法启动，此时需要另一台电脑协助查看资料，制作U盘启动盘等。

#### 0.5 软件
* UltraISO软碟通，用于制作U盘启动盘  
下载网站: UltraISO软碟通 [https://cn.ultraiso.net/xiazai.html](https://cn.ultraiso.net/xiazai.html)  

* 动态磁盘转换器，用于将动态磁盘转换为基本磁盘  
下载网站: 傲梅科技 [https://www.disktool.cn/download.html](https://www.disktool.cn/download.html)  
在网页的最下端，如下图:  
![动态磁盘转换器](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8%E4%B8%8B%E8%BD%BD.png)

### 1. 确认电脑硬盘格式和BIOS引导方式
#### 1.1 磁盘类型: 基本磁盘、动态磁盘  
需要使用基本磁盘。动态磁盘是微软在WIN2000引入的概念，Ubuntu不支持。  

#### 1.2 磁盘分区形式：MBR、GPT  
需要使用GPT。MBR全称是Master Boot Record（主引导记录），MBR早在1983年IBM PC DOS 2.0中就已经提出，是传统的分区方案。GPT全称是Globally Unique Identifier Partition Table，意即GUID分区表。  
GPT磁盘相对于MBR磁盘优化了一些特性，比较关键的有两点：  
* GPT支持2TB以上的大硬盘，MBR不支持。电脑的容量逐年上升，超越2TB指日可待；
* GPT分区个数几乎没有限制，MBR最多4个主分区。

下面介绍如何在XP系统和WIN10系统中查看磁盘类型与磁盘分区形式，其他系统大同小异。  

#### 1.3 XP系统查看磁盘类型和磁盘分区形式  
##### 1.3.1 鼠标右键 **我的电脑**，点击 **管理**；  
![右键我的电脑](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/XP%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F1-%E5%8F%B3%E9%94%AE%E6%88%91%E7%9A%84%E7%94%B5%E8%84%91.png)
##### 1.3.2 **计算机管理** 页面打开后，左侧导航栏中点击 **磁盘管理**；  
![磁盘管理](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/XP%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F2-%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86.png)
##### 1.3.3 鼠标右键 **磁盘0**，点击 **属性**；  
![属性](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/XP%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F3-%E5%B1%9E%E6%80%A7.png)
##### 1.3.4 **属性** 菜单打开后，标签页中选 **卷**，此处可以查看到磁盘类型和磁盘分区形式。图中为基本磁盘和MBR分区。  
![卷](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/XP%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F4-%E5%8D%B7.png)

#### 1.4. WIN10查看磁盘类型和磁盘分区形式  
##### 1.4.1 鼠标右键 **此电脑**，点击 **管理**；    
![右键我的电脑](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F1-%E5%8F%B3%E9%94%AE%E6%88%91%E7%9A%84%E7%94%B5%E8%84%91.png)
##### 1.4.2 **计算机管理** 页面打开后，左侧导航栏中点击 **磁盘管理**；  
![磁盘管理](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F2-%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86.png)
##### 1.4.3 鼠标右键 **磁盘0**，点击 **属性**；  
![属性](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F3-%E5%B1%9E%E6%80%A7.png)
##### 1.4.4 **属性** 菜单打开后，标签页中选 **卷**，此处可以查看到磁盘类型和磁盘分区形式。图中为基本磁盘和GPT分区。  
![卷](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E6%9F%A5%E7%9C%8B%E7%A3%81%E7%9B%98%E6%A0%BC%E5%BC%8F4-%E5%8D%B7.png)

#### 1.5 修改磁盘类型和磁盘分区形式  
* 如果已经是基本磁盘+GPT分区，无序格式转换，可跳过如下两步；
* 如果磁盘类型为动态磁盘，需通过 **动态磁盘转换器** 转换为基本磁盘；  
**注意：转换后所有数据会丢失，提前做好备份！**
* 如果磁盘分区形式为MBR分区，需通过 工具 转换为GPT分区。  
**注意：转换后所有数据会丢失，提前做好备份！**

动态磁盘转换为基本磁盘的操作步骤如下：  
##### 1.5.1 安装 **动态磁盘转换器**  
* 安装过程非常简单，一路“下一步”即可。具体过程如下图：  
![安装动态磁盘转换器1](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A81.png)  
![安装动态磁盘转换器2](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A82.png)  
![安装动态磁盘转换器3](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A83.png)  
![安装动态磁盘转换器4](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A84.png)  
![安装动态磁盘转换器5](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A85.png)  
![安装动态磁盘转换器6](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A86.png)  
![安装动态磁盘转换器7](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A87.png)  
![安装动态磁盘转换器8](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A88.png)  
![安装动态磁盘转换器9](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%AE%89%E8%A3%85%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A89.png)  

##### 1.5.2 运行 **动态磁盘转换器**，转换动态磁盘为基本磁盘
* 运行 **动态磁盘转换器**，点击“下一步”；  
![运行动态磁盘转换器1](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8%E4%BD%BF%E7%94%A81-%E6%AC%A2%E8%BF%8E.png)  

* 选择 **方式1 转换动态磁盘到基本磁盘**，点击“下一步”；
![运行动态磁盘转换器2](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8%E4%BD%BF%E7%94%A82-%E9%80%89%E6%8B%A9%E6%96%B9%E5%BC%8F.png)  

* 选择要转换的磁盘，点击“下一步”；一般的电脑只有 **磁盘0**，选择 **磁盘0** 即可。图片中为 **磁盘1**。
![运行动态磁盘转换器3](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8%E4%BD%BF%E7%94%A83-%E9%80%89%E6%8B%A9%E7%A3%81%E7%9B%98.bmp)  

* 确认进行转换，点击“下一步”；  
**注意：转换后所有数据会丢失，提前做好备份！**
![运行动态磁盘转换器4](https://raw.githubusercontent.com/b31jsc/img/master/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8/%E5%8A%A8%E6%80%81%E7%A3%81%E7%9B%98%E8%BD%AC%E6%8D%A2%E5%99%A8%E4%BD%BF%E7%94%A84-%E6%89%A7%E8%A1%8C.bmp)  

* 等待转换完成即可。

#### 1.6 MBR转GPT的操作步骤如下：
MBR转GPT的方法有很多，在网上百度“MBR转GPT”即可。

#### 1.7 BIOS引导模式：Legacy BIOS、UEFI BIOS  
需要使用UEFI。
##### 1.7.1 修改BIOS引导模式
* 开机，连击 **F2**，进入 **BIOS Setup** 界面，选择选项卡 **Boot**，按下图配置。
* 修改 **Boot Mode** 为 **Legacy Support**，该模式同时支持Legacy BIOS和UEFI BIOS；
* 修改 **Boot Priority** 为 **UEFI First**，优先UEFI BIOS；
* 修改 **USB Boot** 为 **Enable**。
![BIOS1-修改BootMode](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/BIOS1-%E4%BF%AE%E6%94%B9BootMode.png)  

#### 1.8 部分品牌电脑需要关闭Secure Boot

### 2. 安装WIN10
#### 2.1 制作WIN10启动盘  
参考如下网页，使用 **UltraISO软碟通** 制作U盘启动盘。  
[https://github.com/b31jsc/Documents/blob/master/UltraISO%E5%88%B6%E4%BD%9CU%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98.md#ultraiso%E5%88%B6%E4%BD%9Cu%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98](https://github.com/b31jsc/Documents/blob/master/UltraISO%E5%88%B6%E4%BD%9CU%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98.md#ultraiso%E5%88%B6%E4%BD%9Cu%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98)  
**注意：第二步使用准备好的WIN10镜像！**  
**注意：如果电脑经历过磁盘格式转换，可能已经无法启动，此时需要另一台电脑协助制作镜像！**

#### 2.2 通过U盘启动  
系统镜像已经安装到U盘中了，接下来要通过U盘启动，一般有两种方式。“修改BIOS启动项”和“直接选择从U盘启动”，推荐“直接选择从U盘启动”。但是不是所有电脑都支持，如下是联想Y400上的操作方法。
* 修改BIOS启动项  
插入U盘，开机，连击 **F2**，进入 **BIOS Setup** 界面，选择选项卡 **Boot**，在 **EFI** 中将U盘排在第一位，重启。如下图。
![BIOS2-F2修改启动](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/BIOS2-F2%E4%BF%AE%E6%94%B9%E5%90%AF%E5%8A%A8%E9%A1%B9.png)  

* 直接选择从U盘启动  
插入U盘，开机，连击 **F12**，进入 **Boot Menu** 界面，选择“EFI  USB Device”，回车，系统会自动跳转。
![BIOS3-F12直接选择启动项](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/BIOS3-F12%E7%9B%B4%E6%8E%A5%E9%80%89%E6%8B%A9%E5%90%AF%E5%8A%A8%E9%A1%B9.png)  

#### 2.3 Windows安装程序  
从U盘启动后，电脑自动进入Windows安装程序
* 选择 **要安装的语言** 为 **中文（简体-中国）**，默认值就是，无需修改。确认后点击“下一步”；  
![WIN10安装过程1-选择语言](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B1-%E9%80%89%E6%8B%A9%E8%AF%AD%E8%A8%80.png)  
* 选择 **现在安装** ，点击“下一步”；  
![WIN10安装过程2-现在安装](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B2-%E7%8E%B0%E5%9C%A8%E5%AE%89%E8%A3%85.png)  
* 进入 **激活Windows界面** ，点击下方的 **我没有产品密钥** ；  
![WIN10安装过程3-激活](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B3-%E6%BF%80%E6%B4%BB.png)  
* 选择想要安装的WIN10版本，我安装的是 **Windows 10 专业版** ，选中后点击“下一步”；  
![WIN10安装过程4-选择版本](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B4-%E9%80%89%E6%8B%A9%E7%89%88%E6%9C%AC.png)  
* 勾选 **我接受许可协议** ，点击“下一步”；  
![WIN10安装过程5-接受许可条款](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B5-%E6%8E%A5%E5%8F%97%E8%AE%B8%E5%8F%AF%E6%9D%A1%E6%AC%BE.png)  
* 选择 **自定义：仅安装 Windows** ，点击“下一步”；  
![WIN10安装过程6-自定义](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B6-%E8%87%AA%E5%AE%9A%E4%B9%89.png)  
* 建立分区，我将磁盘原有分区全部删除，重新建立分区。
如果想建立的分区大小为整数，创建分区时分区大小参考如下填写：  
50G = 51208M  
250G = 256005M  
500G = 512002M  
我手动建立了四个分区：  

   | 盘符 | 大小 |
   | ---- | ---- |
   | C盘  | 50G  |
   | D盘  | 50G  |
   | E盘  | 250G |
   | F盘  | 500G |

* 图片中的 **恢复** 分区、**系统分区** 分区、**MSR（保留）** 分区是系统自动创建的，不用理会。
![WIN10安装过程7-分区设置1](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B7-%E5%88%86%E5%8C%BA%E8%AE%BE%E7%BD%AE1.png)  
* 完成分区建立后，选中C盘对应的 **驱动器0分区4**，点击“下一步”；  
![WIN10安装过程7-分区设置2](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B7-%E5%88%86%E5%8C%BA%E8%AE%BE%E7%BD%AE2.png)  
* 等待安装完成，安装完成后系统自动重启，首次进入WIN10时还需要一些配置，按文字提示操作即可。下图是安装完成的WIN10桌面；  
![WIN10安装过程8-WIN10桌面](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/WIN10%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B8-WIN10%E6%A1%8C%E9%9D%A2.png)  

### 3. 安装Ubuntu
#### 3.1 制作Ubuntu启动盘  
参考如下网页，使用 **UltraISO软碟通** 制作U盘启动盘。  
[https://github.com/b31jsc/Documents/blob/master/UltraISO%E5%88%B6%E4%BD%9CU%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98.md#ultraiso%E5%88%B6%E4%BD%9Cu%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98](https://github.com/b31jsc/Documents/blob/master/UltraISO%E5%88%B6%E4%BD%9CU%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98.md#ultraiso%E5%88%B6%E4%BD%9Cu%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98)  
**注意：与制作WIN10启动盘类似，第二步使用准备好的Ubuntu镜像！**  

#### 3.2 通过U盘启动
参考 “2.2安装WIN10” 中的 “2.2.1 通过U盘启动”，运行Ubuntu启动盘。

#### 3.3 Ubuntu安装程序
从U盘启动后，电脑自动进入Ubuntu安装程序
* 选择第一项 **Try Ubuntu without installing** ，点击“回车”。系统会进入试用版的Ubuntu系统；  
![Ubuntu安装过程0-Try](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B0-Try.png)  
* 等待系统启动完成，见到如下界面。双击桌面的 **Install Ubuntu 18.04 LTS** ，打开安装程序。确认后点击“下一步”；  
![Ubuntu安装过程1-桌面install](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B1-%E6%A1%8C%E9%9D%A2install.png)  
* 进入欢迎界面，左侧选择 **中文（简体）**，点击“继续”；
![Ubuntu安装过程2-语言](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B2-%E8%AF%AD%E8%A8%80.png)  
* 进入键盘布局界面，左侧选择 **英语（美国）**，右侧选择 **英语（美国）**，点击“继续”；  
![Ubuntu安装过程3-键盘](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B3-%E9%94%AE%E7%9B%98.png)  
* 进入无线界面，连接可用的无线Wi-Fi网络，点击“继续”；  
注意：此处也可以不连接网络，如果不连接网络，下一步不要进行系统更新！
![Ubuntu安装过程4-网络](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B4-%E7%BD%91%E7%BB%9C.png)  
* 进入更新和其他软件界面，选择 **最小安装**，选择 **安装Ubuntu时下载更新**，点击“继续”；  
注意：如果上一步没有连接网络，此处也不可以进行系统更新！
注意：开启系统更新安装时间会更长一些，安装之后就不必更新了！
![Ubuntu安装过程5-最小安装](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B5-%E6%9C%80%E5%B0%8F%E5%AE%89%E8%A3%85.png)  
* 进入安装类型界面，选择 **其它选项**，点击“继续”；  
![Ubuntu安装过程6-其它选项](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B6-%E5%85%B6%E5%AE%83%E9%80%89%E9%A1%B9.png)  
* 在接下来进入的界面进行分区创建，点击左下角的 **+** 加号进行分区创建，共创建四个分区；

   | 大小  | 用于 | 挂载点 |
   | ---:  | :---: | :---: |
   | 30720 | EXT4 | /    |
   |  8192 | 交换分区 | ——  |
   |  1024 | EXT4 | /boot |
   | 40960 | EXT4 | /home |

   注意：此处我创建的分区没有做到整数对齐！  
   创建完成后点击“继续”；  
![Ubuntu安装过程7-分区规划](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B7-%E5%88%86%E5%8C%BA%E8%A7%84%E5%88%92.png)  
* 创建ext4分区；  
![Ubuntu安装过程8-创建ext4分区](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B8-%E5%88%9B%E5%BB%BA%E5%88%86%E5%8C%BAext4.png)  
* 创建swap分区，swap分区也称为交换分区；  
![Ubuntu安装过程9-创建交换分区](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B9-%E5%88%9B%E5%BB%BA%E5%88%86%E5%8C%BA%E4%BA%A4%E6%8D%A2%E5%88%86%E5%8C%BA.png)  
* 完成分区创建后，点击“继续”，等待系统安装完成.下图是安装完成的Ubuntu系统界面；  
![Ubuntu安装过程10-桌面](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/Ubuntu%E5%AE%89%E8%A3%85%E8%BF%87%E7%A8%8B10-%E6%A1%8C%E9%9D%A2.png)  

### 4. 再次介绍分区方案
双系统的关键是分区的配置，如下表，前三个分区是装机过程中系统自动创建的，无需例会，其他分区分别对应WIN10和Ubuntu系统。

   | 大小 | 文件系统 | 用途 |
   | ---: | :---: | :--- |
   | 500M | NTFS | 恢复，OEM分区 |
   | 100M | ——   | EFI系统分区 |
   |  16M | ——   | MSR（保留） |
   |  50G | NTFS | WIN10 C盘 |
   |  50G | NTFS | WIN10 D盘 |
   | 250G | NTFS | WIN10 E盘 |
   | 500G | NTFS | WIN10 F盘 |
   |  30G | EXT4 | Ubuntu / |
   |   8G | EXT4 | Ubuntu 交换分区 |
   |   1G | EXT4 | Ubuntu /boot |
   |  40G | EXT4 | Ubuntu /home |

附上WIN10中查看最终分区方案
![最终分区方案](https://raw.githubusercontent.com/b31jsc/img/master/WIN10%E5%92%8CUbuntu%E5%8F%8C%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E8%AF%B4%E6%98%8E/%E6%9C%80%E7%BB%88%E5%88%86%E5%8C%BA%E6%96%B9%E6%A1%88.png)  


### 注意：
* **问题现象**：使用一段时间后发现两个系统时间不一致。Ubuntu的系统时间是当前时间，WIN10的系统时间比当前时间早8个小时。  
**问题原因**：BIOS会记录一个时间，Windows系统把BIOS时间作为本地时间，即操作系统中显示的时间跟BIOS中显示的时间是一样的。Ubuntu系统把BIOS时间当作UTC时间，操作系统显示的时间是UTC时间经过换算得来的。比如说北京时间是GMT+8，则系统中显示时间是UTC时间+8。  
当Ubuntu启动时，通过网络获取当前时间，然后修改BIOS时间比当前时间早8
个小时，WIN10启动后会认为BIOS中的时间就是当前时间，所以WIN10显示的时间比实际时间早8个小时。  
**解决方法**：修改Ubuntu系统把BIOS时间作为本地时间。输入命令 `timedatectl set-local-rtc 1`，解决上述问题。  







