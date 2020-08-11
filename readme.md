0.git概念
 - Git是目前世界上最先进的分布式版本控制系统（没有之一）。
 - 2008年GitHub网站上线了，它为开源项目免费提供Git存储，
   无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。

- 注意：如果忘记写 -m 会进入vim编辑器界面，此时按下esc :   q   回车
- 强制退出： 【 esc  :   q! 】
-  保存再退出：  【 esc : wq 】
- Already up-to-date：本地代码版本库与服务器一致

1.git安装：
  -官网：https://git-scm.com/downloads
  -其他网址：https://blog.csdn.net/weixin_44198965/article/details/99686507

  - 界面：安装完成后点击开始菜单--git--git-bash，即可打开命令面板，其中：
    + Git gui here     git图形化操作界面
    + Git bash here     命令操作界面


2.用户信息配置 安装完成后，还需要最后一步设置，在命令行输入：
  - 用户名和邮箱
  - 每一次备份都会把当前备份者的信息存储起来
  - git config --global user.name "rfrao"
  - git config --global user.email "xx@qq.com"
  - --后面带的是参数，参数后面一般会跟值


3.初始化git仓库
  - 该仓库存放 项目代码的备份文件
  - .git是隐藏目录，备份文件所在目录
  - 项目右键打开 git bash
  - 命令 git init


4.把代码存储到git仓库中（把大象放到冰箱要几步）
  - step1: 把代码放到仓库门口 
    + git add ./readme.md 
    + git add ./    当前目录所有修改的文件，添加到仓库门口 
  - step2: 把代码放到仓库的某个房间(版本库)
    + git commit -m "完成第一个功能备份" 
  
  - 一次性把修改代码放到房间里（版本库）
    + git commit --all -m "这是一次性的操作" 

   
5.查看当前代码状态（有没有被放到门口，仓库中）
  - git status


6.查看日志
   - git log 查看历史提交的日志
   - git log --oneline 查看简洁版日志


7.回退到指定的版本
   - 回退到上一次代码提交时的状态
     +  git reset --hard Head~0
   - 回退到上上次代码提交时的状态
     +  git reset --hard Head~1
   - 通过版本号精确回退到某一次提交时的状态
     +  git reset --hard [版本号]
     + 这里的[版本号]是指每次随机生成的唯一的版本号。

   - 查看每一次切换版本的记录
     +  git reflog  
  

8.分支
   - 默认有一个主干分支 master

   - 创建分支
     + git branch dev   
     + 创建一个dev分支，dev分支的内容和master分支的内容一样
  
   - 切换分支
    + git checkout dev 
    + 切换到指定分支

   - 查看分支
    + git branch
 
   - 合并分支
     + git merge dev
     + 合并分支里的内容，将当前分支与指定分支(dev)进行合并
     + 当前分支指的是` git branch `命令输出的前面有*号的分支。

   - 删除分支
     + git branch -d dev

   - 分支冲突
     + 当分支内容修改冲突时，需要手动处理，还需要再提交一次处理结果。
     + HEAD永远指向最新的一次代码修改！
     + $ git add ./
     + $ git commit -m "处理冲突后的提交"

    

10.GitHub
   - .git中文件不要轻易修改，它已经将备份文件代码，转为二进制文件。不用看它。
  最终结果：每次提交的版本都存放到本地了。
   - 想要提交代码到网上/服务器  github
   - github 不是git，只是一个网站
   - github该网站服务器 提供了允许别人通过git上传代码的功能。
   - https://github.com/huoqishi
   - github是开源网站，可分享/提交源代码

11.提交代码到github（当作git服务器来使用）
   - git push [地址] [分支名]
   - 地址示例：
    $ git push https://github.com/rfrao/testgit0809.git master
   - 会把当前分支的内容上传到远程的master分支上。
   - 提交到对应的分支上（master）

  
12.从github下载代码到本地
   - git pull [地址] [分支名]
   - $ git pull  https://github.com/rfrao/testgit0809.git master
   - 退出： Q
   - 注意：本地要初始化一个仓库，git init

   - 克隆，会得到远程仓库相同的数据，若多次执行，会覆盖本地内容。
   git clone [地址]
   - git clone https://github.com/rfrao/testgit0809.git



13 SSH提交代码到gihub
   - 这种方式不需要每次都输入用户名和密码，就能够验证上传者的身份
   - 允许指定人员上传

   - 公钥 私钥
   - 二者之间有关联
   - 生成公钥和私钥(私钥自己留着，公钥放在github网站，进行用户验证对比)
   + 生成ssh密钥：
     + 任意目录打开git bash 并输入：ssh -keygen -t rsa -C xm123.qq.com
     + 打开c盘--用户--.ssh文件夹--id_rsa.pub--复制内容
     + 打开gihub网站--个人--设置--SSH设置--创建SSH密钥--输入复制内容
     + 在指定目录打开git bash,输入内容：
     + git push [ssh地址] master
     + 根据提示，输入yes,回车等待结果，看到done即表示成功。
     + (前提是已经提交到本地，`git init`, ` git add ./`, `git commit -m "msg"`)
     + 刷新github页面，查看上传内容。

 

 14.模拟上传测试：
   - 情况1：
     + 首先，小明本地执行了代码修改，并push上传到github，
       而后，小红本地执行了代码修改，并从GitHub下载pull代码库，
       此时，会发现小红本地代码库中有代码冲突错误。
     + 问题解决：小红需要手动处理代码冲突。
  
   - 情况2：
     + 首先，小明本地执行了代码修改3次，并push上传到github，
       而后，小红本地执行了代码修改2次，也push上传到github，
       此时，小红和小明的log版本都不一样，
       此时，小红还发现 push不上去GitHub，并且报错。
     + 问题解决：小红需要pull下载服务器代码库，若和本地代码库版本不同，
                还先解决冲突，再把最新的版本上传push到GitHub服务器。
 

 15.SSH地址简写
   - git remore add [变量名] [SSH地址]
     + git remote add orange git@github.com:rfrao/testgit0809.git

   - it push [变量名] master
   - git pull [变量名] master

   - 当我们在push时，加上 -u 参数，则在下一次push时只需要写 `git push`即可上传。
     + git push [变量名] -u master
     + git push 
     + 原理：加上 [-u]参数后，git会将当前分支与远程指定分支进行关联。
     + 注意：在不同仓库中，是不允许使用的，除非先pull下来。
   
   - Already up-to-date：本地代码版本库与服务器一致
