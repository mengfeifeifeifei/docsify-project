**配置name email**
```json
git config --blobal user.mail "email@example.com"

git config --blobal user.name "example"
```

**上传项目**
```json
1.首先在项目文件夹下执行初始化  
  git init

2.查看当前状态  
  git status

3.将本地仓库关联远程仓库
  git remote add origin git@github.com:qingjiaowonanshenfei/docsify-project.git

4.拉取远程仓库到本地
  git pull --rebase origin master

5.添加暂存区
  git add . (.代表所有修改的文件)
  git commit -m 'xxx'

6.提交
  git push -u origin master
```

**常用**
```json
1.查看所有分支
  git branch -a

2.切换某个分支
  git checkout 分支名称

3.合并分支
  git merge 原分支 目标分支

4.创建本地分支
  git branch demo

5.删除远程分支
  git push origin demo (git push origin --delete demo)
```


