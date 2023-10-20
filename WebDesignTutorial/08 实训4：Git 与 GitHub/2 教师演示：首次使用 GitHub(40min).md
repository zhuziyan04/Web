>[!tip]
> 本操作的前两项流程比较简单，为了给各位锻炼的机会，请参考我已给出的文档自行完成，后两项因为涉及到命令行，请根据实际情况由教师演示完成。


## 2.1 注册账号
首先，进入官网 [GitHub](https://github.com/)，由于浏览器有着很好的翻译功能，这里请各位自己探索注册流程。

>[!warning]
> 在注册的 step2，有一个 Unlimited public repositories for free 选项，这是免费用户，选他！

注册成功后，就会看到欢迎界面了，在欢迎界面提供了一些新手教程和新手任务，建议各位在课余闲暇的时候好好看一遍，对于你用活 GitHub 非常有意义。不过在今天的课程上先跳过这些信息。

如果你有兴趣的话，可以花一点时间去页面右上角用户头像上的下拉菜单中找到 `Your profile` 选项，并提供一些个人信息，方便大家认识你。

>[!tip]
> 关乎到各位期末平时分的绿点图也在 `Your profile` 这个界面里。

>[!tip]
> 学点常用单词
> 1. Sign in - 登录
> 2. Sign up - 注册
> 3. Unlimited - 无限的
> 4. Public - 公共的
> 5. Repositories - 仓库
> 6. Profile - 个人资料

---
## 2.2 新建远程仓库
请找到 `New` 或者 `Start a project` 开始一个新项目并建立该项目的远程仓库。随后会跳出一个标题为 Create a new repositroy 的页面。Repository name、Description 等信息请自行设置。这里仅给一些简单的提示：

1. Repository name 不宜过长，也不建议出现中文字符，英文起名的话容易出现需要空格分隔单词的情况，建议使用下划线替代，比如 repo_name，也可以用驼峰命名法，如 RepoName 做区别。
2. Description 尽可以放飞自我，写点项目的介绍，中英文不限。
3. 首次新建仓库设置 Public 方便大家互访。
4. .gitignore 和 license 都是非常必要的设置，但为了避免一次课程的新内容太多，暂时跳过。

>[!warning]
> `Initialize this repository with a README` 这是在为你的新仓库设置一个 README 说明文件，由于本节课会把各位之前做的网页上传到这个仓库，如果这个仓库已经有了文件，会引起不必要的冲突，所以请务必 ==不要勾选== 这个选项。

>[!tip]
> 学点常用单词
> 1. Create - 新建
> 2. Description - 描述
> 3. Initialize - 初始化
> 4. README - 读我（自我介绍）

---
## 2.3 为本地仓库添加远程链接并上传
>[!tip]
> 新建仓库成功后，如果仓库没中没用任何文件，打开仓库连接后，会显示一个名为 `Quick setup` 的引导页面，对首次接触命令行的我们来说十分有用，务必充分利用。

1. Quick setup 的标题部分，显示了项目的地址信息。请注意地址栏前面的 HTTPS / SSH 是两个可以互相切换的开关按钮。
	![[081.png]]
	其中，SSH 是一种安全有效，一劳永逸的登陆方式，但由于机房存在还原系统，我们即使设置了 SSH，也会被还原，另一种一仓库一设置的 SSH 方式又太繁琐。暂时忽略。

	因此，此处推荐 HTTPS 的方式设置远程链接。

>[!warning]
>  请务必选中 HTTPS 按钮。

2. 请跳过第二部分的命令介绍，直接看 or push a exisiting repo ... 这段提示

	![[082.png]]

	这是因为我们接下来是想把已经存在了一些内容的本地仓库上传至远程仓库，所以是 push a exisiting repo。
	
	由于 git 本地仓库默认的分支（branch）名称叫 master，本来 GitHub 也是和他保持一致的，但因为北美那边搞“政治正确”，认为 master 暗示了 slave 进而踩在了黑人兄弟的伤痛上，所以改成了 main，这就是第二行 git branch -M main 的意义，我们也可以暂时跳过.

	所以可以跳过第二行的设置，并把第三行改成
	```github
	git push -u origin master
	```

3. 先后复制第一行，和改动后的第三行，并依次在 WSL 中本地仓库文件夹下执行，即可建立本地和远程的链接。

---
## 2.4 设置 token 

执行到 2.3 的最后一步 `git push -u origin master` 后，你会发现 GitHub 提示需提供用户名密码才可以完成上传，但输入信息后又得到了出错指令，建议英语不错的同学先自己了解下 token 机制。

由于在我们课堂上通过用户名和密码在 GitHub 上进行 Git 操作比较方便，所以这里提供通过 Personal access tokens（个人访问令牌）来实现访问的方法：

1. 登录 GitHub 账户。
2. 点击头像，进入 Settings（设置）页面。
3. 点击左侧菜单栏中的 Developer settings（开发者设置），然后再点击右侧的 Personal access tokens（个人访问令牌）。
4. 点击 Generate new token（生成新令牌）。
5. 在 Note（注释）字段中输入一个说明 Personal access tokens 的名称，以及要访问的权限（比如 repo、admin:org 等）。
6. 点击 Generate token（生成令牌）。
7. 将生成的 Personal access tokens 复制到 Git 客户端中的密码字段，即可用 Personal access tokens 来进行 Git 操作。

>[!danger]
> Personal access tokens 只会在生成后显示一次，因此请务必将其复制并保存在安全的地方。如果忘记了 Personal access tokens，可以在 Personal access tokens 页面中撤销该令牌并重新生成一个。

---
## 2.5 利用 git clone 下载远程仓库
>[!tip]
> GitHub 上所有 Public 仓库都可以使用 git clone 命令，建议你问同组人要个仓库链接试试。

### 2.5.1 基本命令
`git clone` 是用于将 Git 仓库复制到本地的命令，以下是 `git clone` 的基本操作方法：

1. 进入你的个人文件夹。
2. 输入 `git clone` 命令，后跟远程 Git 仓库的 URL。例如，
	```
	git clone https://github.com/<username>/<repository>.git
	```
	其中 `<username>` 是你的 GitHub 用户名，`<repository>` 是你要克隆的仓库名称。
3. 输入用户名和 token，Git 将从远程仓库克隆一个副本到本地。

### 2.5.2 机房网速较慢时的应对
如果你只想获取最新版本的代码，可以使用 `--depth` 参数来限制克隆的深度，例如：

```bash
git clone --depth=1 [仓库地址]
```

这样只会克隆最近一次提交的代码。这个参数可以有效地减少下载的历史版本信息的数量。

---

## 2.6 git push 与 git pull

无论是自己的仓库，还是 clone 别人的，只要远程仓库的设置完成，本地与远程仓库建立第一次链接后，就可以非常方便的利用这两个命令同步本地和远程仓库了。

1. git pull：从远程仓库获取最新版本的代码并合并到本地仓库。
2. git push：将本地仓库的代码推送到远程仓库中。

使用这两条命令时需要注意的是：

1. 在使用 git push 命令前，需要先进行 git add 和 git commit 操作，以便将代码变更保存到本地仓库中。
2. 只要在一台电脑前 git push 过代码，那另一台电脑在编辑改动代码前，务必保证先 git pull 获取最新版本，否则下次 git push 的时候会遇到版本不同步的问题。

>[!warning]
> 本节课程的内容比较多，各位无法深刻体会到上述两条的重要性，请放心，如不注意，同步问题很快就会出现在你的仓库，失败有时候是最好的老师。