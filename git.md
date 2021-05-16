**目标**

- 了解版本控制软件的作用
- 了解版本控制系统的分类
- Git的特性
- 初始化 Git 仓库的命令
- 查看文件状态的命令
- 一次性将文件加入暂存区的命令
- 将暂存区的文件提交到 Git 仓库的命令
- 能够使用 `Github` 创建和维护远程仓库
- 能够掌握 `Git` 分支的基本使用
<a name="ck1CG"></a>
## 版本控制软件

- **版本控制软件**是一个用来记录文件变化，以便将来查阅特定

版本修订情况的系统，因此有时也叫做“**版本控制系统**”
<a name="8JOm9"></a>
## 使用版本控制软件的好处

- **操作简便：只需识记几组简单的终端命令**，即可快速上手常见的版本控制软件
- **易于对比：**基于版本控制软件提供的功能，能够方便地比较文件的变化细节，从而查找出导致问题的原因
- **易于回溯：**可以将选定的文件回溯到之前的状态，甚至将整个项目都回退到过去某个时间点的状态
- **不易丢失：**在版本控制软件中，被用户误删除的文件，可以轻松的恢复回来
- **协作方便：**基于版本控制软件提供的分支功能，可以轻松实现多人协作开发时的代码合并操作
<a name="aHjer"></a>
## 版本控制系统的分类
<a name="81570649"></a>
### 本地版本控制系统
**单机运行**，使维护文件版本的操作工具化<br />特点：使用软件来记录文件的不同版本，提高了工作效率，降低了手动维护版本的出错率<br />缺点：<br />① 单机运行，不支持多人协作开发<br />② 版本数据库故障后，所有历史更新记录会丢失
<a name="795e5ad0"></a>
### 集中化的版本控制系统
联网运行，支持多人协作开发；**性能差、用户体验不好**<br />**典型代表 `SVN`**<br />特点：<br />基于服务器、客户端的运行模式<br />① 服务器保存文件的所有更新记录<br />② 客户端只保留最新的文件版本<br />**优点：**联网运行，支持多人协作开发<br />缺点：<br />① 不支持离线提交版本更新<br />② 中心服务器崩溃后，所有人无法正常工作<br />③ 版本数据库故障后，所有历史更新记录会丢失
<a name="ca948407"></a>
### 分布式版本控制系统
**联网运行，支持多人协作开发；性能优秀、用户体验好**<br />**典型代表：`Git`**<br />特点：<br />基于服务器、客户端的运行模式<br />① 服务器保存文件的所有更新版本<br />② 客户端是服务器的完整备份，并不是只保留文件的最新版本<br />优点：<br />① 联网运行，支持多人协作开发<br />② 客户端断网后支持离线本地提交版本更新<br />③ 服务器故障或损坏后，可使用任何一个客户端的备份进行恢复
<a name="Saosz"></a>
## Git基础概念
<a name="ERW2z"></a>
### 什么是 Git
`Git` 是一个**开源的分布式版本控制系统**
<a name="1oK1L"></a>
### **Git 的特性**
① 直接记录快照，而非差异比较<br />② 近乎所有操作都是本地执行
<a name="Xchcz"></a>
#### `SVN` 的差异比较
传统的版本控制系统（例如 `SVN`）是**基于差异**的版本控制，它们存储的是**一组基本文件**和**每个文件随时间逐步累积的差异**<br />**好处：**节省磁盘空间<br />**缺点：**耗时、效率低<br /> 在每次切换版本的时候，都需要在基本文件的基础上，应用每个差异，从而生成目标版本对应的文件
<a name="AE0rN"></a>
#### git的记录快照
**Git 快照**是在原有文件版本的基础上重新生成一份新的文件，**类似于备份**。为了效率，如果文件没有修改，Git<br />不再重新存储该文件，而是只保留一个链接指向之前存储的文件。<br />**缺点：**占用磁盘空间较大<br />**优点：** **版本切换时非常快**，因为每个版本都是完整的文件快照，切换版本时直接恢复目标版本的快照即可。<br />**特点： ** **空间换时间**
<a name="bcb4c73d"></a>
#### **近乎所有操作都是本地执行**
在 Git 中的绝大多数操作都**只需要访问本地文件和资源**，一般不需要来自网络上其它计算机的信息<br />**特性：**<br />① 断网后依旧可以在本地对项目进行版本管理<br />② 联网后，把本地修改的记录同步到云端服务器即可
<a name="99d8cbd7"></a>
### **`git` 中的三个区域**
使用 `Git` 管理的项目，拥有三个区域，分别是**工作区**、**暂存区**、**`Git` 仓库**
<a name="9b84c689"></a>
###  git中的三种状态

- **已修改 `modified`**
   - 表示修改了文件，但还没将修改的结果放到**暂存区**
- **已暂存 `staged`**
   - 表示对已修改文件的当前版本做了标记，使之包含在**下次提交的列表中**
- **已提交 `committed`**
   - 表示文件已经安全地保存在本地的 **Git 仓库中**

**注意：**

- 工作区的文件被修改了，但还没有放到暂存区，就是**已修改**状态。
- 如果文件已修改并放入暂存区，就属于**已暂存**状态。
- 如果 Git 仓库中**保存着特定版本**的文件，就属于**已提交**状态。

查看所有的全局配置项<br />git config --list --global<br />

<a name="iiJD2"></a>
### 获取 `Git` 仓库的两种方式
① 将尚未进行版本控制的本地目录**转换**为 `Git` 仓库<br />② 从其它服务器**克隆**一个已存在的 `Git` 仓库<br />以上两种方式都能够在自己的电脑上得到一个可用的 Git 仓库
<a name="qDrvC"></a>
### 在现有目录中初始化仓库
如果自己有一个尚未进行版本控制的项目目录，想要用 `Git` 来控制它，需要执行如下两个步骤：<br />① 在项目目录中，通过鼠标右键打开“`Git Bash`”<br />② 执行 `git init` 命令将当前的目录转化为 `Git` 仓库<br />`git init` 命令会创建一个名为 .git 的隐藏目录，**这个 .git 目录就是当前项目的 Git 仓库**，里面包含了**初始的必要文件**，这些文件是 Git 仓库的**必要组成部分**<br />**Git 操作的终极结果：让工作区中的文件都处于**“未修改”**的状态。
<a name="ihKsZ"></a>
### 检查文件的状态 git status
<a name="xDyNA"></a>
### 以精简的方式显示文件状态 git status -s
新添加到暂存区中的文件前面有绿色的A标记
<a name="4zXIt"></a>
### 跟踪新文件git add  XXX   /   git add .
<a name="uZidI"></a>
### 提交更新 git commit -m "新建了index.html 文件"
未跟踪文件前面有红色的 **??** 标记<br />修改过的、没有放入暂存区的文件前面有红色的 **M** 标记。<br />已修改，已存放暂存区的文件前面有绿色的 **M **标记。
<a name="Tl6nU"></a>
### 撤销对文件的修改 git checkout --XXXX文件
**撤销对文件的修改指的是：**把对工作区中对应文件的修改，**还原**成 Git 仓库中所保存的版本。<br />**操作的结果：**所有的修改会丢失，且无法恢复！**危险性比较高，请慎重操作！**<br />**撤销操作的本质：**用 Git 仓库中保存的文件，覆盖工作区中指定的文件。
<a name="c2439caf"></a>
### 取消暂存的文件  git reset HEAD XXX文件
<a name="EIXLz"></a>
### 跳过使用暂存区域，直接从工作区提交至仓库 git commit -a -m "日志信息"
无法监听未被git到的文件
<a name="pBLH6"></a>
### 移除文件  git rm -f index.js  / git rm --cached index.css
从 Git 仓库中移除文件的方式有两种：<br />① 从 Git 仓库和工作区中**同时移除**对应的文件<br />② 只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件<br /># 从 Git仓库和工作区中同时移除 index.js 文件<br />git rm -f index.js<br /># 只从 Git 仓库中移除 index.css，但保留工作区中的 index.css 文件<br />git rm --cached index.css
<a name="JgTkb"></a>
### 忽略文件
一般我们总会有些文件无需纳入 `Git` 的管理，也不希望它们总出现在未跟踪文件列表。 在这种情况下，我们可以创建一个名为 `.gitignore` 的配置文件，列出要忽略的文件的匹配模式。<br />文件 `.gitignore` 的格式规范如下：<br />① 以 **# 开头**的是注释<br />② 以 **/ 结尾**的是目录<br />③ 以 **/ 开头**防止递归<br />④ 以 **! 开头**表示取反<br />⑤ 可以使用 **glob 模式**进行文件和文件夹的匹配（glob 指简化了的正则表达式）

- **星号 *** 匹配**零个或多个任意字符**
- **`[abc]`** 匹配**任何一个列在方括号中的字符** （此案例匹配一个 a 或匹配一个 b 或匹配一个 c）
- **问号 ?** 只匹配**一个任意字符**
- **两个星号 **** 表示匹配**任意中间目录**（比如 a/**/z 可以匹配 a/z 、 a/b/z 或 a/b/c/z 等）
- 在方括号中使用**短划线**分隔两个字符， 表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）
<a name="UJKZE"></a>
### `.gitignore` **文件的例子**
**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1613823397626-2980d357-5e7b-42b3-bf93-5951a7aa934a.png#align=left&display=inline&height=525&margin=%5Bobject%20Object%5D&name=image.png&originHeight=525&originWidth=671&size=90609&status=done&style=none&width=671)**
<a name="DEH8x"></a>
### 查看提交历史  git log
# 按时间先后顺序列出所有的提交历史，最近的提交在最上面<br />git log<br /># 只展示最新的两条提交历史，数字可以按需进行填写<br />git log -2<br /># 在一行上展示最近两条提交历史的信息<br />git log -2 --pretty=oneline<br />
<a name="oL3xL"></a>
### 回退到指定的版本
# 在一行上展示所有的提交历史<br />git log --pretty=oneline<br /># 使用 git reset --hard 命令，根据指定的提交 ID 回退到指定版本<br />git reset --hard <CommitID>  id是git  log 里面显示的<br /># 在旧版本中使用 git reflog --pretty=oneline 命令，查看命令操作的历史<br />git reflog --pretty=onelone<br /># 再次根据最新的提交 ID，跳转到最新的版本<br />git reset --hard <CommitID>
<a name="3a2be50c"></a>
## 什么是开源许可协议
开源并不意味着完全没有限制，为了**限制使用者的使用范围**和**保护作者的权利**，每个开源项目都应该遵守开源<br />许可协议（ `Open Source License` ）。
<a name="d9d9ed06"></a>
### 常见的 5 种开源许可协议

- `BSD`（Berkeley Software Distribution）
- `Apache Licence 2.0`
- **`GPL`**（GNU General Public License） (⭐⭐⭐)
   - 具有传染性的一种开源协议，不允许修改后和衍生的代码做为闭源的商业软件发布和销售
   - 使用 `GPL` 的最著名的软件项目是：Linux
- `LGPL`（GNU Lesser General Public License）
- **`MIT`**（Massachusetts Institute of Technology, MIT） (⭐⭐⭐)
   - 是目前限制最少的协议，唯一的条件：在修改后的代码或者发行包中，必须包含原作者的许可信息
   - 使用 MIT 的软件项目有：`jquery`、`Node.js `;
<a name="Kti2v"></a>
## 开源项目托管平台
专门用于免费存放开源项目源代码的网站，叫做**开源项目托管平台**。目前世界上比较出名的开源项目托管平台<br />主要有以下 3 个：

- `Github`（全球最牛的开源项目托管平台，没有之一）
- `Gitlab`（对代码私有性支持较好，因此企业用户较多）
- `Gitee`（又叫做码云，是国产的开源项目托管平台。访问速度快、纯中文界面、使用友好）

**注意：**以上 3 个开源项目托管平台，只能托管以 `Git` 管理的项目源代码，因此，它们的名字都以 `Git` 开头
<a name="npqpX"></a>
## 远程仓库的两种访问方式
`Github` 上的远程仓库，有两种访问方式，分别是 `HTTPS` 和 `SSH`。它们的区别是：<br />① `HTTPS`：**零配置**；但是每次访问仓库时，需要重复输入 `Github` 的账号和密码才能访问成功<br />② `SSH`：**需要进行额外的配置**；但是配置成功后，每次访问仓库时，不需重复输入 `Github` 的账号和密码<br />**注意：**在实际开发中，**推荐使用 SSH 的方式访问远程仓库。**
<a name="YyZdN"></a>
### 基于 SSH key(⭐⭐⭐)
`SSH key` 的**作用**：实现本地仓库和 `Github` 之间免登录的加密数据传输。<br />`SSH key` 的**好处**：免登录身份认证、数据加密传输。<br />`SSH key` 由**两部分组成**，分别是：<br />① `id_rsa`（私钥文件，存放于客户端的电脑中即可）<br />② `id_rsa.pub`（公钥文件，需要配置到 `Github` 中）
<a name="vNT5c"></a>
#### 生成 SSH key
① 打开 Git Bash<br />② 粘贴如下的命令，并将 `your_email@example.com` 替换为注册 `Github` 账号时填写的邮箱：

- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

③ 连续敲击 3 次回车，即可在 `C:\Users\用户名文件夹\.ssh` 目录中生成 `id_rsa` 和 `id_rsa.pub` 两个文件
<a name="JN7nm"></a>
#### 配置 SSH key
① 使用记事本打开 `id_rsa.pub` 文件，复制里面的文本内容<br />② 在浏览器中登录 `Github`，点击头像 -> `Settings -> SSH and GPG Keys -> New SSH key`<br />③ 将 `id_rsa.pub` 文件中的内容，粘贴到 `Key` 对应的文本框中<br />④ 在 `Title` 文本框中任意填写一个名称，来标识这个 `Key` 从何而来
<a name="rM8Vl"></a>
#### 检测 `Github` 的 `SSH key` 是否配置成功

- 打开 `Git Bash`，输入如下的命令并回车执行：

ssh -T git@gitee.com

- 上述的命令执行成功后，可能会看到如下的提示消息：<br />![](https://cdn.nlark.com/yuque/0/2021/png/12526667/1613878861020-bcbc3cf3-cee5-4fa2-a8b2-904af6aabee2.png#align=left&display=inline&height=106&margin=%5Bobject%20Object%5D&originHeight=106&originWidth=637&size=0&status=done&style=none&width=637)<br />
- 输入 `yes` 之后，如果能看到类似于下面的提示消息，证明 `SSH key` 已经配置成功了：<br />![](https://cdn.nlark.com/yuque/0/2021/png/12526667/1613878861016-cb3289e4-d1f1-48c1-b68d-2ca82ae78f66.png#align=left&display=inline&height=76&margin=%5Bobject%20Object%5D&originHeight=76&originWidth=630&size=0&status=done&style=none&width=630)
<a name="bcacd32d"></a>
#### 将远程仓库克隆到本地
打开 `Git Bash`，输入如下的命令并回车执行：<br />git clone 远程仓库的地址
<a name="QVhxP"></a>
## GIT 分支
<a name="bEeI4"></a>
### master 主分支
在初始化本地 `Git` 仓库的时候，`Git` 默认已经帮我们创建了一个名字叫做 `master` 的分支。通常我们把这个<br />`master` 分支叫做主分支。<br />**用来保存和记录整个项目已完成的功能代码**。<br />因此，**不允许程序员直接在 `master` 分支上修改代码**，因为这样做的风险太高，容易导致整个项目崩溃。
<a name="S0Cyp"></a>
### 功能分支
**功能分支**指的是专门用来开发新功能的分支，它是临时从 `master` 主分支上分叉出来的，当新功能开发且测试<br />完毕后，最终需要合并到 `master` 主分支上
<a name="piQGg"></a>
### 查看当前 Git 仓库中所有的分支列表  git branch
<a name="x19nU"></a>
### 创建新分支  git branch 分支名称
<a name="BlP1e"></a>
### 切换分支  git checkout login
<a name="rBON1"></a>
### 分支的快速创建和切换  git checkout -b 分支名称
是下面两条命令的简写形式：<br />① `git branch` 分支名称<br />② `git checkout` 分支名称
<a name="qMDKI"></a>
### 合并分支
# 1. 切换到 master 分支<br />git checkout master<br /># 2. 在master 分支上运行 git merge 命令，将 login 分支的代码合到 master 分支<br />git merge login
<a name="LERaa"></a>
### 删除分支 git branch -d 分支名称
<a name="DyDO1"></a>
### 遇到冲突时的分支合并
如果**在两个不同的分支中**，对**同一个文件**进行了**不同的修改(commit)**，Git 就没法干净的合并它们。 此时，我们需要打开<br />这些包含冲突的文件然后**手动解决冲突**
<a name="twzYq"></a>
### 远程分支操作
<a name="5HPgo"></a>
#### 将本地分支推送到远程仓库(⭐⭐⭐)
如果是**第一次**将本地分支推送到远程仓库，需要运行如下的命令：<br /># -u 表示把本地分支和远程分支进行关联，只在第一次推送的时候需要带 -u 参数<br />git push -u 远程仓库的别名 本地分支名称:远程分支名称<br /># 实际案例<br />git push -u origin payment:pay<br /># 如果希望远程分支的名称和本地分支名称保持一致，可以对命令进行简化<br />git push -u origin payment<br />**注意：**第一次推送分支需要带 **-u 参数**，此后可以直接使用 `git push` 推送代码到远程分支
<a name="iQxw4"></a>
### 查看远程仓库中所有的分支列表  git remote show 远程仓库名称
 git remote show origin
<a name="Fo3l9"></a>
### 跟踪分支
跟踪分支指的是：从远程仓库中，把远程分支下载到本地仓库中。需要运行的命令如下：

创建git的办法<br />第一步，登录官网，个人中心，创建一个新的项目<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616571002653-84548014-ab4e-4d33-8336-8608c97a7860.png#align=left&display=inline&height=89&margin=%5Bobject%20Object%5D&name=image.png&originHeight=89&originWidth=507&size=7419&status=done&style=none&width=507)<br />第二步:打开自己的文件，从主分支切换到开发分支，git checkout -b login进行开发，<br />第三步:开发完成后，检查文件的状态 git status,输入git add . <br />第三步:提交更新 git commit -m "新建了index.html 文件"   显示working tree clean<br />第四步，git branch 查看分支，切换回主分支 git checkout main<br />第五步:合并副分支内容到主分支git merge login<br />第六步：切换到主分支<br />$ git remote add origin 远程仓库地址<br />第七步： git push -u origin master<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />1.新建码云项目仓库<br />
<br />填写仓库名称 将 使用Readme文件初始化这个仓库 选项的勾取消<br />3.在项目文件夹内 按住Shift+鼠标右键打开Windows PowShell<br />1.输入git init 初始化仓库<br />2.输入 git status 检查是否有代码未提交<br />3.输入git add . 提交所有代码 （add后有一个空格）<br />
<br />4.git全局设置<br />输入git config --global user.name “代码过敏症”<br />git config --global user.email “1746294426@qq.com”<br />
<br />5.将本地仓库与线上仓库绑定<br />在Windows PowShell输入<br />在这里插入图片描述<br />
<br />6.检查本地当前所在分支<br />git branch<br />
<br />7.新建本地分支<br />git checkout -b user (-b user 新建名为user的分支)<br />
<br />8.检查当前分支文件状态<br />git status<br />
<br />9.添加到缓存区<br />git add .<br />
<br />10.再次检查状态<br />git status<br />
<br />11.提交到本地仓库中<br />git commit -m “输入提交文字”<br />
<br />再次检查状态<br />git status<br />显示 working tree clear<br />
<br />13.显示所在分支<br />git branch<br />
<br />14.将本地分支推送到云端 并以（分支名）保存<br />git push -u origin （分支名）<br />
<br />如果显示错误 没有提交 可以试试 git push origin master<br />
<br />15.切换分支<br />git checkout (分支名)<br />
<br />16.将分支合并到主分支<br />先切换到master 然后合并分支<br />
<br />git merge (分支名)<br />
<br />17.将本地代码推送到云端<br />git push<br />
<br />18.Git连接(远程仓库)码云地址<br />git remote add origin 你的码云地址<br />
<br />19.拉取码云上的所有文件到项目中来<br />git pull origin master<br />
<br />20.或者直接执行克隆项目文件<br />git clone 你的码云地址<br />
<br />
<br />这时候会报错：<br />There is no tracking information for the current branch.<br />
<br />因为新创建的分支push到远程仓库后没有与本地分支关联，下面语句可以令远程分支与本地分支关联起来<br />
<br />git branch --set-upstream-to=origin/release_3.1.3 release_3.1.3<br />上面的origin/release_3.1.3是已经推送到远程的分支<br />
<br />末尾的release_3.1.3是本地分支<br />
<br />执行这段代码即可<br />git branch --set-upstream-to=origin/master dev<br />
<br />master是远程分支，dev是本地分支
