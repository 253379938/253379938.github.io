---
title: Git
date: 2024-12-08 20:45:53
categories:
  - Git
tags:
  - Git
---

**Git 是一个免费的开源分布式版本控制系统，旨在处理从小型到 快速高效的超大型项目。**

<h4 id="Pqf5c">Git的安装</h4>

git官网:[Git](https://git-scm.com/)

:::tips
// 查看git版本

git -v

初次使用git需要配置用户名和邮箱

git config --global user.name "Jasper Yang'

git config --global user.email geekhall.cn@gmail.com

![](./Git/1732771915677-78ecf971-8142-462c-b6b9-5a373d49bf58.png)

查看配置的信息

git config --global --list

:::

<h4 id="fTdbq">Git的使用</h4>
<h5 id="JOa9i">新建仓库</h5>

:::tips
方式一 : git init     //本地初始化仓库

方式二 : git clone  //远程克隆仓库

:::

<h5 id="hFwcB">工作区域和文件状态</h5>
<details class="lake-collapse"><summary id="ua24441b2"><span class="ne-text">工作区域</span></summary><p id="u3b49bc67" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732772549334-abaf791a-542c-4983-a1d2-867486e8e86d.png" width="992" id="aZ7t4" class="ne-image"></p></details>
<details class="lake-collapse"><summary id="uee52c5b5"><span class="ne-text">文件状态</span></summary><div data-type="tips" class="ne-alert"><p id="u561971f1" class="ne-p"><span class="ne-text">未跟踪:新创建的,未被git管理的文件</span></p><p id="u0da2fac8" class="ne-p"><span class="ne-text">未修改:已被git管理,文件内容未被修改的文件</span></p><p id="u08e46a05" class="ne-p"><span class="ne-text">已修改:已修改,未被添加到暂存区的文件</span></p><p id="u9bca1ca2" class="ne-p"><span class="ne-text">已暂存::已被添加到暂存区的文件</span></p></div><p id="uab356d06" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732772735047-29d7e85d-498d-40fb-b91e-46b3c66075ed.png" width="1031" id="ubd7274c1" class="ne-image"></p><p id="ue1be15a2" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732783489100-cdccaa59-036a-4abf-b29d-f532460549be.png" width="420" id="u81d4ee70" class="ne-image"></p></details>
<h5 id="APnI7">添加和提交文件</h5>

:::tips
git init       创建仓库

git status   查看仓库

git add       添加到暂存区

git commit 提交

git log        查看历史提交记录

:::

<h5 id="iWAqB">git reset 回退版本</h5>
<details class="lake-collapse"><summary id="u74de697a"><span class="ne-text">git reset</span></summary><p id="u94caa391" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732773470015-e79cce61-fadd-4408-9f81-6ab750c4fb60.png" width="1066" id="uba69f707" class="ne-image"></p></details>

:::tips
ls 查看工作区所有文件

ls -a 查看工作区所有文件(包括隐藏文件)

git ls-liles 查看暂存区所有文件

:::

:::tips
谨慎使用 --hard 会删除两个版本之间的工作区和暂存区

若误操作删除,可以使用git reflog 查看操作的历史记录,然后使用git reset 回退到误操作前的版本

:::

<h5 id="PxRXz">git diff</h5>
<details class="lake-collapse"><summary id="u7ac941aa"><span class="ne-text">git diff</span></summary><p id="u6480e4f4" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732774168228-3499e932-da8b-495f-9298-8c4ff7992573.png" width="1055" id="u0ffa9351" class="ne-image"></p></details>

:::tips
//  HEAD 指向分支的最新提交节点

git diff    默认查看工作区和暂存区的差异

git diff HEAD  查看工作区和版本库的差异

git diff --cached 查看暂存区和版本库的差异

git diff <ID> <ID> 查看两次版本库的差异

git diff <ID> <ID> <flie> 查看两次版本库中某个文件的差异

:::

<h5 id="zUsvn">git rm</h5>
<details class="lake-collapse"><summary id="u14cc557a"><span class="ne-text">git rm</span></summary><p id="uf61798a2" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732775143522-e8eb1bcf-e989-49cb-9d6f-3705c6524b45.png" width="1074" id="ud26482dc" class="ne-image"></p></details>


<h5 id="nJvyJ">.gitignore</h5>
<details class="lake-collapse"><summary id="u64ee3d8f"><span class="ne-text">.gitignore</span></summary><p id="u3faf5e9a" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732775241241-3856ded3-d183-455f-bdbc-3862bfc32acd.png" width="1069" id="u328ea1ea" class="ne-image"></p></details>

Git官网匹配规则:[Git - gitignore Documentation](https://git-scm.com/docs/gitignore)

<h5 id="uMZob">远程仓库</h5>
<details class="lake-collapse"><summary id="u77f25584"><span class="ne-text">不存在本地仓库</span></summary><p id="u809ffe96" class="ne-p"><span class="ne-text">echo&quot;# remote-repo&quot;&gt;&gt; README.md</span></p><p id="u20eb9812" class="ne-p"><span class="ne-text">git init</span></p><p id="uc6343321" class="ne-p"><span class="ne-text">git add README.md</span></p><p id="uaba48681" class="ne-p"><span class="ne-text">git commit -m&quot;first commit&quot;</span></p><p id="ueb47bd2e" class="ne-p"><span class="ne-text">git branch - main</span></p><p id="u98a0e619" class="ne-p"><span class="ne-text">git remote add origin git@github.com:geekhall-laoyang/remote-repo.git</span></p><p id="u4a691752" class="ne-p"><span class="ne-text">git push -u origin main</span></p></details>
<details class="lake-collapse"><summary id="ub1ce2e9e"><span class="ne-text">存在本地仓库</span></summary><p id="u50cfc4d2" class="ne-p"><span class="ne-text">git remote add origin git@github.com:geekhall-laoyang/remote-repo.git</span></p><p id="u52d33af1" class="ne-p"><span class="ne-text">git branch - main</span></p><p id="uf0b08533" class="ne-p"><span class="ne-text">git push -u origin main</span></p></details>
<details class="lake-collapse"><summary id="u2976878c"><span class="ne-text">配置SSH密钥</span></summary><div class="ne-quote"><p id="ubf0ca822" class="ne-p"><span class="ne-text">如果第一次使用ssh方式,需要配置SSH密钥,详见</span><span id="aYA92" class="ne-bookmark-inline"><a href="https://blog.csdn.net/lqlqlq007/article/details/78983879" target="_blank">git ssh key配置_git配置ssh key-CSDN博客</a></span></p></div><p id="u40053760" class="ne-p"><img src="https://cdn.nlark.com/yuque/0/2024/png/35307424/1732782348793-e29eae91-71c5-4d70-8eae-5435aa735915.png" width="688" id="uf156c63f" class="ne-image"></p></details>

:::tips
git remote -v      查看本地仓库关联远程仓库

git push -u origin main:main 将本地分支和远程分支关联并推送(如果本地和远程分支相同,则可省略:main)

git pull<远程仓库名><远程分支名>:<本地分支名>  如果省略的话默认就是拉取仓库别名为origin的主分支

:::

<h5 id="msHSx">分支</h5>

:::tips
git branch    查看分支

git branch <name>     创建新的分支

git checkout <name>   切换分支(git checkout 也有恢复文件的功能,如果分支名和文件名重复,可能冲突)

git switch <name>  切换分支

git merge dev   合并分支   (首先切换到要接受合并的分支,例如:main)

git branch -d dev 删除已被合并的分支  ( 未被合并不能被-d删除,需要-D强制删除分支  )

git merge --abort  终止合并

:::

<h5 id="XBLN7">合并冲突</h5>

如果两个分支修改了同一处代码,合并时会产生合并冲突,需要解决冲突

:::tips
当发生冲突可以使用git status 查看冲突文件列表,也可使用git diff 查看具体冲突内容

需要手动修改冲突文件,在重新提交

:::



<h5 id="MPBt4">git  rebase变基</h5>

![](./Git/1732784949965-9d77b1e1-d0e4-4a19-9a44-38aef9ea7520.png)

![](./Git/1732785147042-fd8304df-3a89-4293-bdfd-af7d272816a4.png)![](./Git/1732785156279-aa64bcd2-9e0e-4a5c-8ce2-be406e3f104a.png)

<h5 id="fvKQh">git cherry-pick</h5>

:::tips
`<font style="color:rgb(77, 77, 77);">git cherry-pick</font>`<font style="color:rgb(77, 77, 77);">命令的作用，就是将指定的提交（</font>[commit](https://so.csdn.net/so/search?q=commit)<font style="color:rgb(77, 77, 77);">）应用于其他分支。</font>

<font style="color:rgb(77, 77, 77);">git cherry-pick <commitHash></font>

:::

![](./Git/1732785882221-49592d40-dda3-4867-97dd-7a8564cacd06.png)

:::tips
 $ git cherry-pick <HashA> <HashB>   合并两次的提交

// 不包含A，包含B

$ git cherry-pick A..B 

// 如果想搞成[]区间，使用 git cherry-pick A^..B 相当于[A B]包含A

$ git cherry-pick A^..B 

:::

![](./Git/1732786053734-4ea518c3-27d9-4a60-b874-e3c8c5834298.png)

