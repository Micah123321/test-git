---
笔记创建于: '2022-05-09 12:27:12'
---

# git介绍

> Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。 Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。 Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

# 安装git

[Git - Downloads (git-scm.com)](https://git-scm.com/downloads)
下载,右键到文件夹打开git bash

设置下个人数据

```shell
$ git config --global user.name "你的名字"
## 邮箱
$ git config --global user.email "email@example.com"
```

总而言之,就是一个管理代码或者资源文化的仓库系统

# 命令行使用

```shell
## 创建git仓库
git init
## 此时创建文件,创建好了之后输入以下指令提交
git add .
## 版本提交信息
git commit -m "要提交的信息"

## 查看仓库状态
git status

## 查看版本信息
git log

```

![](https://oss.xiaomao6.com/mkoss/img/Roaming/picgo/20211026--14-48-31-e7fbe4.png)

如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数：

## 版本回退

```shell
## HEAD^为上个版本 ^^ 为上上个 100个为`HEAD~100`
git reset --hard HEAD^

## 此时想返回最新的版本也有办法,找到对应的id前几位
git reset --hard 前几位id

```

## 删除文件

```shell
git rm xx文件

## 恢复版本库中的文件到工作区中
git checkout -- 文件名
```

# 远程仓库

## gitee

注册账号,注册记住你的邮箱

### 配置密钥

```shell
## 填入你的邮箱
ssh-keygen -t ed25519 -C "xxxxx@xxxxx.com"
## 查看
cat ~/.ssh/id_ed25519.pub

```

粘贴到gitee公钥管理
[SSH公钥 - Gitee.com](https://gitee.com/profile/sshkeys)

此时配置完毕

### 创建项目

创建一个对应语言的项目,克隆下来,再进行提交,或者初始化之后在git创建空项目,然后提交上去

```shell

## 创建git仓库
git init
## 此时创建文件,创建好了之后输入以下指令提交
git add .
## 版本提交信息
git commit -m "要提交的信息"

## 创建分支
git branch -M master

git remote add origin 你的地址 

git push -u origin master

```

### 推送到远程仓库

```shell
git push origin master
```

## github

注册账号

配置个人信息

配置ssh密钥用于git项目

![](https://oss.xiaomao6.com/mkoss/2021/11/18/886fbb8b.png)

具体加入操作看上方

具体来说,就是纯英文版本的gitee,gitee用多了,github自然会了

因为区域原因,所以有时候git不下来,推荐使用镜像网站

![](https://oss.xiaomao6.com/mkoss/2022/05/09/be1d2dfb.png)

提交倒是没什么问题

## git代理

> 因为使用github 需要梯子,使用使用git的代理功能
> 这里只代理github
> 根据梯子的代理端口来设定

![](https://oss.xiaomao6.com/mkoss/2022/05/09/730d2ed8.png)

```shell
git config --global http.https://github.com.proxy socks5://127.0.0.1:10808
```

此时即可直接克隆

## 双仓库推送

> 此时觉得一个仓库存放备份不稳妥,则需要双仓库 gitee github

- 先在github新建一个仓库

```shell
# 创建链接
git remote set-url --add origin git@github.com:Micah123321/micah-markdown.git

git remote set-url --add origin git@github.com:Micah123321/xunda.git

# 查看状态
```

![](https://oss.xiaomao6.com/mkoss/2022/05/09/49999e63.png)

此时直接运行`git push`即可直接备份到俩个仓库

![](https://oss.xiaomao6.com/mkoss/2022/05/09/0aeb1cdb.png)

### 注意事项

发现有时候上传不成功,检查发现是steam++占用了host的问题,导致ssh代理出错,解决方案是 是使用v2ray的路由代理代替steam++的host代理功能

