---
title: 捡垃圾之蜗牛星际折腾黑群晖
date: 2019-08-25 14:59:02
categories: 技术向
tags: 群晖,NAS
---
# 捡垃圾之蜗牛星际折腾黑群晖
<!--more-->
![300块捡到手的蜗牛星际](http://pw9qgbqkb.bkt.clouddn.com/Snipaste_2019-08-25_13-35-09.png)
	到手先拆机换静音风扇,垃圾电源/SSD/内存继续用,后续看情况再换,毕竟穷~
## 一、环境配置

### 1、安全群晖系统
	    好多年不接触，群里各种PVE，虚拟机等等看不懂，先按照教程最基础的安装黑群晖吧。
		HDMI接口是坏的，买个VGA转HDMA开机，点亮没问题。按照教程改BIOS--插入U盘启动盘启动--格式化SSD--写入群晖引导文件--关机--插入存储硬盘，重启--内网电脑找到群晖并安装DSM
		一步一步按照教程安装划分存储区，做基本设置，最后改MAC，改SN半洗白。
		
![安装的918+DSM](http://pw9qgbqkb.bkt.clouddn.com/Snipaste_2019-08-24_19-51-12.png)
### 2、网络配置
+ 找电信要公网IP
+ 准备域名
+ 旧路由器网件4300不支持阿里DDNS遂刷openwrt系统
+ 配置NAS静态IP，填写阿里DDNS，做端口转发
+ 做域名解析（一级域名A记录，二级域名CNAME记录）
+ 申请SSL证书（阿里云添加TXT记录，群晖添加证书文件）

>https远程访问为了隐藏端口号，常用套件改用别名，没常用套件的用二级域名做CNAME转向+群晖反向代理设置
![反向代理设置](http://pw9qgbqkb.bkt.clouddn.com/%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86.png)
	
### 3、安装常用套件
- 安装常用套件DRIVE，moment等
    cloud sync同步百度云上传不限速，下载10K蛋疼无比又没法不用
- 做导航网页
- 安装博客--安全性考虑遂改用hexo+github+netlify方案
![导航页](http://pw9qgbqkb.bkt.clouddn.com/Snipaste_2019-08-25_13-41-45.png)

博客也是个大坑，永远不知道BUG出现在什么位置～～～
![博客](http://pw9qgbqkb.bkt.clouddn.com/IMG_2858%2820190825-011644%29.jpg)

### 4、docker
docker是个好东西，不用安装臃肿的虚拟机，也不吃资源。功耗就下来了～～
docker主要安装了2个东西，一个远程迅雷一个aria2解决远程下载的痛点，不限速百度云就别想了，折腾好几次都没速度，放弃！
+ 远程迅雷按照教程来，传说关闭了但是确实还能用，就是注意登录迅雷页面不能用https
+ aria2 用二级域名访问，反向代理https转http，代理2次，一次WEBUI端口，一次数据隧道端口

## 二、使用
+ 手机安装APP和访问网页备份数据，观看NAS视频文件，远程下载至NAS等
+ 电视安装kodi访问群晖视频文件（开启NFS服务）


    折腾了几个星期大概基本能用吧，后续换电源，换SSD或改U盘，加硬盘做RAID1慢慢来吧。
![大佬的喷漆款](http://pw9qgbqkb.bkt.clouddn.com/%E7%99%BD%E8%89%B2b%E5%8D%95.png)

