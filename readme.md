0.git概念
 - Git是目前世界上最先进的分布式版本控制系统（没有之一）。
 - 2008年GitHub网站上线了，它为开源项目免费提供Git存储，
   无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。


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
  
  - 注意：如果忘记写 -m 会进入vim编辑器界面，此时按下esc :   q   回车
  - 强制退出： esc  :   q!
 
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
   - git push [地址] master
   - 地址示例：
    $ git push https://github.com/rfrao/testgit0809.git master
   - 会把当前分支的内容上传到远程的master分支上。
   - 提交到对应的分支上（master）


   15.小红提交的内容


