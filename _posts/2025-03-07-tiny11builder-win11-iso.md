---
title: 使用tiny11builder自制精简win11 iso镜像
date: 2025-03-07 18:00:00 +0800
categories: [Windows]
tags: [iso,windows,tiny11]
---

注：由于文章最初发表于CSDN账号，所以转移过来后图片留有水印

## 下载最新win11 iso镜像

前往MSDN的新版网站：[https://next.itellyou.cn/](https://next.itellyou.cn/)

注册登录后，在windows11的分类下找到consumer editions x64版本并下载

![](https://github.com/user-attachments/assets/b21c68ff-675e-4e1d-a99e-5f466bfe60da)   

## 下载tiny11builder

前往tiny11builder的github仓库：[https://github.com/ntdevlabs/tiny11builder](https://github.com/ntdevlabs/tiny11builder​)

在release页选择最新版本的压缩包下载，下载后解压缩备用

![](https://github.com/user-attachments/assets/9683541e-2322-431e-83fd-d7b8c1a9d2ca)

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

![](https://github.com/user-attachments/assets/10b838d7-b667-40ad-b21e-9a907cbe890e)

### 管理员身份运行Windows PowerShell

![](https://github.com/user-attachments/assets/fe15338c-1900-45a0-a5ae-aeeadba9169c)

输入`Set-ExecutionPolicy unrestricted`以解除组策略脚本的运行限制

![](https://github.com/user-attachments/assets/578693be-5a3c-4725-a2ad-f7d30fe1d6cf)

### 运行精简脚本

下载回来的tiny11builder压缩包里有两个精简脚本，分别对应普通精简和core精简。按需选择，右键使用powershell运行

![](https://github.com/user-attachments/assets/11e57b53-c4f0-4f78-b1d3-517d93ed3d55)

输入iso文件装载的盘符，此处示例是E盘

![](https://github.com/user-attachments/assets/21f0174d-85c5-4458-b403-311056695310)

等待片刻后会显示iso镜像中含有的Windows版本，选择所需的版本（其他版本会被删除），个人建议选专业版就足够了

![](https://github.com/user-attachments/assets/0382dea6-2faf-4d64-876c-028a688661dc)

等待精简过程，不会太久，精简期间建议电脑不要做其他复杂操作，否则会有概率会导致部分精简脚本运行失败或报错

最后提示Done.Creation completed! Press any key to exit the script...时就说明完成了

随便敲个键，回车退出（一定要做，因为脚本最后一步是清理c盘缓存，路径在C盘根目录的tiny11文件夹）

![](https://github.com/user-attachments/assets/23552e92-c486-4f2e-8f78-1d70b5269630)

精简后的tiny11.iso文件在脚本所在路径下。精简后的iso文件大小并不会比精简前小太多，但系统安装后的C盘会小不少

![](https://github.com/user-attachments/assets/d0be8fd8-077f-40cc-a9a8-97e753d7d950)

## 进一步精简（可选，推荐）

以下是系统安装后执行的精简工具，分别是

windows defender移除：[https://github.com/ionuttbara/windows-defender-remover](https://github.com/ionuttbara/windows-defender-remover)

microsoft edge浏览器移除：[https://github.com/ShadowWhisperer/Remove-MS-Edge](https://github.com/ShadowWhisperer/Remove-MS-Edge)
