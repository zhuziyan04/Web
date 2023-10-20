## 2.1 查看文档的变化

如果你在某次 `git commit` 向仓库提交了新版本之后，不对目录中的内容进行任何改动，而是立刻再次键入 `git commit` 命令，就会得到系统提示: 

```bash
nothing to commit, working tree clean
```

显然，由于没有改动过任何内容，系统提示：“没啥好提交的，有一个记录了目录中所有文件变化的 working tree 是 clean 的”。那我们有没有办法看看这个 working tree 的内容呢？答案是显而易见的。

>[!info]
> 利用 git status 命令，可以查看记录了当前仓库自上一次 commit 之后的文档的增、删、改等信息的 working tree。

倘若还是没有进行过任何修改，系统提示和没有任何改动时的 `git commit` 一致：

```bash
nothing to commit, working tree clean
```

但如果有过改动，请各位看一个实例：
```
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    a.txt
        modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        newText.txt
```

>[!warning]
> 不要被满屏的英语吓到，请放下抵触心理，跟着教师一起猜猜看这些记录分别代表了哪种改动。

___
## 2.2 快速确认更新
接着上一节的例子继续，文档发生了 3 处更改，如果我们想确认这 3 处更改，并在下一次 `git commit` 时把这 3 处更改作为同一个版本提交，根据我们之前的学习，应该键入以下命令：

```bash
get add a.txt
get add index.html
get add newText.txt
```

这些改动还不算多，如果在实际的开发流程中的话，每次版本更新可能涉及到十几或几十处修改，显然连敲十几遍 `git add` 是不合理的，Git 的开发者也考虑到了这种情况。

>[!info]
> 可以使用 `git add .` 命令，一次性确认所有的修改。键入命令后，如果操作成功系统不会给任何提示，因为 no news is good news 是 linux 的设计理念之一。

此时用上我们在 2.1 中新学的 `git status` 命令就会看到如下提示：

```bash
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   index.html
        renamed:    a.txt -> newText.txt
```

>[!tip]
> 有意思的是，Git 还“自作聪明”了一回，各位发现了吗？

___
## 2.3 实现版本的自由切换

正在写的这份课程文档日志较为丰富，正好可以作为示例来演示在各个版本间的自由切换的方法。请各位按步骤进行操作。

### 2.3.0 确认工作目录

准备工作不能忽视，首先就是要切换工作目录到目前的这篇课程文档目录：

```bash
cd /mnt/f/00BuQiang/Obsidian/WebDesignTutorial
```

>[!warning]
> 各人保存这份文档的实际地址各不相同，上面的命令只是演示，请按实际情况操作。

### 2.3.1 查看版本日志
确认了工作目录无误之后，就能用上一节课学到的 `git log` 命令查看本仓库提交过的历史版本了。

>[!tip]
> 由于提交的内容较多，一屏幕显示不完全，系统会暂停在满屏的位置，此时可以按 `Space` 键或 `Enter` 键进行翻页，请各位观察一下这两种方式的不同。看到 (END) 字样则代表已经翻到日志的最后，此时可以按 `Q` 键返回。

下面，我截取两端日志做简单说明：
```
commit 6fbe89402a33cb47a69b1957841cbe0f7159ddbc (HEAD -> main, origin/main)
Author: Bu Qiang@SSTS <yoyobq@hotmail.com>
Date:   Tue Feb 21 20:24:56 2023 +0800

    docs: 修改 04 的课程设计，由理论为主改为实操为主，继续优化已完成部分的课程结构

commit 923905b34e6b166fcd7ad09bf1de6d25ce8bad1a
Author: Bu Qiang@SSTS <yoyobq@hotmail.com>
Date:   Tue Feb 21 01:11:10 2023 +0800

    docs: 基本完成 04 章节的编辑
```

1. 首行的 commit 字样之后一长串的数字与字母的组合，就是系统分配给各个版本的 id，这是识别不同版本的非常重要的信息。
2. 次行的 Author 代表了此次版本提交的作者信息，这个信息需要单独设置，我为了上课方便期间已经帮大家设置好了，之后的课程还会提及具体的设置方法。
3. Date 部分显然是提交这个版本的日期和具体时间，这个设置和上一行的作者信息将来会影响到绿点的生成。
4. 最后缩进的的一行就是 commit 时提供的简短版本说明文字。

拿到了各个版本的 id 信息，接下来就是版本间的切换了。

### 2.3.2 切换各个版本
>[!info]
> 利用 `git reset --hard [对应的版本id]` 命令实现版本间的切换。

例如此时可以输入下面这行命令进行切换。

```bash
git reset --hard ab3c6
```

成功后系统提示：

```bash
HEAD is now at ab3c61c docs: 项目确立文件结构，并试写课程概述章节
```

>[!warning]
> 我在这里造了一个小陷阱，如果没有预先读过这段警告直接敲上面的命令的话，一定发现课程文档读着读着就没有了，变成了上周的初级版本。大概率是要通过重新解压缩我课上分发压缩包才又看到了这些文字。

>[!question] 
> 如果你敲了命令后看到成功提示，却发现本篇文档没有受到影响，又是怎么回事？


>[!tip]
> 另一个值得一提的细节是 `git reset --hard` 后并不是完整的 id 号，而是 id 号的前几位。具体位数并不固定，只要足够保证 id 的唯一性，Git 允许省略后面的部分。

当然，还有一个更直接的恢复方式，通过查阅 log 记录，键入最新版本的 id 进行复原操作，失去的文档会自动跳出来。

```bash
git reset --hard 0e02e
```

___
## 2.4 显示更简洁全面的版本日志

2.3 中的最后一步实际上存在重大隐患，请按顺序输入下面的三条命令。
```bash
clear
git reset --hard ab3c6
git log
```

不难发现，版本日志只剩下了两个记录：

```
commit ab3c61c817584a593ddff2a018fdbbb51863d45f
Author: Bu Qiang@SSTS <yoyobq@hotmail.com>
Date:   Sat Feb 11 00:40:35 2023 +0800

    docs: 项目确立文件结构，并试写课程概述章节

commit 9ec947a165948d52687b2120da3ac23fea77693d
Author: Bu Qiang@SSTS <yoyobq@hotmail.com>
Date:   Sat Feb 11 00:38:38 2023 +0800

    build: 更新 .gitignore 文件
```

>[!info]
> 如果最新版本的 id 无从查起，就谈不上恢复了，这个时候，需要 `git reflog` 命令出场了。这是 Git 操作的一道安全保障，它能够记录几乎所有本地仓库的改变，包括所有分支的 commit 提交，以及已经被删除的 commit。

键入命令后系统提示：
```
6fbe894 (HEAD -> main, origin/main) HEAD@{0}: reset: moving to 6fbe89
ab3c61c HEAD@{1}: reset: moving to ab3c6
6fbe894 (HEAD -> main, origin/main) HEAD@{2}: commit: docs: 修改 04 的课程设计，由理论为主改为实操为主，继续优化已完成部分的课程结构
923905b HEAD@{3}: commit: docs: 基本完成 04 章节的编辑
8605fd5 HEAD@{4}: commit: fix: 删除误增的 node_modules 文件夹
0748f84 HEAD@{5}: commit: docs: 完成 02 03 文档的编辑，并继续更新文档结构
3b7556e HEAD@{6}: commit: fix: 修正重复提交造成的文件重复
45b616f HEAD@{7}: commit: docs: 调整 01，02章节的设计，完成 01 章节编辑
20d1d5a HEAD@{8}: Branch: renamed refs/heads/master to refs/heads/main
20d1d5a HEAD@{10}: commit (amend): docs: 完成 01 认识软件与工具的编辑，微调部分章节次序
bec5df1 HEAD@{11}: commit (amend): docs: 完成 00 认识软件与工具的编辑，微调部分章节次序
0ae18f3 HEAD@{12}: commit: docs: 完成 00 认识软件与工具的编辑，微调部分章节次序
e6850eb (master) HEAD@{13}: commit: docs: 完成 00 课程概述的编辑
ab3c61c HEAD@{14}: commit: docs: 项目确立文件结构，并试写课程概述章节
9ec947a HEAD@{15}: commit (initial): build: 更新 .gitignore 文件
```

不难发现哪怕是被删除的 log 也统统列出了 id 各位就不用担心无法通过 id 恢复文档了。

>[!danger]
> 一个血泪教训是，如果你正在编辑文档，千万不要在修改了文档后，尚未 commit 版本前用 `git reset` 进行版本的切换，否则所有新修却未 commit 的内容都会消失。