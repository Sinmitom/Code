 
<!-- TOC -->目录
@Author 谢文韬
@Date 20200228

- [1. Why GitHub](#1-why-github)
- [2. Git](#2-git)
    - [创建版本库：](#创建版本库)
    - [Git时间：](#git时间)
    - [Git工作区和暂存区](#git工作区和暂存区)
    - [Git管理修改：](#git管理修改)
    - [远程仓库：](#远程仓库)
    - [关联仓库：](#关联仓库)
    - [从远程仓库克隆：](#从远程仓库克隆)
    - [创建分支与合并分支：](#创建分支与合并分支)
    - [多人协作](#多人协作)
    - [推送分支](#推送分支)
    - [标签管理](#标签管理)
    - [操作标签：](#操作标签)
    - [自定义Git](#自定义git)


#   1. Why GitHub
	• 有全世界最多公开的托管开源项目、代码最全，涵盖技术生态最全面、聚集牛人最多的平台。
	• 基于git实现了代码托管、而git可能是目前最好用的版本控制系统。
	• 提供了较为丰富的api，Issue Tracking和wiki等工具一应俱全……
	• free！！！！！
#   2. Git
	• Git是目前世界上最先进的分布式版本控制系统。
	• Git需设置名字和Email地址
	$ git config --global user.name "Your Name"
	$ git config --global user.email "email@example.com"

##  创建版本库：
选择一个空目录，通过git init命令可以将这个目录变成Git可以管理的 仓库。若未发现 .git 目录，可以用ls-as命令查看。注：Git只能追踪文本文件的改动，如txt文件，网页，程序代码等，但无法追踪图片、视频这些二进制的文件。

	$ git init
	$ git add *** //把文件添加到仓库，.表示添加所有文件到仓库
	$ git commit ***//把文件提交到仓库
	$ git commit -m "***"  //-m后面输入的是本次提交的说明
## Git时间：
	$ git status   //查看仓库当前的状态
	$ git diff  *** //查看文件修改的内容
	$ git log     //显示从最近到最远的提交日志，可以加上--pretty==oneline参数过滤一些信息
	$ git reset   //回退版本， HEAD^表示上一个版本,HEAD^^表示上上个版本，HEAD~100表示以上100个版本
	$ git reflog  //记录每一次命令
##  Git工作区和暂存区
	工作区：能看到的目录
	版本区：.git为git的版本库
##  Git管理修改：
    每次修改如果不用git add到暂存区，那就不会加入到commit中。
	git checkout --file   //丢弃工作区的修改
	$git reset HEAD file  //把暂存区的修改撤销掉
	若已提交到了版本库时，需版本回退操作。
	## Git删除文件
	$rm file   //删除文件
	$git rm test.txt  //从版本库中删除该文件
##  远程仓库：

本地Git仓库和Github仓库之间的传输是通过SSH加密的，

	第一步创建SSH Key ：$ ssh-keygen -t rsa -C"youremail@qq.com" ；
	第二步，登录github，创建一个key；
	第三步，开始操作……
##  关联仓库：
	创建新仓库后，在本地仓库运行$ git remote add origin git@github.com:仓库名字/learngit.git， 接着用
	$git push命令将其推送到远程。
##  从远程仓库克隆：
    $git clone git@github.com:Sinmitom/Coode git   //克隆一个本地库
## 创建分支与合并分支：
 **创建dev分支**

	$git checkout -b dev   //创建并切换
	$git branch //查看当前分支，列出所有的分支，当前分支会标一个*号
	$git merge dev //将dev分支的工作成果合并到master分支上
	$git branch -d dev  //删除dev分支
	$git switch -c dev   //创建并切换到新的dev分支
	$git switch master  //直接切换到master分支
	$git branch -D<name> //强行删除一个未被合并过的分支

**解决冲突**：

    Git无法自动合并分支时，必须先解决冲突再提交，合并完成。
	$git log --graph //看到分支合并图
	
**合并分支**：
    
    合并分支时，加上 --no--ff参数就可以用普通模式合并，合并后的历史有分支，能看出做过合并，而fast forward合并就看不出来曾经做过合并。
**Bug分支**：
    
    修复bug时，通过创建新的bug分支进行修复，然后合并。当手头工作未完成时，先把现场git stash一下，再去修复bug， 修复后，再用git stash pop，回到工作现场；在master分支上修复的bug，想要合并到当前dev分支，可以用git cherry-pick<commit>命令，避免重复劳动。

## 多人协作
	本地库对应master， 远程仓库对应orgin
	$git remote   //查看远程库的信息
	$git remote -v  //显示更详细的信息

## 推送分支
	$git push origin master  //把该分支上所有的本地提交到远程库。
	$git push origin dev  //推送其他分支如dev
	$git checkout -b dev origin/dev   //创建远程origin的dev分支到本地
	$git pull  //将最新的提交从origin/dev抓下来
	$git branch --set-upstream-to=origin/dev dev   //指定本地dev分支与远程origin/dev分支的链接

## 标签管理
**创建标签**：

	$git tag<name>  //打上新标签
	$git tag   //查看所有标签
	$git tag -a<tagname> -m"tips"   //可以指定标签信息

## 操作标签：
	$git tag -d v0.1  //删除标签
	$git push origin v1.0  //推送某个标签到远程
	$git push origin --tags  //一次性推送全部尚未推送到远程的本地标签
	$git push origin :refs/tags/v0.1 //远程删除
	
## 自定义Git
	$git config --global color.ui true   //让Git显示颜色
	
	tips:待补充
	
