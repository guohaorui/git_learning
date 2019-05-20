# Git Learning 廖雪峰

## 创建版本库

``` 
$ git init
```

```
$ git add file
```

``` 
$ git commit -m "The change in this commitment"
```

## 版本控制

### 查看日志

``` 
$ git log 
```

可选参数一栏显示

```
$ git log --pretty=oneline
```

### 回退版本

利用HEAD表示当前版本，HEAD^ 表示上一个版本，HEAD^^ 表示上上个版本，HEAD~100 表上上100个版本

示例

```
$ git reset --hard HEAD^
```

要在不同版本之间穿梭，查到不同版本对应的commit id即可

+ 查看命令历史，以便确定不同版本的commit id

```
$ git reflog
```

+ 查到不同版本的commit id后穿梭版本

```
$ git reset --hard commit_id
```

### Working Directory & Repository & Stage $ Master

![1555309576095](C:\Users\Henry\AppData\Roaming\Typora\typora-user-images\1555309576095.png) 

``` 
$ git status 
```

可查看当前stage的情况

### 管理修改

commit只会将stage中的文件添加到master中，所以要上传文件首先要add到stage中

```
$ git diff HEAD -- readme.txt
```

可以看文件加了几行，删了几行

### 撤销修改

+ 改乱了工作区直接丢弃工作区的修改

```
$ git checkout -- readme.txt
```

结果会还原到stage或者master的版本

+ 改乱了工作区的内容并加到了stage

```
$ git reset HEAD <file>
```

就会到上个场景

+ 提交了不合适的修改到版本库，用版本回退，前提是没有推送到远程库



### 删除文件

```
$ git rm
```

```
$ git checkout -- file
```

命令`git rm`用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失**最近一次提交后你修改的内容**

## 远程仓库

### 添加远程库

```
$ git remote add origin git@github.com:guohaorui/git_learning.git
```

origin 相当于远程库在git中的名字

```
$ git push -u origin master
```

将本地库的所有内容推送（push）到远程库上

-u不但把本地master分支内容推送到远程新的master分支上，还会把本地的master和远程的master进行关联起来，以后推送或者拉取的时候就可以简化命令

```
$ git push origin master
```



### 从远程库克隆

```
$ git clone git@github.com:guohaorui/git_learning.git
```

要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。

Git支持多种协议，包括`https`，但通过`ssh`支持的原生`git`协议速度最快。

使用`https`除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用`ssh`协议而只能用`https`。
