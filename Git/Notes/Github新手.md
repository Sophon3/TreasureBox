## github上传项目方法

### 第一种

```python
1: 进入项目文件夹，用git bush打开
2：git init    #将这个文件夹变成git可管理的仓库
3：git add .   #将项目中的文件添加到仓库
4：git status  #查看当前的状态
5：git commit -m "注释" #把项目提交到仓库
#这里已经完成了本地git仓库的工作了
#之后在github上面建立好仓库
6：git remote add origin 仓库地址 #将GitHub上的仓库与本地仓库关联
（7）：git pull --rebase origin master #如果GitHub上建立的仓库添加了README等文件，需要先将GitHub仓库的内容下载下来
7：git push -u origin master #第一次上传仓库是空的所以需要添加-u，这里的master
8:git push origin master #之后的上传
########################################################################
# 注意github的分支，2020年之后github的默认分支由master改为main,而git的默认分支依然为master，也可以在github的setting中修改
#可以git config --global init.defaultBranch main  修改为main分支，同样也能改为其他分支。
#######################################################################
git --version #查看git版本
删除本地分支：git branch -d 分支名称
强制删除本地分支：git branch -D 分支名称
删除远程分支：git push origin --delete 分支名称

```



### 第二种