查看所有的全局配置项
git config --list --global

查看指定全局配置项
git config user.name
git config user.email

想打开git config 命令帮助手册
git help config

想获取 git config 命令的快速参考
git config -h

[未跟踪 未修改 已修改 已暂存]

在目录中初始化一个git仓库
git init

检查文件状态	[出现在Untracked files下面的是未跟踪的文件]
git status
以精简的方式显示文件的状态	[为跟踪的文件前面有??标记]
git status -s
git status --short

查看本地库
ll

创建文件
vim hellow.txt
【yy是复制	p是粘贴		:wq保存】

查看文件内容
cat hellow.txt

查看文件末尾的第一行
tail -n l hellow.txt


----------------------------------------------------------------------

【Git标准工作流程是 工作区——>暂存区——>Git仓库】
* 跟踪文件，将其加入暂存区	A
git add "index.html"

* 提交，加入git仓库中
git commit -m "新建了index.html"

[红M 已修改	绿M 已修改且已放到暂存区]

* 跳过使用暂存区域 【这样写可以不用将改后的文件放入暂存区再提交】
git commit -a -m "修改后提交的index.html"	

* 撤销对文件的修改【其实就是将git仓库中的文件将工作区已修改的文件覆盖掉】
git checkout -- index.html

* 向暂存区一次性添加多个文件
git add .

* 移除暂存文件
git reset HEAD 要移除的文件名
git reset HEAD . 暂存区文件全部移除

* 从Git仓库和工作区中同时移除index.js文件
git rm -f index.js
* 只从Git仓库中移除index.css,但保留工作区中的indedx.css文件
git rm --cached index.css

------------------------------------------------------------------------

忽略文件（一般创建一个名为.gitignore的配置文件）
1.以#开头的是注释
2.以/结尾的是目录
3.以/开头防止递归
4.以！开头表示取反
5.可以使用glob模式，进行文件和文件夹的匹配
：指简化了的正则表达式
	1. * 匹配零个或多个任意字符
	2. [abc] 匹配任何一个列在方括号中的字符（此处指：匹配a，或匹配b，或匹配c）
	3. ？只匹配一个任意字符
	4. [0-9] 匹配所有0到9的数字
	5. ** 表示匹配任意中间目录（比如a/**/z,可以匹配a/z 或  a/b/c/z）

按时间先后顺序列出所有的提交历史，最近提交的排在最上面
git log
只显示最新的两条提交历史
git log -2
在一行上展示最近两条提交历史的信息
git log -2 --pretty=oneline
%h 提交的简写哈希值	%an 作者名字	%ar 作者修订日期	%s 提交说明
git log -2 --pretty=format:" %h | %an | %ar | %s "

回退指定版本
git reset --hard ID
在旧版本中使用git reflog --pretty=online  查看全提交历史

--------------------------------------------------------------------------

查看所有分支列表
git branch

创建新分支
git branch 分支名称

切换分支
git checkout 分支名称

创建分支，并切换到创建的分支上
git checkout -b 分支名称

合并分支
git checkout master	切换到主分支
git merge 分支名称	合并分支
遇到冲突时的分支合并（注：分支与master不同，需主动解决冲突	不论是分支还是master修改后都必须放入暂存区，不然无法合并）

删除分支
git branch -d 分支名称