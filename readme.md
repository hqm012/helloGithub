# github运行向导
1. 情况一：
github 上 new reposity 之后直接 clone 即可。强烈建议配置SSH后使用SSH方式拉取代码。情况一强烈推荐，情况二有太多其他复杂因素。
2. 情况二：
    1. 本地文件夹内运行：`git remote add origin git@github.com:hqm012/helloGithub.git` 这行命令的意思是：添加一个remote，name为origin，url为git@github.com:hqm012/helloGithub.git，name和url为必填项。
    2. 然后运行：`git branch -M main`，这行命令的意思是把正在工作的分支名重命名为main，例如git安装时默认为master分支，重新命名为main分支，否则需采用 `git push <remote> <source>:<destination>`，不推荐。如果不重命名，那么直接进行下面步骤3则会把写的source设为默认分支
    3. 最后运行 `git push -u origin main` 即可把内容push到github上，第一次使用push命令需要带上 -u 配置项，全称为 --set-upstream 设置上游，也可以使用`git push -u <remote> <source>:<destination>`，不推荐。需要注意的是：如果此时本地没有进行任何提交，会不存在refs，无法进行第三步。

## git push 骚操作
 `git push -u <remote> <source>` source是本地的，如果远程source不存在，则会在远程仓库新建一个source。如果该远程仓库是第一次提交，则会把source设为默认分支。
 `git push <remote> <source>:<destination>` 如果不写source则把远程的destination删除了，例如`git push origin :other` 会把远程的other分支删除，但不能删除远程的默认分支

## git pull
git pull 拉取的是本地没有的commit，如果本地已存在远程上所有的commit则不会有任何改变。
git pull 也可以使用 <source>:<destination> ，git pull orgin main:foo，会使本地的foo分支拉取远程main分支所有的commit，这种<source>:<destination>方式都不推荐使用，会造成可读性大大降低。