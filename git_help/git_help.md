----------
# 概述
----------
## 年度状态分析
	https://octoverse.github.com/
## 证书license
![（加载失败）git证书说明](https://raw.githubusercontent.com/xuanshengmail/pictures/master/picgo/git-license-protocol.png)
## 配置ssh
	1. ssh-keygen -t rsa -C "your email"
	2. cd ~/.ssh
	3. copy the (public key) content of file id_rsa.pub
	4. sign in your github
	5. new a ssh key
	6. paste the content
## 配置github图床
	1. 新建一个空仓库
	2. 账户设置中develop settings中为picgo申请token
	3. 在picgo中配置github图床
	4. ctrl+shift+p上传图片
	5. 直接粘贴剪贴板中的链接  
## markdown语法
	1.<pre class="prettyprint"><code class="language-java">  [代码]  </code></pre>用来环绕代码块
	2. ` [代码] `用来环绕一行中某些部分属于代码的情况
	3. <!-- [注释] -->用来环绕注释内容
	4. <p align='center'>  [内容]  </p>用来环绕居中内容
	5. 表格语法：
|这是|一个|表格|
|:----|:----:|----:|
|foefowewewewj|wefweweqweegg|fwegqweqwewegwe|
|左对齐|居中对齐|右对齐|
	6. checkbox效果列表
- [] list1
- [x] list2
- [] list3

----------
# 命令
----------
## 账户初始化

### 显示所有的配置信息
	git config --list

### 配置提交仓库时：用户名
	git config --global user.name 'your_name'

### 配置提交仓库时：邮箱
	git config --global user.email 'your_email'

## 别名
### 命令方式添加别名
	git config --global alias.ci commit
### 修改.gitconfig文件
	通过命令方式添加一条后，按照原有格式在~./.gitconfig文件中直接添加其他别名

## 新建仓库

### 文件夹中初始化为本地空仓库
	git init

### 通过github初始化本地仓库
	git clone [url]

## 添加删除文件

### 文件添加到暂存区
	git add [file1] [file2]
	git add -p
		s (分片选择)

### 删除文件，并影响暂存区
	git rm [file1] [file2]

### 改名文件，并影响暂存区
	git mv [file-origin] [file-renamed]

### 清空当前目录中未跟踪文件
	git clean -n (列出目标文件)
	git clean -f (删除未跟踪文件)
	git clean -d (删除未跟踪文件夹)

## 代码提交
### 通过.gitignore文件增加白名单
	该白名单文件本身是需要进行版本控制的
	在.gitignore中增加来忽略某些或者某类文件的版本控制
<pre class="prettyprint"><code class="language-java">
# ignore these temp file
*.obj
*.exe
</code></pre>
### 允许提交有混合换行符的文件
	git config --global core.safecrlf false

### 暂存区提交到本地仓库
	git commit -m [message]

### 工作区直接提交到本地仓库
	git commit -a -m [message]（前提是仓库中已有该文件版本）
### 提交信息的编写规范
	1. git commit（此时弹窗可编写多行提交信息）
	2. 规范:
			<type>(<scope>):<subject>
			//空一行
			<body>
			//空一行
			<footer>
			
			//说明：
			- type:
				* feat(新增功能)  
				* fix(修复bug)
				* docs(修改文档)
				* style(更改格式)
				* refactor(重构代码)
				* test(增加测试)
				* chore(辅助工具的变动)
			- scope：
				* 影响的范围或者文件
			- subject：
				* 主题，大致描述本次修改的内容
			- body:
				* 主体，详细描述修改的内容（可省略）
			- footer
				* 尾注，用户关闭issue (比如：close #4)
				
			@（type+scope+subject不可超过70个字符，否则git log会换行）
## 查看状态

### 查看变更信息
	git status

### 显示当前分支的历史版本
	git log (整个仓库的)
	git log [filename]
	git log -n (只显示最近n个commit)
	git log --oneline （简要地行显示）
	git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short

### 查看历史提交的具体更改
	git show [old version hashCode]
	git show HEAD[~<0-X>]

### 查看文档中每一行的提交信息
	git blame [filename]
	git blame -L startLine,endLine [filename]
### 查看不同版本中间的区别
![（加载失败）git证书说明](https://raw.githubusercontent.com/xuanshengmail/pictures/master/picgo/git-diff.jpg)

## 同步远程仓库

### 查看链接的远程仓库
	git remote -v

### 与远程仓库建立连接
	git remote add [shortname] [github——url]

### 本地仓库内容提交到远程仓库
	git push [shortname] [local——branch]

### 将远程仓库内容拉取到本地
	git pull [shortname] [local——branch]

## 回撤操作
### 仓库到暂存区
	git reset [HEAD] --soft (融合)
### 暂存区到工作区
	git reset HEAD (融合)
	git checkout (覆盖)
### 仓库到工作区
	git reset [HEAD] --hard (覆盖)
### 回撤动作同步到远程仓库
	git push -f
### 变基操作
	git rebase -i HEAD[~3]

## 标签操作
### 列出所有标签
	git tag
### 打标签
	git tag tagname [hashcode]
### 打标签时加入标签详细信息
	git tag tagname [hashcode] -m "tag message"
### 删除标签
	git tag -d tagname
### 标签推送到远程仓库
	git push origin --tags  (所有标签)
	git push origin tagname (某个标签)
## 分支操作
![](https://raw.githubusercontent.com/xuanshengmail/pictures/master/picgo/git-branch.jpg
)
### 创建分支
	git branch brname
### 切换工作分支
	git chechout brname
### 创建并切换分支
	git chechout -b brname
### 修改分支名字
	git branch -m oldname newname  (有错误会提示)
	git branch -M oldname newname （新的名字有冲突不会提示,强制执行）
### 删除分支
	git branch -d brname (未合并，会提示)
	git branch -D brname (未合并，不提示，直接删除)
### 查看分支
	git branch -v 			(本地所有分支)
	git branch -r 			(远程所有分支)
	git branch --merged     (本地未已合并分支)
	git branch -r --merged （远程已合并分支）
	git branch --no-merged  (本地未合并分支)
### 取出远程分支
	git chechout -t origin/brname
### 推送分支到远程
	git push -u origin brname
### 删除远程分支	
	git push origin <space>:<remote branch>
	git fetch -p
### 合并分支
	git merge <brname>

## 冲突
### 条件
	在不同的分支上，修改同一个文件
	同一分支上，不同的人，修改了同一个文件
	不同的仓库，修改了同一个文件
### 注意
	冲突只在合并分支的时候才会发生
	发生冲突并不可怕，冲突的代码并不会丢失
### 解决冲突的办法
	git status查看发生冲突的文件
	对冲突文件做修改
	重新提交，commit时不要加-m给message信息

## stash操作
### 保存进度
	git stash
### 弹出进度
	git stash pop
### 查看stash列表
	git stash list
### 删除stash列表
	git stash clear
## 解决git clone 下载慢问题
	1，在阿里云服务器上git clone下来
	2，zip dst -r 目录
	3，从阿里云上下载下来并解压
	4，执行git remote rm origin
	5, 执行git remote origin 远程仓库URL