---
layout: post
title: 使用tiny11builder自制精简win11 iso镜像
date: 2025-03-07 18:00:00 +0800
categories: [Windows]
tags: [iso,windows,tiny11]
---

注：由于文章最初发表于CSDN账号，所以转移过来后图片留有水印

## 下载最新win11 iso镜像

前往MSDN的新版网站：[https://next.itellyou.cn/](https://next.itellyou.cn/)

注册登录后，在windows11的分类下找到consumer editions x64版本并下载

![](/2025/03/20250308124430630.png)

## 下载tiny11builder

前往tiny11builder的github仓库：[https://github.com/ntdevlabs/tiny11builder](https://github.com/ntdevlabs/tiny11builder​)

在release页选择最新版本的压缩包下载，下载后解压缩备用

![](/2025/03/20250308124430632.png)

在仓库主页中可以看到，tiny11builder精简的软件内容，个人推荐普通精简。另外，精简后的镜像将绕过系统初始化时的Microsoft账户登录

>普通精简：  
Clipchamp  
News  
Weather  
Xbox (although Xbox Identity provider is still here, so it should be possible to be reinstalled with no issues)  
GetHelp  
GetStarted  
Office Hub  
Solitaire  
PeopleApp  
PowerAutomate  
ToDo  
Alarms  
Mail and Calendar  
Feedback Hub  
Maps  
Sound Recorder  
Your Phone  
Media Player  
QuickAssist  
Internet Explorer  
Tablet PC Math  
Edge  
OneDrive  

>更完全的核心精简（core）：  
all of the above +  
Windows Component Store (WinSxS)  
Windows Defender (only disabled, can be enabled back if needed)  
Windows Update (Windows Update wouldn't work anyway without WinSxS, so enabling it would only put the system in a state where it would try to update but fail spectacularily)  
WinRE  

## 开始精简

### 右键iso文件装载镜像

![](/2025/03/20250308124430633.png)

### 管理员身份运行Windows PowerShell

![](/2025/03/20250308124430634.png)

输入`Set-ExecutionPolicy unrestricted`以解除组策略脚本的运行限制

![](/2025/03/20250308124430635.png)

### 运行精简脚本

下载回来的tiny11builder压缩包里有两个精简脚本，分别对应普通精简和core精简。按需选择，右键使用powershell运行

![](/2025/03/20250308124430636.png)

输入iso文件装载的盘符，此处示例是E盘

![](/2025/03/20250308124430637.png)

等待片刻后会显示iso镜像中含有的Windows版本，选择所需的版本（其他版本会被删除），个人建议选专业版就足够了

![](/2025/03/20250308124430638.png)

等待精简过程，不会太久，精简期间建议电脑不要做其他复杂操作，否则会有概率会导致部分精简脚本运行失败或报错

最后提示Done.Creation completed! Press any key to exit the script...时就说明完成了

随便敲个键，回车退出（一定要做，因为脚本最后一步是清理c盘缓存，路径在C盘根目录的tiny11文件夹）

![](/2025/03/20250308124430639.png)

精简后的tiny11.iso文件在脚本所在路径下。精简后的iso文件大小并不会比精简前小太多，但系统安装后的C盘会小不少

![](/2025/03/20250308124430640.png)

## 进一步精简（可选，推荐）

以下是系统安装后执行的精简工具，分别是

windows defender移除：[https://github.com/ionuttbara/windows-defender-remover](https://github.com/ionuttbara/windows-defender-remover)

microsoft edge浏览器移除：[https://github.com/ShadowWhisperer/Remove-MS-Edge](https://github.com/ShadowWhisperer/Remove-MS-Edge)
