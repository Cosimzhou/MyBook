git 笔记
========

git log --diff-filter=D --summary | grep delete #查看删除文件的记录

回退到历史的某一步，即使commit已不存在
git reflog
git reset xxxx

查看commit所属的分支
```
#查本地所有分支
git branch --contains <CommitID>
#查远程所有分支
git branch -r --contains <CommitID>
#查本地和远程的所有分支
git branch -a --contains <CommitID>
```


撤销文件
```
# 撤销文件的修改
git checkout <file> #撤销文件未在索引区中的修改

# 撤销add入索引区中的文件的修改
git reset HEAD <file>
git checkout <file>


# 撤销刚刚commit的文件的修改
git reset HEAD^
git checkout <file>

HEAD~n        # 顺序分支n级父节点
HEAD^2        # 合并分支的父节点，只有“2”有效
```






删除远程分支tag
git push origin --delete <branchName>        #删除远程分支
git push origin --delete tag <tagname>        #删除远程tag

否则，可以使用这种语法，推送一个空分支到远程分支，其实就相当于删除远程分支：
git push origin :<branchName>
这是删除tag的方法，推送一个空tag到远程tag：

git tag -d <tagname>
git push origin :refs/tags/<tagname>


无merge节点合并
git checkout <branch>
git rebase origin/<another branch>
# 冲突修复后 git add ，然后git rebase --continue
# 或者使用 git rebase --abort 恢复内容

#远端分支前置commit变动，本地同步
git fetch origin/<branch-name>
git reset [--hard] origin/<branch-name>


git mergetool <file> #修改conflict
窗口排布：

本地HEAD commit 共同祖先 commit 远程HEAD commit

当前工作区

git merge -Xignore-space-change <branch>


合并commit
git rebase -i HEAD~n        # 合并当前的n个commit
git rebase -i <commit id> # 合并commit id前的若干commit
\# 编辑时：第一个pick，之后squash，修改某一个edit
git commit --amend [<commit_title>] # 修改标题

git rebase -i

| 选项 [options] | 含义          |
| -------------- | ------------- |
| pick | 正常选中 |
| reword | 选中，并且修改提交信息；|
| edit | 选中，rebase时会暂停，允许你修改这个commit（参考这里） |
| squash | 选中，会将当前commit与上一个commit合并 |
| fixup | 与squash相同，但不会保存当前commit的提交信息|
| exec | 执行其他shell命令 |



git blame -L <line no> <file name> #看看这行代码赖谁？

git fetch origin <branch> #拉其它分支上的代码


```
显示commit id
git rev-parse HEAD                               #显示当前的commit id
git rev-parse —short HEAD                        #显示当前的commit短id
git rev-parse --show-toplevel                    #显示git的根目录

git log -1 --pretty=%h                           # 短commit id
git log -1 --pretty=%H                           # 全commit id
git symbolic-ref --short -q HEAD                 # master

git describe                                     # <tag>-<commit count>-g<commit id>
git describe --match "v[0-9]*" --abbrev=4 HEAD
git describe --dirty --match "software-v[0-9]*"
```


## 瘦身

先查找大文件，命令如下：
```
git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"
```

例如删除nspatientList1.txt文件：
```
git filter-branch --force --index-filter 'git rm -rf --cached --ignore-unmatch bin/nspatientList1.txt' --prune-empty --tag-name-filter cat -- --s
```

删除之后会有大量输出，显示已经从各自历史log中剔除掉关于这个大文件的信息，之后可以使用gc命令再次压缩:
```
git gc --prune=now
```



初始化

```bash
# 初始化方式一：
git clone git@git.github.com:<user>/<repository>.git
cd <repository>
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

# 初始化方式二：
cd <existing_folder>
git init
git remote add origin git@git.github.com:<user>/<repository>.git
git add .
git commit -m "Initial commit"
git push -u origin master

# 初始化方式三：
cd <existing_repo>
git remote rename origin old-origin    #已存在
git remote add origin git@git.github.com:<user>/<reposit>.git
git push -u origin --all
git push -u origin --tags
```



# 日常使用场景的命令
## 一、克隆
```
git clone git@host:group/repo                    #将host上git仓库里的group/repo项目克隆到本地
```


## 二、日常
```
git status                                       #列出未记入本次提交中的变动
git add .                                        #在本次提交中添加变动的所有文件
git add -A                                       #在本次提交中添加变动的所有文件
git commit -m "提交代码的标"                     #向“本地”代码库提交本次提交内容
git commit --amend                               #修改当前前的commit
git push                                         #将本地代码库推送至仓库服务器中
git pull                                         #从仓库服务器上拉取代码
git pull --rebase                                #从仓库服务器上拉取代码,不一致处进行rebase，而非merge
git rm <filename>                                #同时删除文件和对其的跟踪
=>  git rm --cached <filename>                   #删除对文件的跟踪，保留文件
git push origin <local branch>:<remote branch>   #提交本地<local branch>分支到远程<remote branch>
git push --set-upstream origin <local branch>    #提交本地<local branch>分支到远程
git push --force origin <branch>                 # 覆盖远程的分支

git clean -df   # 清理没有track的文件

# 使用远端内容
git fetch origin branch
git reset --hard origin/branch


git config --global user.name <username>
git config --global user.email <user email>

git config --global color.ui true

git config --get core.excludesfile
git config --global core.excludesfile ~/.gitignore_global  # 全局gitignore

git config --global diff.tool vimdiff
git config --global difftool.prompt false
git config --global alias.d difftool

```

## 三、分支
```
git branch                              #列出分支
git remote -v                           #列出git仓库的服务器路径
git branch <new-branch>                 #新建分支new-branch
git checkout <branch-name>              #切换到分支branch-name中去
git merge <other-branch>                #将其它分支合并到目前分支上去

git checkout <commit id>                #切换到<commit id>指出的提交记录中去
git checkout -b <branch name>           #创建并切换到<branch name> 指出的提交记录中去
git checkout HEAD^                      #切换到上一次提交中去
git checkout HEAD                       #切换到最后一次(最前端)提交中去
git checkout -                          #切回上一次使用的分支
git push origin --delete <branchName>   #删除远程分支

git checkout <file>                     #恢复git中的这个文件
```


也可以使用这种语法，推送一个空分支到远程分支，其实就相当于删除远程分支：

git push origin :<branchName>
这是删除tag的方法，推送一个空tag到远程tag：

git tag -d <tagname>
git push origin :refs/tags/<tagname>
两种语法作用完全相同。

解决冲突：
git checkout <file> --theirs    #使用远程修改覆盖本地
git checkout <file> --ours     #使用本地修改覆盖远程

```
<<<<<<<HEAD
<ours contents>
=======
<theirs contents>
>>>>>>>
```

## 四、异常处理
```
git revert HEAD                 #撤销上次前提交
git revert HEAD^                #撤销上上次前提交
git reset --hard                #将项目恢复到上次提交的状态（遗弃掉所有本次未提交完成的修改，不可恢复）
git reset HEAD                  #如果后面什么都不跟的话 就是上一次add 里面的全部撤销了
git reset HEAD <file>           #就是对某个文件进行撤销了
git stash                       #舍弃此次未提交的内容
git reset HEAD -- <file>        #将文件撤销到上次提交
```



# 更新fork 后的代码
首先要先确定一下是否建立了主repo的远程源：
git remote -v
如果里面只能看到你自己的两个源(fetch 和 push)，那就需要添加主repo的源：
git remote add upstream URL
git remote -v
然后你就能看到upstream了。
如果想与主repo合并：
git fetch upstream
git merge upstream/master

---------------------
子命令分类详述
==============

# submodule
git submodule add 仓库地址 路径
git submodule update --init --recursive

git submodule [--quiet] add [-b <branch>] [-f|--force] [--name <name>] [--reference <repository>] [--] <repository> [<path>]
git submodule [--quiet] status [--cached] [--recursive] [--] [<path>...]
git submodule [--quiet] init [--] [<path>...]
git submodule [--quiet] deinit [-f|--force] (--all| [--] <path>...)
git submodule [--quiet] update [--init] [--remote] [-N|--no-fetch] [-f|--force] [--checkout|--merge|--rebase] [--[no-]recommend-shallow] [--reference <repository>] [--recursive] [--] [<path>...]
git submodule [--quiet] summary [--cached|--files] [--summary-limit <n>] [commit] [--] [<path>...]
git submodule [--quiet] foreach [--recursive] <command>
git submodule [--quiet] sync [--recursive] [--] [<path>...]
git submodule [--quiet] absorbgitdirs [--] [<path>...]

删除submodule
0. mv a/submodule a/submodule_tmp
1. git submodule deinit -f -- a/submodule
2. rm -rf .git/modules/a/submodule
3. git rm -f a/submodule
# Note: a/submodule (no trailing slash)

# or, if you want to leave it in your working tree and have done step 0
3. git rm --cached a/submodule

# log命令
```
git log -S <keyword>                     # 搜索历史提交文本内容
git log -G <regex>                       # 搜索历史提交内容，按正则表达式
git log -p  <filename>                   #显示这个文件所有的修改提交
git log --pretty=oneline <filename>      #上一命令的完整形式
git log --oneline --graph --decorate
git show <commit id> [<filename>]        # 显示这次提交的这个文件是什么情况
git ls-files                             #列出所有管理的文件
```

git reflog 参数与git log 相同，可以将所有分支的记录都列出来
```
git reflog [show] [log-options] [<ref>]：就是显示同可引用的历史版本，同git reflog。就在后边可以加日志的选项。
git reflog expire [--expire=<time>] [--expire-unreachable=<time>] [--rewrite] [--updateref] [--stale-fix] [--dry-run | -n] [--verbose] [--all | <refs>…]：删除掉更老的reflog条目。
git reflog delete [--rewrite] [--updateref] [--dry-run | -n] [--verbose] ref@{specifier}…：从reflog中删除一个条目。
git reflog exists <ref>：检查一个ref是否有一个reflog条目
```

 --diff-filter=[(A|C|D|M|R|T|U|X|B)...[*]]
Select only files that are
Added (A), Copied (C), Deleted (D), Modified (M),
Renamed (R), have their type (i.e. regular file, symlink, submodule, ...) changed
(T), are Unmerged (U), are Unknown (X), or have had their pairing Broken (B).
mode


# grep

```
git grep 'time_t' -- '*.[ch]'
#Looks for time_t in all tracked .c and .h files in the working directory and its subdirectories.

git grep -e '#define' --and \( -e MAX_PATH -e PATH_MAX \)
#Looks for a line that has #define and either MAX_PATH or PATH_MAX.

git grep --all-match -e NODE -e Unexpected
#Looks for a line that has NODE or Unexpected in files that have lines that match both.

git grep solution -- :^Documentation
#Looks for solution, excluding files in Documentation.
```

# tag命令相关
```
git tag                                  #列出所有的tag标签
git tag <tag>                            #添加轻量级tag
git tag -l <expr>                        #列出与表达式匹配的tag
git tag -a <tag> -m <message>            #添加带消息的tag
git tag -d <tag>                         #删除tag
git show <tag>                           #显示tag内容
git push origin <tag>                    #将tag推到服务器上，普通的push是不会推tag的
git push origin --tags                   #将所有的tag推到服务器上
git push origin --delete tag <tagname>   #删除远程tag
```

# diff命令
```
git diff <branch A>..<branch B>            #显示两个分支间的差异
git diff <branch A>...<branch B>           #显示分支A、B共有父分支与分支B之间的差异
git diff [master]...<branch B>             #在master上执行时，B是从master建立的分支，则是显示分支B建立后有了多少修改
git diff 是一个难以置信的有用的工具，可以找出你项目上任意两点间 的改动，或是用来查看别人提交进来的新分支。
哪些内容会被提交(commit)
git diff用来找你当前工作目录和上次提交与本地索引间的差异。
git diff                                   #显示当前的工作目录里的，没有 staged(添加到索引中)，且在下次提交时不会被提交的修改。
如果你要看在下次提交时要提交的内容(staged,添加到索引中),你可以运行：
git diff --cached                          #显示当前的索引和上次提交间的差异；这些内容在不带"-a"参数运行 "git commit"命令时就会被提交。
git diff HEAD                              #显示工作目录与上次提交时之间的所有差别，所显示内容都会在执行"git commit -a"命令时被提交。
如果你要查看当前的工作目录与另外一个分支的差别，你可以用下面的命令执行:
git diff <branch>                          #显示当前工作目录与另外分支的差别。你也以加上路径限定符，来只比较某一个文件或目录。
git diff HEAD -- <filename/path>           #显示<filename/path>目录/文件与上次提交之间的差别
git diff --stat                            #统计一下有哪些文件被改动
```


分支Diff
```
git diff master..                          # 查看分支diff
git diff master.. <file>                   # 查看指定文件，从分支master当前的diff

	@@ -a,b +c,d @@ filename
# 与diff -u 的位置表述一致，含义如下：
# a旧文件的起始行数，b旧文件的行数
# c新文件的起始行数，d新文件的行数
```

## diff 打包补丁
```
git diff --cached > <patch>
git diff --HEAD > <patch>

# 应用补丁
git apply <patch>
git apply --check <patch>    # 预先检查
git apply --reject <patch>   # 将能打的补丁先打上，有冲突的会生成.rej文件
```

# stash命令
```
git stash
git stash push -m "leave message"
git stash save "what you want to say"

git stash apply              #应用stash
git stash list               #查看所有的搁置版本
git stash pop                #恢复一个stash
git stash pop <stash{n}>     #恢复一个指定的stash
git stash show <stash id>    #显示一个stash的git diff --stat
git stash drop <stash id>    #删除一个stash
git stash clear              #删除所有stash
```


# cherry-pick命令
```
git cherry-pick <commit id>

git checkout <old_cc>
git cherry-pick <commit id>     #
```




五、忽略跟踪内容
1、.gitignore规则
1. 以“/”开头表示目录；
2. 以“?”通配单个字符
3. 以“*”通配多个字符；
4. 以方括号“[]”包含单个字符的匹配列表；
5. 以叹号“!”跟踪某个文件或目录；
6. 前面的两个*号代表任意多层上级文件夹

git 对于 .gitignore 配置文件是按行从上到下进行规则匹配的，如果前面的规则匹配的范围更大，则后面的规则将不会生效；

2、示例：
规则：.DBStore/*
说明：忽略目录 .DBStore 下的全部内容；注意，不管是根目录下的 /.DBStore/ 目录，还是某个子目录 /lib/.DBStore/ 目录，都会被忽略；
规则：/upload/*
说明：忽略根目录下的 /upload/ 目录的全部内容；

规则：!.gitignore
跟踪 .gitignore 文件
说明：忽略全部内容，但是不忽略 .gitignore 文件



github 上建立新的仓库的步骤
echo "# <repository name>" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/Cosimzhou/<repository name>.git
git push -u origin master


其它小工具
# 类似 md5sum 或 sha1 的消息摘要工具
git hash-object --stdin



# 清理空格（及注释）
git stripspace --strip-comments


------------
# 类似的工具

SVN

略

skaffold

Skaffold handles the workflow for building, pushing and deploying your application, allowing you to focus on what matters most: writing code.

```
skaffold init
skaffold run
skaffold dev
```

