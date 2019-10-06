# git学习笔记

[Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)

```shell
$ mkdir learngit  //创建空文件夹
$ cd learngit
$ pwd  //显示当前路径


$ git add readme.md  //区分大小写
$ git commit -m "annotation"
$ git status  //查看git是否被修改
$ git diff readme.md  //查看制定文件修改内容(commit之前)

$ git log
$ git log --pretty=oneline
$ git reset --hard HEAD^^
$ git reset --hard HEAD~2

$ git reset --hard 102f7ff  //直接用commit ID来回到之前或之后的版本，ID不需要输完整(4位即可)
$ git reflog  //获得各个版本的commit ID
```

### 撤销

#### 只是保存在工作区(working directory)，还未add到版本库(Repository)的暂存区(stage)

```shell
$ git checkout -- readme.md  //注意文件名与"--"之间会有空格，否则会被当做指令识别
```

命令`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，这里有两种情况：

* 一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

* 一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

#### 已经add到暂存区了但是还没commit

```shell
$ git reset HEAD readme.md  //把暂存区的修改回退到工作区。HEAD表示最新的版本。
$ git checkout -- readme.md
```

#### 已经commit

若还没有把自己的本地版本库推送到远程，可以用`git reset`回退到上一个版本

### 删除

1. 先删除一个文件

   * 直接删除
   * `$ rm test.txt`

2. 确实要删除这个

   ```shell
   $ git rm test.txt
   $ git commit -m "remove test.txt"
   ```

3. ```shell
   $ git checkout -- test.txt
   ```

   ==注意：从来没有被添加到版本库就被删除的文件，是无法恢复的！==

### 远程仓库

```shell
$ git remote add origin git@github.com:FUTURETECH6/Test.git
$ git remote add origin https://github.com/FUTURETECH6/Test.git


```

