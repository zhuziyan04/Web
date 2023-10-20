完成本课程的所有要求以后，请勿忘组织并 commit 一个新的版本，为了不影响各位的绿点生成，我要做一些简单的补充：

## 3.1 最后一次对 init 位置的提示

见教师演示。

___

## 3.2 正确设置提交信息

为方便各位学习 git，避免在学习之初就因为要输入较长的指令而产生挫败感，我在之前的课程中简化了一个重要的内容，今天要把这一环给补上。

如果各位回家后已经尝试过 Git 的使用，并试图利用 git commit 提交版本的话，应该会遇到以下的出错提示：

>[!question]
> 请告诉我它在说什么？


```
*** Please tell me who you are.
Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: empty ident name (for <alex@AlexOfficePC.>) not allowed

            Git exited with code 128. Did you forget to run:

              git config --global user.email "you@example.com"
              git config --global user.name "Your Name"

git exited with error code 128
```

>[!warning] 
> 之前已经说过，Liunx 的设计理念里面有一条，no news is good news，如果敲入命令后出现大段提示，往往都不会是好消息，这个时候就要好好得去读一读提示里到底说了什么内容。千万不要看到是英语就直接跳过。

它在要求你提供提交代码者得 email 和 name 这两个信息。其中 email 部分请保证和你将来要申请得 github 账号保持一致，==否则会影响绿点的统计==。name 信息可以随意一些，我建议和 github 昵称保持一致，方便核对个人信息。

>[!warning]
> 我在机房的电脑设置过这两条信息，所以提交时不会有出错提示，但 email 不一致会导致绿点无法计入你的账号，影响平时分结分，所以务必要设置正确。可以通过 git log 查看 Author 查看提交信息是否正确。

>[!error]
> 机房有还原系统，这代表你每次在机房提交代码时，都应该重新设置这两条信息。

>[!tip]
> 建议专业学生攒一台自己的主力工作电脑，台式机更佳，出门在外可以通过联网远程登陆的方式连接家中或宿舍里的这台主力电脑，就不需要在机房或其他陌生的环境里频繁改设置了。