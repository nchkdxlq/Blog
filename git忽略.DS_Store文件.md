## git忽略.DS_Store文件

在终端使用`git status`查看文件状态时，经常会出现名称为`.DS_Store`的文件，使用`git checkout .DS_Store`命令取消修改后，下次再次查看文件状态时又出现了。真的是赶都赶不走，特别的烦人。

在当前`git`仓库下修改`.gitignore`文件配置，如果没有该文件的话新建一个。在`.gitignore`中添加如下配置
```
#.DS_Store 这行为注释
.DS_Store
*/.DS_Store
```
保存退出即可。再次使用`git status`命令查看文件状态时，发现`.DS_Store`文件已经被忽略了。

但是，当你切换到其他的`git`仓库查看文件状态时，发现还有`.DS_Store`文件没给忽略。那这是怎么回事呢？原来上面设置只是针对单个`git`仓库的设置。假设有N的项目，需要一个一个设置，多么费劲。这时就需要一个全局的`gitignore`配置。

首先切换到当前用户的根目录`~/`。

1. 新建`.gitignore`文件（如果没有）。在文件中添加
```
#.DS_Store 这行是注释
.DS_Store
```
保存退出。

2. 新建`.gitconfig`文件（如果没有）。在文件中添加
```
[core]
excludesfile = ~/.gitignore
```
保存退出。

上面配置完成后，对所有的`git`仓库都生效。查看文件状态时，再也不会出现`.DS_Store`还没`git`管理的情况了。
**说明：如果设置了全局的`.gitignore`配置，单个`git`就不需要再配置了。**
