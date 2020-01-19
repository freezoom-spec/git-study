# 目录
+ [git 命令简介](git-命令简介)
+ [git rebase](#git-rebase)
+ [git reset](#git-reset)
+ [git revert](#git-revert)
+ [git rm ](#git-rm)


# git 命令简介

![git](https://github.com/freezoom-spec/git-study/blob/master/images/git.jpg)

`git add`:  当对工作区修改或新增的文件执行命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，
而该对象的ID被记录在暂存区的文件索引中。

`git commit`： 暂存区的目录树写到版本库中，分支会做相应的更新。即分支指向的目录树就是提交时暂存区的目录树。

`git reset HEAD`： 暂存区的目录树会被重写，被分支指向的目录树所替换,**工作区不受影响**.
    
`git rm --cached <file>`:  命令时，会直接从暂存区删除文件，**工作区不受影响**。
    
`git checkout .` 或者 `git checkout -- <file>`: 会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。
    
`git checkout HEAD .` 或者 `git checkout HEAD <file>`:会用HEAD指向的分支中的全部或者部分文件替换暂存区和以及工作区中的文件。
这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。

# git rebase 

合并近三个个commit操作实例：

+ 1、`git log` 显示commit记录

    ![git log](https://github.com/freezoom-spec/git-study/blob/master/images/rebase/rebase1.png)
+ 2、`git rebase -i 2cd1a7` **-i** 参数表示要合并提交的前一个commit 或者执行 `git rebase -i HEAD~3`

    ![git log](https://github.com/freezoom-spec/git-study/blob/master/images/rebase/rebase2.png)
+ 3、 第二步完成后显示所有的合并的commit，进入vi模式进行合并操作。
    
    + pick的commit会执行提交。
    + squash的commit会被合并到前一个commit。
     
    修改完后ESC退出vi模式，:wq保存退出，再次进入vi模式编写合并的信息提示，退出vi模式，保存退出即可。
    
    ![git log](https://github.com/freezoom-spec/git-study/blob/master/images/rebase/rebase3.png)
+ 4、`git log` 进行验证合并结果

    ![git log](https://github.com/freezoom-spec/git-study/blob/master/images/rebase/rebase4.png)

# git reset
 
 `git reset`: 回退，修改HEAD的位置，即将HEAD指向的位置改变为之前存在的某个版本。
 
 ![git log](https://github.com/freezoom-spec/git-study/blob/master/images/reset.jpeg)
 
 常用命令：
  
  `git reset commit`：回退到某个commit
  
  `git reset origin/分支` ：回退到某个分支
  
 三种模式： 
 
 + --hard：直接将工作目录、暂存区(index)及版本库(repository)都重置成目标Reset节点的內容。
 
 + --mixed（默认）：只保留工作目录的內容，但会将暂存区(Index)和版本库中的內容更改和reset目标节点一致。
 
 + --soft：保留工作目录和暂存区(index)的内容，只让版本木中的内容和reset目标节点保持一致。
 
 **适用场景：操作未提交到远程库的撤销操作**
 
# git revert

 `git revert commit`: 返回,想要撤销版本二，但又不想影响撤销版本三的提交，就可以用 `git revert` 命令来反做版本二，生成新的版本四，
    这个版本四里会保留版本三的东西，但撤销了版本二的东西。
   
 ![git log](https://github.com/freezoom-spec/git-study/blob/master/images/revert.jpeg)
 
  **适用场景：操作已经提交到远程库**
  
# git rm 

 `git rm --cached “文件路径”` : 将该文件从缓存中删除，不删除物理文件

 `git rm --f “文件路径”`: 将该文件从缓存中删除，还会删除物理文件（不会回收到垃圾桶）

 `git rm -r 文件夹`: 递归删除，删除文件夹内的所有文件
