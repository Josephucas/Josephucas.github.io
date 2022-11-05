---
title: windows&linux-skills
date: 2022-10-27 10:09:27
categories:
tags:
description:
top:
---

<p align="right">副标题</p> 



<!-- more -->

## 定时开关机

### 定时关机

windows 环境下

win+r之后输入taskschd.msc

然后在操作项创建基本任务

然后再启动程序里面找到C盘里面Windows文件夹system32文件夹shutdown.exe程序

最后在添加参数选项里面选择-s -t 10

后续添加了管理员权限





### 定时开机

我这台电脑是f12

开机的时候先进入bios界面，选择电源选项下面的唤醒配置菜单

打开时钟唤醒选项下的daily event，在设置到每天的开机时间，启动顺序选主要

如果是只需要启动一次就选single event(一次)，然后在下面设置号几月几号几点几分

如果是要设定每周固定星期几开机，那就选weekly event(每周)，然后在下面设置具体星期几和时间。设置好保存退出即可完成定时开机的设置。



## 系统无损迁移

将原本机械硬盘里面C盘的东西，全部迁移到新的固态硬盘中，并且直接使用，然后可以直接把原来机械硬盘的系统盘删掉作为普通盘使用

使用傲梅轻松备份就可以实现了

可以参考下面的：

https://www.abackup.com/easybackup-tutorials/migrate-operating-system-to-ssd-6540.html







