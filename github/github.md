# git管理项目
## 1). 创建本地仓库
    创建.gitignore配置文件
    git init
    git add *
    git commit -m "xxx"
    
## 2). 创建github远程仓库
    New Repository
    指定名称
    创建
## 3). 将本地仓库推送到远程仓库
    git remote add origin https://github.com/zxfjd3g/170612_JSAdvance.git 关联远程仓库
    git push origin master

## 4). push本地的更新 
    git add *
    git commit -m "xxx"
    git push origin master
        
## 5). 克隆github上的项目:
    git clone https://github.com/zxfjd3g/170612_JSAdvance.git
        
## 6). pull远程的更新
	在克隆下的文件内部执行
    git pull origin master
    
## 7). 撤消本地修改
    git status  查看变化
    git checkout -- xxx文件  撤消指定文件的修改

## 8). 在pull远程更新时, 保留本地修改
	git add *
	git commit -m "xxx"
	git pull origin master
    

##9）. 在本地删除文件后，add 失败
	warning: You ran 'git add' with neither '-A (--all)' or '--ignore-removal',
	whose behaviour will change in Git 2.0 with respect to paths you removed.
	Paths like 'epet-app/src/mock/data.json' that are
	removed from your working tree are ignored with this version of Git.
	
	* 'git add --ignore-removal <pathspec>', which is the current default,
	  ignores paths you removed from your working tree.
	
	* 'git add --all <pathspec>' will let you also record the removals.
	
	Run 'git status' to check the paths you removed from your working tree.

	解决办法： git add -A  or  git add --all （忽略删除文件） 
			  git status  检测是否加到缓存区