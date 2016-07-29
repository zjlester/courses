# 版本控制系统应用指南

### 内容提要及学习目标 
#### 内容提要
版本控制系统可以理解为是一个针对快速版本迭代、多人协作开发过程中文档管理困难而提供的计算机辅助管理系统。历史上一些著名的版本控制系统包括CVS、ClearCase等。当前开源的Subversion和Git是使用最多的版本控制系统。
在本课程中，我们将介绍Git版本管理系统，并结合代码托管网站Github进行版本控制。

#### 学习目标

* 了解git的工作机制，理解暂存区、代码库、分支、推送、克隆等概念。
* 

#### 实验内容

1、安装Git
Ubuntu系统下：
    sudo apt-get install git
Windows系统中：


2、配置
    git config --global.username "ilester"
    git config --global.email "i@ilester.net"

3、创建代码库

    mkdir learngit
    cd learngit
    git init
创建一个文档readme.txt

4、添加文件并提交
git add readme.txt
git commit -m "add readme file"

git status 
git diff readme.txt

5、恢复回旧版本
git reset --hard HEAD^ 上一版本
git reset --hard HEAD^^ 上上版本
git reset --hard HEAD~100 退回上100个版本

git reset --hard 版本ID

git reflog 查看版本ID
git log 查看版本历史


HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

6、理解工作机制
工作区：代码存储的目录，原则上应该不包括隐藏的.git
版本库：指工作区中的.git，可以视为分作暂存区和分支

提交时的步骤：
1、git add将文件提交至暂存区
2、git commit将暂存区中未提交的内容加入当前分支
默认会创建master分支
每次提交前，如果更新不存在于暂存区，是不会提交的。

git checkout --file readme.txt #放弃变更，重新签出文件。两种情况，未执行git add则放弃所有变更，已执行git add但未执行git commit恢复暂存区中的状态 。--file选项必须加，不然变成切换分支。

7、删除文件
git rm test.txt 

8、添加远程库（Github)
创建公钥私钥对：
ssh-keygen -t rsa -C "i@ilester.net" 

id_rsa:私钥
id_rsa.pub ：公钥

登录Github，在accounts/settings中找到添加。
在Github创建新仓库testgit,访问格式：git@github.com:zjlester/testgit.git

git remote add origin git@github.com:zjlester/testgit.git
git push -u origin master
The authenticity of host 'github.com (192.30.253.112)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.
Counting objects: 17, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (13/13), done.
Writing objects: 100% (17/17), 2.05 KiB | 0 bytes/s, done.
Total 17 (delta 5), reused 0 (delta 0)
To git@github.com:zjlester/testgit.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
关联之后，以后只需要： 
git push origin master

9、克隆远端代码库
git clone git@github.com:zjlester/Gittest.git
不需要事先git init，会在当前目录下创建以Gittest为名的文件夹并克隆代码库。

10、分支管理
git branch 查看当前的分支
git branch test 创建一个新分支test
git checkout test 切换到test分支

git checkout -b dev 创建dev分支并切换至dev

git merge test 将test分支合并到当前分支
git branch -d test 删除test分支






