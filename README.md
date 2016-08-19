# GIT使用
author@xdoctorme
##1.ssh的建立
`ssh-keygen -t rsa -C "562915256@qq.com"` 

进入`C:\\Documents and Settings\\Administrator\\.ssh`中, 使用记事本打开 `id_rsa.pub` 文件, 将该文件中的内容复制到GitHub-Account Setting-ssh keys中 。邮箱为github注册邮箱ssh验证
`ssh -T git@github.com`  
##2.配置本地用户名和邮箱
`git config --global user.name "chu"`  

`git config --global user.email  "562915256@qq.com"`  注意有空格！！
并且我又配置了编辑器（git 默认是vim如果需要别的请下载且配置好环境变量..并不会）  

`git config --global core.editor vim`  

查看本地已配置用户名邮箱和编辑器  

`git config --global -l`  

##3.添加远程服务器（github库）
`git remote add origin git@github.com:chuweijia/chuchu.git`  

remote 远程的意思  

`git remote -v`查看本地添加的远程服务器（原理就是fetch+push)  

`git remote rm origin`  删除本地添加的服务器  

或者用`ssh+clone`（两步）  

##4.初始化本地文件夹
`git init`  

注意git有三个配置文件  

`C:\\Users\\CHU-pc\\.gitconfig`    具体到用户 --global  

`D:\\Git\\etc\\gitconfig`         是我安装git的地方 可以传递 --system  

`.git/config`                  .git 是你初始化git 文件夹时建立的隐藏文件夹   

##5.无分支push
`git add "test.txt"`添加  

`git commit -m "test is ok"`提交（未push状态)  

`git push origin master`（正式上线 push 推送到远程服务器)  


每一步都可以通过`git status` 查看状态 是否clean  

本地分支默认是master 于是解决方案  

`git branch`         查看本地所有分支  

`git branch bch1` 新建本地分支bch1  

`git checkout bch1` 切换到指定分支  

`git add`  `git commit`  保障了此时分支下的文件不会到master中！！  

`ls` 查看分支下的全部文件（确认）  

`git push origin bch1` 将本地分支推送到远程  


全部push上去 重复只会提交已更改的任务 （删除除外且已删除的会被推到远程）  

`git add -A` 在本地重新add一次   

并提交`git commit`  

清除远程分支bch1 本地分支(空）:远程分支 `git push origin :bch1`   
##6.关于.gitignore文件 暂时不详..
将需要被忽略上传的文件写入其中  

`touch .gitignore`  在与.git同级的文件夹下新建它  

`vim .gitignore` 进入vim编辑器 将需要被忽略的文件写入 虽然我这个实现不了啊啊啊！  

`fd1/*`  忽略目录 fd1 下的全部内容（根目录下的 /fd1/ 目录，子目录 /child/fd1/ 目录/fd1/*忽略根目录下的 /fd1/ 目录的全部内容  

`/*!.gitignore!/fw/bin/!/fw/sf/`忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录  

退出vim `ESC 或者shift+;`  

先退出输入模式`:q `退出（保存么？事实证明并没有）`:wq` 这里显示只读！！为什么？？且无法退出

