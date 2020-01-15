  # git reset
 
 `git reset` 有三种模式 
 
 `git reset --hard` 重置工作目录和缓存区
 
 `git reset --soft` 保留干工作目录，重置HEAD所带来的新的差异放进暂存区
 
 `git reset --mixed(默认)` 保留干工作目录，清空暂存区
 
 
 # git rm

`git rm --cached “文件路径”` 

将该文件从缓存中删除，不删除物理文件

`git rm --f “文件路径”`

将该文件从缓存中删除，还会删除物理文件（不会回收到垃圾桶）

`git rm --cache` 和 `git reset HEAD` 的区别到底在哪里呢？

`git reset HEAD`: **用版本库内容清空暂存区** 
`git rm --cached` xxx: **只把特定文件从暂存区删除**
