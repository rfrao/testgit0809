1.git安装

2.初始化git仓库
 - 该仓库存放 项目代码的备份文件
 - .git是隐藏目录，备份文件所在目录
 - 项目右键打开 git bash
 - 命令 git init

3.用户信息配置
 - 用户名和邮箱
 - 每一次备份都会把当前备份者的信息存储起来
 - git config --global user.name "rfrao"
 - git config --global user.email "xx@qq.com"
 - --后面带的是参数，参数后面一般会跟值

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

   
5. 查看当前代码状态（有没有被放到门口，仓库中）
 - git status

 6.查看日志
  - git log 查看历史提交的日志
  - git log --oneline 查看简洁版日志

7.回退到指定的版本
  - 回退到上一次代码提交时的状态
    +  git reset --hard Head~0
  - 回退到上上次代码提交时的状态
    +  git reset --hard Head~1