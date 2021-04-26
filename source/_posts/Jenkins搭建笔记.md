---
title: Jenkins搭建笔记
date: 2021-04-04 16:08:55
tags:
---

Jenkins安装：https://www.jenkins.io/zh/download/

1、首次安装时可不选插件，后续按需下载
2、插件下载地址可自定义，通过修改：C:\Windows\System32\config\systemprofile\AppData\Local\Jenkins\.jenkins\updates。也可再【插件管理】的高级选项中进行update
3、常用插件包括：Localization: Chinese (Simplified)-用于汉化和	
Role-based Authorization Strategy--用于角色管理

Credentials Binding--用于凭证管理

4、调整默认权限策略：管理Jenkins
--》Configure Global Security中选择授权策略，调整为Role-Based Strategy
5、管理角色：先通过系统管理=》全局安全配置，选择Role-Based Strategy。然后ManagerJenkins==》Manage and Assign Roles==》Manage Roles
6、管理凭证：ManageJenkins=》ManageCredentials
7、如何生成ssh：命令行输入：ssh-keygen -t rsa，然后再C:\Users\Administrator\.ssh即可找到。其中.pub结尾的是公钥，另一个是私钥。公钥可配置再github或gitee等第三方平台上。
8、安装后首次启动jenkins：打开安装目录，执行：java -jar Jenkins.war --httpPort=8080
平时启动jenkins：net start jenkins

停止jenkins: net stop jenkins

重启jenkins：http://localhost:8084/restart

https://blog.csdn.net/sinat_36710456/article/details/86079557
9、添加环境变量：ManagerJenkins=》ConfigureSystem=》Environment variables。重启后才能生效。
10、Jenkins修改默认工作空间：https://blog.csdn.net/qq_38093657/article/details/90054843
11、为项目添加构建参数：https://www.cnblogs.com/wangxu01/articles/11103538.html
bat命令中要使用%XXX%来获取参数
12、gradle 命令传属性参数：gradle -PbuildApp=others buildTask
https://blog.csdn.net/zxcofuestc/article/details/88392967
https://blog.csdn.net/weixin_39541750/article/details/113075508

13、无法安装插件，提示：unable to find valid certification path to requested target怎么办？：https://blog.csdn.net/hzau_boy/article/details/114373469

14、反向代理问题：只要保证系统配置中的路径跟访问的路径一致，反向代理就消失了。比如：配置地址为http://192.169.1.252:8084，而访问地址为http:localhost:8084,就会出现反向代理错误。

15、Android构建参考：https://blog.csdn.net/sz_chrome/article/details/99496148

16、如何将slave作为windows服务启动？先下载jenkins-agent.jnlp，使用javaws 启动jnlp文件，然后选择File选项中的以服务形式安装。

