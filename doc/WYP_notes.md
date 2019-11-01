### 关于wyp操作中我遇到的问题

在师兄步骤2.2中，我在执行  `git remote -v` 

报错
`fatal: Not a git repository (or any parent up to mount point /home)
 Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).`

我执行了 `git init`，然后再执行`git remote -v`不再出现报错，但是什么都没有出现，我于是先进行了自己仓库（fork师兄后的仓库）远程的关联：

`git remote add origin git@github.com:wangyunpeng139/git_flow_test.git`

再次执行`git remote -v`，出现如下：

`wyp@wyp-pc:~/wyp_github/git_flow_try$ git remote -v
 origin	git@github.com:wangyunpeng139/git_flow_test.git (fetch)
 origin	git@github.com:wangyunpeng139/git_flow_test.git (push)
`

问题解决，然后再按照师兄的下几步开始一步步操作，先设置一个upstream

`git remote add upstream git@github.com:yhfeng1995/git_flow_test.git`

再继续执行`git remote -v`，问题解决，终于出现如下

`wyp@wyp-pc:~/wyp_github/git_flow_try$ git remote -v
 origin	git@github.com:wangyunpeng139/git_flow_test.git (fetch)
 origin	git@github.com:wangyunpeng139/git_flow_test.git (push)
 upstream	git@github.com:yhfeng1995/git_flow_test.git (fetch)
 upstream	git@github.com:yhfeng1995/git_flow_test.git (push)
`

感谢师兄～


## 2019-11-01 日笔记，最终版，前面的可以不看

`
$ git clone git@github.com:wangyunpeng139/git_flow_test.git
$ cd git_flow_test/
$ git remote -v
  origin	git@github.com:wangyunpeng139/git_flow_test.git (fetch)
  origin	git@github.com:wangyunpeng139/git_flow_test.git (push)


$ git remote add upstream git@github.com:yhfeng1995/git_flow_test.git
$ git remote -v
  origin	git@github.com:wangyunpeng139/git_flow_test.git (fetch)
  origin	git@github.com:wangyunpeng139/git_flow_test.git (push)
  upstream	git@github.com:yhfeng1995/git_flow_test.git (fetch)
  upstream	git@github.com:yhfeng1995/git_flow_test.git (push)

wyp@wyp-pc:~/wyp_github/git_flow_test$ git fetch upstream
来自 github.com:yhfeng1995/git_flow_test
 * [新分支]          develop    -> upstream/develop
 * [新分支]          master     -> upstream/master

$ git checkout master
   error: pathspec 'master' did not match any file(s) known to git.
 报错了，应该是没有变动的东西，这一步不管他。对后面没影响
 
 
$ git merge upstream/master
  Already up-to-date.

$ git push origin master
    error: src refspec master does not match any.
    error: 无法推送一些引用到 'git@github.com:wangyunpeng139/git_flow_test.git'
没有东西提交，也没有commit，所以会报错～～～

$ git flow init
  Which branch should be used for bringing forth production releases?
     - develop
  Branch name for production releases: []  
  Fatal: Missing branch name
  git flow feature start wyp_notes
  Fatal: Not a gitflow-enabled repo yet. Please run 'git flow init' first.
报错了～，不理会他，发现对后面没影响


使用师兄的方法建立分支(又报错了～～～)
$ git flow feature start wyp_notes
Fatal: Not a gitflow-enabled repo yet. Please run 'git flow init' first.

换一个方法建立分支（成功了～～）
$ git checkout -b feature/wyp_notes develop
  切换到一个新分支 'feature/wyp_notes'

$ git checkout develop
切换到分支 'develop'
您的分支与上游分支 'origin/develop' 一致
 
$ git pull
Already up-to-date.


$ git log feature/wyp_notes..develop

(下面两个可选，建议加上)，参考连接：[https://zhuanlan.zhihu.com/p/39148914]
$ git checkout feature/wyp_notes
   切换到分支 'feature/wyp_notes'
$ git rebase develop
  当前分支 feature/wyp_notes 是最新的。


分支推送，基本功能，所以师兄省略了详细细节
$ git add .
$ git commit -m "wyp's notes in the first"
   [feature/wyp_notes 1acb5fa] wyp's notes in the first
   1 file changed, 34 insertions(+)
   create mode 100644 doc/WYP_add.md
$ git push origin feature/wyp_notes
   对象计数中: 4, 完成.
   Delta compression using up to 8 threads.
   压缩对象中: 100% (3/3), 完成.
   写入对象中: 100% (4/4), 970 bytes | 0 bytes/s, 完成.
   Total 4 (delta 0), reused 0 (delta 0)
   To git@github.com:wangyunpeng139/git_flow_test.git
   256abbc..1acb5fa  feature/wyp_notes -> feature/wyp_notes
`
