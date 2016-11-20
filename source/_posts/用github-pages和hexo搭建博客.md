---
title: 用github pages和hexo搭建博客
date: 2016-07-19 21:31:24
tags:
---
[安装Git](http://www.baidu.com)
[安装Node.js](https://nodejs.org/en/)
<h2>搭建博客有两种方法:</h2>
*1. 使用username.github.io*
*2. 使用项目仓库*
**注意:项目仓库允许有多个，但是username.github.io只允许有一个;并且hexo只上传他的public文件**
## 注册及创建仓库
*注册这里就不再说明*
      **1. 使用username.github.io名建立仓库**
       添加一个名为username.github.io的仓库，进入仓库后设置settings,按下launch automatic page generator-->设置-->continue to layouts-->选择主题.
      **2. 创建项目仓库**
       此种方法创建仓库和以上方法类似，只不过将仓库名设为其他。之后创建另一个分支gp-pages,设置settings.
     **3. 打开Git**
        1. 创建.git
           mkdir name    //创建目录
           git init  
        2. 登录Git:  
        git config --global user.name "###" 
         //这里的名字不是github的昵称，是你的真实名字
        git config  --global user.email "###"
          //注册git时的邮箱
        3. 设置SSH
           在Git Bash中输入ssh-keygen,一路回车则可以生成ssh,
           将生成的ssh粘贴复制到settings里的ssh。
        4. 检测ssh是否设置成功
           ssh-T git@github  
        5. 采用username.github.io创建仓库时，在本地的git bash上把这个仓库复制下来
				git clone git@github.com:username/repository name				
           如果要推送东西的话依次用git add,git commit -m " ",git push命令(首先要切换到你想要的目录)
           如果是项目仓库的话同时需要这步。
        6. 在git bash上输入 npm install -g hexo  (安装hexo)
<br />
<h2>安装hexo及命令</h2>
   **主要命令**
   1. hexo s  ---- 在本地预览网页 
   2. hexo g   ---- 生成网页
   3. hexo deploy (hexo d)  ---- 部署.deploy目录
   4. hexo new -----新建文章
   5. hexo new page ---- 新建页面
   ***
   <strong>步骤</strong>
     在本地创建一个Hexo文件夹，鼠标右键选择Git Bash,依次输入命令：
       1. hexo init    创建网站所需的所有文件
       2. hexo g    
       3. hexo s
       4. 在浏览器地址栏输入localhost:4000  查看hexo博客
       5. 将hexo 和 github pages连接起来: 
       修改Hexo文件夹下面的_config文件：
       如果用第一种方法创建的仓库的话，将deploy的branch设为master,否则设为gh-pages;
       同时将deploy的repo设为仓库的SSH路径。
       在Hexo的Git Bash上输入下面命令
       `npm install hexo-deployer-git --save`    //安装一个包
       6. 上传到github上面
       hexo clean  清除缓存
       hexo g
       hexo d      //部署.deploy目录
       7. 还可以clone别人的主题
       如：`git clone https://github.com/wuchong/jacman.git themes/jacman`  
       更新主题时: 
          `cd themes/jacman`
          `git pull`
          将Hexo文件里的_config的theme设为你想要的主题

