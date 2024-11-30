# git book 学习记录

## 查看git配置变量

命令：**git config --list ** ，通过设置不同选项可以查看不同权限的配置。

1. **--system**：查看系统中每个用户的配置
2. **--global**：查看当前用户的配置
3. **--local**：查看当前仓库的配置

> 就近原则，距离仓库越近的配置会覆盖越远的配置。

设置选项**--show-origin**：可以查看所有git配置文件的路径，查看当前仓库的配置文件路径：**git config --local --show-origin**

## 设置或修改git配置变量

命令：**git config --global user.name 'fan_ren' **，给当前用户配置添加或修改变量。

> 特别注意：*值的设置需要在选项后面*

## 删除git配置变量

命令：**git config  unset --global user.name**，删除当前用户配置的变量。

## git 获取帮助

1. **git help config **：获取命令*git config*的帮助手册。
2. **git config --help**：同样也是获取命令*git config*的帮助手册。
3. **git config -h**：获取命令*git config*的快速参考。

## git 获取仓库

1. 将未进行版本控制的本地目录转成git仓库：
   - 首先进入到本地目录，**cd /test**
   - 接着执行git初始化命令，**git init**
   - 然后把文件添加到暂存区，**git add test.txt**
   - 最后提交到git本地仓库，**git commit -m '初次提交'**
2. 从远程服务器**克隆**一个现有的git仓库：
   - 到[Github](https://github.com/)或者[Gitee]([Gitee - 基于 Git 的代码托管和研发协作平台](https://gitee.com/))任意项目页下面的*code*复制项目地址
   - 然后执行git克隆命令，**git clone  https://github.com/lang711/git-study.git  git-test**，默认目录名为*git-study*，更改下载目录名为*git-test*

## git 术语

1. *未修改（Unmodified）或者已跟踪（Tracked）*：指已经纳入版本控制的文件，已跟踪，但没有被修改。

2. *未跟踪（Untracked）*：指没有纳入版本控制的文件。比如新建一个文件，该文件就属于未跟踪。

3. *工作区（Workspace）*：指开发者写代码的目录。

4. *暂存区（Stage）*：指所有已暂存文件的记录。

5. *git本地仓库（Repository）*：指本地电脑上记录所有版本的数据库。

6. *已修改（Modified）*：指未修改的文件被修改。

7. *已暂存*（Staged）：指已修改或者未跟踪的文件被添加到暂存区。

8. *已提交（Commited）*：指暂存区的文件被提交到git本地仓库，文件状态变成未修改。

   ![Git 下文件生命周期图。](https://git-scm.com/book/zh/v2/images/lifecycle.png)

## 查看工作区的文件状态

命令：**git status**

![image-20241129183119077](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129183119077.png)

上图显示当前处于master分支上，有一个*test1.txt*文件未跟踪，提示用*git add*去跟踪*test1.txt*文件。

设置选项**-s**，可以显示更简略的状态信息：

![image-20241129191530896](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129191530896.png)

上图显示，左边是状态信息，右边是文件信息。状态信息分为两栏，左边表示暂存区状态，右边表示工作区状态。

- **A**：表示已添加到暂存区
- **M**：表示已跟踪文件被修改
- **??**：表示未跟踪
- **R**：表示重命名文件

## 跟踪新文件

命令：**git add test1.txt**，跟踪*test1.txt*文件并会添加到暂存区，如果是目录，则跟踪目录下所有文件并添加到暂存区。

![image-20241129183408039](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129183408039.png)

> 没有提示信息表示命令执行成功，**但并不表示命令如愿生效**

上图显示在master分支上，变化可以被提交，提示用*git restore*去撤销暂存，会变成未跟踪状态。

## 暂存已修改的文件

当修改已跟踪文件，状态会改变成已修改。下图显示在master分支上，变化没有被暂存，不能提交，提示用*git add*去暂存修改，或者用*git restore*放弃修改。

![image-20241129184804169](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129184804169.png)

命令：**git add test1.txt**，添加已修改的文件*test1.txt*到暂存区。

![image-20241129185817012](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129185817012.png)

## 忽略文件（.gitignore）

*格式规范*：

- 所有空行或者以#开头都会被忽略
- 使用简化的正则表达式匹配规则
- 匹配规则可以以**/**开头防止递归，表示从当前目录下匹配
- 匹配规则可以以**/**结尾指定目录，表示忽略指定目录下所有文件
- 忽略匹配规则可以在规则前加上**!**

*简化的正则表达式*：

- *****：匹配任意字符。
- **?**：匹配一个字符。
- **[abc0-9]**：匹配列出的其中一个字符。*0-9*表示从0到9。
- ******：匹配中间任意目录。

## 查看修改文件差异

命令**git diff**，可以查看暂存区和工作区的文件补丁。

![image-20241129200152525](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129200152525.png)

设置选项**--staged**，可以查看最后一次提交与暂存区的文件补丁。

![image-20241129200834830](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129200834830.png)

## 提交暂存区

命令**git commit**，会弹出[**vim编辑器**](https://www.runoob.com/linux/linux-vim.html)，可以输入提交说明，已修改没有被暂存的仍然保持已修改状态。

![image-20241129201846998](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129201846998.png)

![image-20241129202606150](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129202606150.png)

设置选项**-m**，也可以直接输入提交说明。

![image-20241129203014920](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129203014920.png)

设置选项**-a**，相当于添加到暂存区再提交。

![image-20241129204555472](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129204555472.png)

## 移除文件

命令**git rm**

1. 手动删除工作区的文件，需要再把删除操作添加到暂存区：

   ![image-20241129205841061](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129205841061.png)

2. 使用命令**git rm test1.txt**删除，删除操作会直接被添加到暂存区：
   ![image-20241129205933924](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129205933924.png)

3. 使用选项**--cached**，会从暂存区还原成未跟踪状态：

   ![image-20241129211213468](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129211213468.png)

4. 使用选项**-f**，会强制删除文件，不会记录删除操作，也不能恢复文件：

   ![image-20241129211517325](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129211517325.png)

## 重命名（移动）文件

命令**git mv test1.txt test2.txt**，将*test1.txt*重命名为*test2.txt*，并将重命名操作添加到暂存区。

![image-20241129212735046](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129212735046.png)

其实相当于执行了

```cmd
mv test1.txt test2.txt
git rm test1.txt
git add test2.txt
```

## 查看提交历史

1. 命令**[git log](https://git-scm.com/book/zh/v2/Git-基础-查看提交历史)**，查看由近到远的提交记录。

   ![image-20241129213954015](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129213954015.png)

2. 设置选项**-p**，可以查看每次提交相对于上一次提交的补丁。

   ![image-20241129214140088](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129214140088.png)

3. 设置选项**--stat**，可以查看每次提交的总结，总结文件改变信息。

   ![image-20241129214325210](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129214325210.png)

4. 设置选项**--graph**，可以查看分支、合并历史。

   ![image-20241129220213231](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129220213231.png)

5. 设置选项**--pretty=oneline**，可以在一行中查看每次提交的哈希值。设置选项**--pretty=format:"%an"**，可以查看每次提交的作者。

   ![image-20241129221059072](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129221059072.png)

   ![image-20241129221620344](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129221620344.png)

6. 设置选项**--since=120.minutes**，可以查看2小时前的提交记录。

   ![image-20241129221225875](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129221225875.png)

   

## 撤销操作

1. 撤销提交：当还有一些文件没有提交或者提交说明做补充时，可以使用**git commit --amend**来替换上次提交。

   ![image-20241129222713712](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129222713712.png)

2. 撤销暂存。

   ![image-20241129223408429](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129223408429.png)

3. 撤销文件修改，会丢失数据。

   ![image-20241129223154656](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129223154656.png)

## 查看远程仓库

1. 命令**git remote**，查看所有远程仓库。![image-20241129235211570](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129235211570.png)设置选项**-v**，可以查看远程仓库名和读写仓库的地址。![image-20241129235347277](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129235347277.png)

2. 命令**git remote show origin**，查看远程仓库origin信息。

   ![image-20241130001636581](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130001636581.png)

## 添加远程仓库

命令**git remote add duyi https://github.com/lang711/duyi-allPhase.git**，添加远程仓库*duyi*。

![image-20241129235802182](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241129235802182.png)

## 重命名远程仓库

命令**git remote rename duyi duer**，给*duyi*重命名为*duer*。

![image-20241130001952222](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130001952222.png)

## 移除远程仓库

命令**git remote remove duer**，移除远程仓库*duer*。

![image-20241130002059445](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130002059445.png)

## git命令设置别名

本质就是简单的将别名替换成对应的命令。

1. 简单命令：

   ![image-20241130014146443](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130014146443.png)

2. 复杂命令：

   ![image-20241130014039717](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130014039717.png)

   > 设置复杂命令，***必须使用双引号包含值***

## 创建标签

1. 附注标签，命令**git tag -a v2.0 1f97c6d6f -m '最新版本'**，给*1f97c6d6f*的提交打上标签*v2.0*，并且添加标签说明*最新版本*。

   ![image-20241130015407440](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130015407440.png)

2. 轻量标签，直接**git tag v1.9 b58db017**，给*b58db017*的提交打上标签*v1.9*，仅仅只是某次提交的引用。

   ![image-20241130015915927](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130015915927.png)

3. 创建远程标签：**git push origin v2.0**，将本地*v2.0*推送到远程仓库origin的*v2.0*。

   ![image-20241130021223543](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130021223543.png)

## 删除标签

命令**git tag -d v2.0**，删除标签*v2.0*

![image-20241130020402206](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130020402206.png)

删除远程标签：**git  push origin --delete v2.0**，删除远程仓库origin的*v2.0*。

![image-20241130021450475](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130021450475.png)

## 查看标签

命令**git show v1.9**，查看标签*v1.9*所引用的提交。

![image-20241130020559050](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130020559050.png)

查看本地所有标签：**git tag**![image-20241130020824482](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130020824482.png)

## 切换标签

命令**git checkout v1.9**，*HEAD*指针不再指向master，而是指向*v1.9*代表的提交。

![image-20241130022008788](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130022008788.png)

## 创建分支

命令**git branch test**，创建*test*分支。

![image-20241130204205102](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130204205102.png)

> master分支也只是普通分支，可以在配置中改变

## 切换分支

命令**git checkout test**，切换到*test*分支。

![image-20241130204616537](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130204616537.png)

设置**-b**，会创建分支并切换到该分支。

![image-20241130210100570](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130210100570.png)

## 删除分支

命令**git branch -d next**，删除*next*分支。

![image-20241130211114945](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130211114945.png)

> 不能在当前分支去删除当前分支

## 合并分支

命令**git merge next**，分支*master*合并分支*next*。

![image-20241130214436743](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130214436743.png)

合并冲突。

![image-20241130211807005](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130211807005.png)

变基，复制分支然后追加。命令**git rebase master**

![image-20241130233106806](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130233106806.png)

## 查看分支

命令**git branch**，查看所有分支。

![image-20241130214729343](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130214729343.png)  

> *代表HEAD指针指向该分支

设置选项**-v**，可以查看所有分支最后一次提交。

![image-20241130214954559](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130214954559.png)

设置选项**--merged**，可以查看已经合并了的分支。

![image-20241130215149272](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130215149272.png)

## 抓取数据

命令**git fetch origin**，命令**git pull**会在*fetch*之后进行*meige*。

1. 从远程仓库*origin*抓取本地没有的数据。
2. 更新远程跟踪分支*origin/master*。

![远程跟踪分支 `teamone/master`。](https://git-scm.com/book/zh/v2/images/remote-branches-5.png)

## 推送数据

1. 推送分支：**git push origin master:main**，将本地仓库master分支推送到远程仓库main分支。

   ![image-20241130231701787](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130231701787.png)

2. 删除远程分支：设置选项**--delete**。

   ![image-20241130231622365](C:\Users\fan-ren\AppData\Roaming\Typora\typora-user-images\image-20241130231622365.png)



