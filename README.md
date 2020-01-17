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
 
 常用命令：
  
  `git reset commit` ：重置回退到某个commit
  `git reset origin/分支` ：重置回退到某个远端分支
  
 
 + --hard：重置位置的同时，直接将 working Tree工作目录、 index 暂存区及 repository 都重置成目标Reset节点的內容,所以效果看起来等同于
 清空暂存区和工作区。
 
 + --soft：重置位置的同时，保留working Tree工作目录和index暂存区的内容，只让repository中的内容和 reset 目标节点保持一致，
 因此原节点和reset节点之间的【差异变更集】会放入index暂存区中(Staged files)。所以效果看起来就是工作目录的内容不变，暂存区原有的内容也不变，
 只是原节点和Reset节点之间的所有差异都会放到暂存区中。
 
 + --mixed（默认）：重置位置的同时，只保留Working Tree工作目录的內容，但会将 Index暂存区 和 Repository 中的內容更改和reset目标节点一致，
 因此原节点和Reset节点之间的【差异变更集】会放入Working Tree工作目录中。所以效果看起来就是原节点和Reset节点之间的所有差异都会放到工作目录中。
 

 # git rm 

`git rm --cached “文件路径”` 

将该文件从缓存中删除，不删除物理文件

`git rm --f “文件路径”`

将该文件从缓存中删除，还会删除物理文件（不会回收到垃圾桶）

`git rm -r 文件夹`

递归删除，删除文件夹内的所有文件
