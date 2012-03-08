# git 使用:

* 权限管理器 Gitosis 安装

  ```
$ yum install python-setuptools      //python工具
$ git clone git://eagain.net/gitosis.git
$ cd gitosis
$ sudo python setup.py install
/git/repositories/gitosis-admin.git/gitosis-export/gitosis.conf 
文件是用来设置用户、仓库和权限的控制文件。
/git/repositories/gitosis-admin.git/keydir
目录则是保存所有具有访问权限用户公钥的地方
  ```
        
* clone分支

  clone获取的git库,只包含了当前工作分支,如想获取其他分支信息,需要使用"git branch -r"来查看,
    然后"git checkout -b 本地分支名 远程分支名",如果本地分支已经存在,则不需要"-b"参数.
    eg: git branch -r
        git checkout -b 本地分支名 origin/远程分支名
        
* 常用命令:
    
    git remote prune remote_branch
        删除远程all stale tracking分支
        
    git remote rm remote_branch
        删除所有分支

  ```
$ git remote
    origin
$ git branch -r
    origin/master
$ git remote add linux-nfs git://linux-nfs.org/pub/linux/nfs-2.6.git
$ git remote
    linux-nfs
    origin
$ git fetch
    * refs/remotes/linux-nfs/master: storing branch 'master' ...
    commit: bf81b46
$ git branch -r
    origin/master
    linux-nfs/master
$ git checkout -b nfs linux-nfs/master
  ```  

### gitHub上的操作:
Download and install Git

    
  ```
$ git config --global user.name "chaing"
$ git config --global user.email chaing@gmail.com
  ```

Next steps:

```
$ mkdir myGit
$ cd myGit
$ git init
$ touch README
$ git add README
$ git commit -m 'first commit'
$ git remote add origin git@github.com:chaing/myGit.git
$ git push origin master
```

Existing Git Repo?

  ```
$ cd existing_git_repo
$ git remote add origin git@github.com:chaing/myGit.git
$ git push origin master
  ```

* 初始化一个本地库:

  ```
$ git init myGit
  ```

* 查看状态:

  ```
$ git status
  ```
  
* 添加跟踪文件:

  ```
$ git add file-name
  ```
  
* 提交到本地库:
* 
  ```
$ git commit -m "init mygit"
  ```
  
* 创建分支:

  ```
$ git branch branch-name
  ```
  
* 转换到分支:

  ```
$ git checkout branch-name
  ```
  
* 删除分支:

  ```
$ git branch -D branch-name
  ```
  
* 查看分支:

  ```
$ git branch
  ```

* 详细情况:

  ```
$ git show-branch
  ```
  
* 比较当前工作目录和版本库中数据的差别:

  ```
$ git diff
  ```
  
* 合并两个分支:

  ```
$ git checkout master
$ git merge "Merge work in robin" HEAD branch-name
  ```