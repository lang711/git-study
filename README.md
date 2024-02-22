# git学习

## 1. 追踪文件

`git add`文件或者目录的路径，添加到暂存区，如果是目录就跟踪该目录下所有文件，可使用路径正则

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222160525878.png)



## 2. 查看状态

`git status`查看当前的状态，加上--short或者-s得到更紧凑的状态信息 

-s输出中有两栏，左栏是暂存区的状态，右栏是工作区的状态

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222160304062.png)

## 3. 查看修改

`git diff`查看文件具体改动，对比工作区和暂存区的文件

--staged查看暂存区最后一次提交的文件

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222163016324.png)

## 4. 提交更新

`git commit -m`提交暂存区中的所有文件到本地数据库中

-a跳过`git add`环节，直接提交所有被追踪的文件

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222165343101.png)

## 5. 移除文件

- `git restore`文件或者目录，同`git add`，移除暂存区的文件

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222170450764.png)

- `git rm -f`文件，移除暂存区的文件并删除工作区的文件

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222171336262.png)

## 6. 重命名文件

`git mv 文件名a 文件名b`将文件名a重命名为b

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222171820593.png)

## 7. 查看日志

 `git log`查看提交更新的日志，-p 可以查看每次提交的差异，--stat每次提交的简略信息

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222172721331.png)

