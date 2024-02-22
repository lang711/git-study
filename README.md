# git学习

## 1. 追踪文件

`git add`文件或者目录的路径，如果是目录就跟踪该目录下所有文件，可使用路径正则

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

-a跳过`git add`环节，直接提交所追踪的文件

![](C:\Users\32894\AppData\Roaming\Typora\typora-user-images\image-20240222164920469.png)