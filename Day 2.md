# Daily Report

--------

## 一、学习时间： *2020年7月7日*

## 二、学习内容：

   1. 复习了一下昨天学习的markdown语法笔记以及git部分语法笔记。

   2. 将剩下的git学习完毕。

      > 了解了如何使用github参与一个开源项目，先Fork到自己账下，然后从自己账号下clone，这样就能推送修改到自己的仓库。最后通过pull request贡献代码。
      >
      > 接触了Gitee
      >
      > 大致了解了搭建Git服务器的步骤
      >
      > 首先需要一台运行Linux的机器，推荐Ubuntu或Debian
      >
      > 1.安装git
      >
      > 2.创建一个git用户
      >
      > 3.创建证书登录
      >
      > 4.初始化Git仓库
      >
      > 5.禁用shell登录
      >
      > 6.克隆远程仓库
      >
      > Gitosis用于管理公钥
      >
      > Gitolite控制权限
      >
      > 了解了SourceTree的使用

   3. 学习了Mac终端的常用命令

   4. 温习了逆波兰表达式

​						

* ## Mac终端常用命令

  > 1. pwd (print working directory) 显示当前目录的路径名 
  >
  > 2. ls (list directory contents) 显示当前目录的内容 
  >
  >    - `ls -l` — 用长格式列出来
  >    - `ls -a` — 列出文件（包括隐藏的文件）
  >    - `ls -al` — 以长格式列出文件（包括隐藏的文件）
  >
  > 3. cd (change directory) 改变当前目录
  >
  >    * cd — (无参数)返回home目录
  >    * cd ~ — 返回home目录，可以使用cd ~/Music快速到达该目录，使用cd ~Guest/进入Guest用户的home目录
  >    * cd - — 返回上一次操作的目录，可与当前目录进行切换
  >    * cd .. — 返回上一层目录，..表示上一层目录，而.表示当前目录，如./Music，表示当前目录下的Music文件
  >
  > 4. mkdir (make directory) 创建目录 
  >
  > 5. rmdir (remove directory) 删除目录 
  >
  > 6. touch 新建一个文件
  >
  > 7. rm 删除文件或目录
  >
  > 8. ##### `mv 原文件 目标目录/新文件名` — 移动
  >
  > 9. ##### `cp 带目录文件 目标目录` — 复制粘贴
  >
  > 10. ##### `man 命令` — 查看使用手册
  >
  > 11. ##### `history` — 查看之前执行过命令的历史记录
  >
  > 12. ##### `ps` — 查看当前终端运行的程序
  >
  > 13. `cat`— 显示或连接文件 
  >

  

* ## git 语法

  > 1. * git分支管理便捷，而SVN创建和切换分支过于缓慢。
  >
  >    * Git支持多种协议，包括`https`，但`ssh`协议速度最快。
  >
  >    * 分支策略：master分支仅用来发布新版本，成员在dev分支上干活。
  >
  >    * 开发一个新feature，最好新建一个分支。
  >
  >    * 多人协作的工作模式：
  >
  >      1. 首先，可以试图用`git push origin <branch-name>`推送自己的修改；
  >      2. 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并；
  >      3. 如果合并有冲突，则解决冲突，并在本地提交；
  >      4. 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！
  >
  >      如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`。
  >
  >    * 标签总是和某个commit挂钩。如果这个commit既出现在master分支，又出现在dev分支，那么在这两个分支上都可以看到这个标签
  >
  >    
  >
  > ​       
  >
  > 2. 语法学习
  >
  >    * 使用`git clone 远程库地址`  命令克隆远程库
  >
  >    * 查看分支：`git branch`
  >
  >    * 创建分支：`git branch <name>`
  >
  >    * 切换分支：`git checkout <name>`或者`git switch <name>`
  >
  >    * 创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`
  >
  >    * 合并某分支到当前分支：`git merge <name>`
  >
  >    * 删除分支：`git branch -d <name>`
  >
  >    * 用`git log --graph --pretty=oneline --abbrev-commit`命令可以看到分支合并图
  >
  >    * 合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并
  >
  >    * 修复bug时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场
  >
  >    * 在master分支上修复的bug，想要合并到当前dev分支，可以用`git cherry-pick <commit>`命令，把bug提交的修改“复制”到当前分支
  >
  >    * `git stash list`命令可以查看stash内容
  >
  >    * 工作现场用`git stash apply`恢复，但是恢复后，stash内容并不删除，你需要用`git stash drop`来删除。或者用`git stash pop`，恢复的同时把stash内容也删了
  >
  >    * 如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除
  >
  >    * 查看远程库信息，使用`git remote -v`；
  >
  >    * 本地新建的分支如果不推送到远程，对其他人就是不可见的；
  >
  >    * 从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；
  >
  >    * 在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
  >
  >    * 建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；
  >
  >    * 从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。
  >
  >    * 命令`git rebase `可以把本地未push的分叉提交历史整理成直线，目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比
  >
  >    * 命令`git tag <tagname>`用于新建一个标签，默认为`HEAD`，也可以指定一个commit id；
  >
  >    * 命令`git tag -a <tagname> -m "..."`可以指定标签信息；
  >
  >    * 命令`git tag`可以查看所有标签。
  >
  >    * 命令`git push origin <tagname>`可以推送一个本地标签；
  >
  >    * 命令`git push origin --tags`可以推送全部未推送过的本地标签；
  >
  >    * 命令`git tag -d <tagname>`可以删除一个本地标签；
  >
  >    * 命令`git push origin :refs/tags/<tagname>`可以删除一个远程标签。
  >
  >    * 命令`git config --global color.ui true`可以让Git显示颜色。
  >
  >    * 忽略某些文件时，需要编写`.gitignore`；**（复习点）**
  >
  >    * `.gitignore`文件本身要放到版本库里，并且可以对`.gitignore`做版本管理。**（复习点）**
  >
  >    * 命令` git config --global alias.别名 命令名` 可以配置别名
  >
  >      > 加上`--global`是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用
  >
  >    * 命令 `cat .git/config` 可以查看配置文件，别名就在`[alias]`后面，要删除别名，直接把对应的行删掉即可。而当前用户的Git配置文件放在用户主目录下的一个隐藏文件`.gitconfig`中；配置别名也可以直接修改这个文件，如果改错了，可以删掉文件重新通过命令配置。
  >
  >      
  >

  ## 三、遇到的问题

  * 在运行sourcetree时遇到打不开的情况，“Sourcetree” can’t be opened because Apple cannot check it for malicious software.

    > 解决方案: 右击，open

  ## 四、学习总结

  这总算把第0期任务完成了，主要是git学习的时候跟着敲花了不少时间。接下来准备正式进入第1期任务的学习。

