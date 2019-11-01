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

