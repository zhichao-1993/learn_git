   * [问题](#问题)
      * [1.已经在远程仓库建立的分支，本地git branch -r 看不见新建的分支  ？](#1已经在远程仓库建立的分支本地git-branch--r-看不见新建的分支--)
      * [2.如何建立本地分支与远程分支的追踪关系？（四种方法）](#2如何建立本地分支与远程分支的追踪关系四种方法)
      * [3. 删除了本地仓库的分支，也删除了远程仓库的分支，也做了同步，为什么本地git branch -a还是能查到已经删除的分支?](#3-删除了本地仓库的分支也删除了远程仓库的分支也做了同步为什么本地git-branch--a还是能查到已经删除的分支)
      * [4.在本地建立仓库，并和远程关联](#4在本地建立仓库并和远程关联)
      * [5.git checkout 的时候，在工作区对文件做了修改，但是未add或restore的时候，不能切换到其他分支](#5git-checkout-的时候在工作区对文件做了修改但是未add或restore的时候不能切换到其他分支)
      * [6.git clone后本地只有一个分支master](#6git-clone后本地只有一个分支master)
# 问题
## 1.已经在远程仓库建立的分支，本地git branch -r 看不见新建的分支  ？
   + git checkout master 切换到master
   + git pull 同步一下master
   + git branch -r   就可以查看到在远程仓库新建的分支了
   
## 2.如何建立本地分支与远程分支的追踪关系？（四种方法）
   + 远程上没有建立分支
        + git push --set-upstream origin branch_loc_name #推送本地分支到远程并建立跟踪，远程如果没有，就创建此分支
   + 远程上建立了分支，但是没有追踪
        +  手动建立追踪关系 git branch --set-upstream=origin/a a 
            + git branch --set-upstream-to=<远程主机名>/<远程分支名> <本地分支名>  
        +  push时建立追踪关系 git push -u origin b 
            + 首先要切换到b分支上，才可以操作
            + git push -u <远程主机名><本地分支名>
            + 本地分支和远程分支同名的分支进行追踪
        +  新建分支的时候建立追踪 git checkout -b c origin/c
            + git checkout -b <新建的本地分支名> <远程主机名>/<远程分支名>
            
## 3. 删除了本地仓库的分支，也删除了远程仓库的分支，也做了同步，为什么本地git branch -a还是能查到已经删除的分支?
    + git remote prune origin
    + 使用了这个命令就可以删除远程仓库已经不存在的分支
    
    
## 4.在本地建立仓库，并和远程关联
   + mkdir 空文件夹
   + cd 空文件夹
   + git init 将文件夹变成仓库
   + 打开GitHub网站，进入自己的账号
   + 点击创建新的仓库
   + 取名
   + 复制git网址
   + 在仓库下运行git Bash
   + 输入 git remote -u origin<远程主机名> master<本地分支名>

## 5.git checkout 的时候，在工作区对文件做了修改，但是未add或restore的时候，不能切换到其他分支
   + 把修改的文件add到缓存区，或者撤销修改的文件
   
## 6.git clone后本地只有一个分支master
   1.git branch -a 查看分支
   2.git checkout -b 本地分支名  origin(远程主机名)/远程分支名
   3.这样远程分支就下载到本地了