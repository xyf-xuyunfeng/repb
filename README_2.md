# 移动app第2天

## 反馈问题
  - 速度;
  - 提交到服务器(github)
  - 上传博客(github博客)

## 回顾Git
- git是什么?
  + git 版本管理
- git 如何初始化一个git仓储
  + git init
- git 添加文件到暂存区
  +　git add [file]
- git提交暂存区文件到仓库中
  + git commit -m ""
- git status
  + 查看当前状态
- 查看日志:
  + git log
  +　git log --oneline

- git diff
  + 对不同版本的文件的不同

- 提交到远程服务器
  + git push [地址] master
- git remote add origin [地址]

- 搭建博客
  +　gh-pages



## Git继续
  - 使用ssh的方式上传代码

### 1.创建公钥私钥
  - 命令: `ssh-keygen -t rsa`
    ＋　这个命令会生成一个公钥和私钥，在ｃ盘用户目录下的.ssh目录。要把生成的公钥提供给服务器.
  - 不要重复使用这个命令：
    +　这个命令每一次生成的公钥私钥都不一样，

### 团队配合开发
    1. 初始化一个仓储，提交到远程服务器
    2. 从远程服务器下载仓储.
    3. 修改代码添加功能，
    4. 然后再提交到服务器（需要在本地先提交）

    *在团队开发中，一定要先拉再提交,push之前需要先pull一下*;
      - git pull [地址] [分支名].



### 从远程服务器拉取时出现冲突。
  - 如果遇到冲突，需要自己手动去处理冲突，选择想要保留的代码。
  - 如果解决冲突的时间太长，这个期间已经有个再次提交，我们需要再一次的pull代码。

### git使用流程
  - 1.新建文件夹，在文件夹中使用命令：`git init`初始化一个空的仓储
    ＋　这一步会在当前目录创建一个隐藏的.git文件夹
  - 2.开始写我们的项目，就在这个文件夹(.git同级目录)中写，写的时候就像我们之前一样去写。
  - 3.每次写完一个功能需要添加到暂存区
  - 4.把暂存区的代码提交到仓库。
  - 4.5如果，服务器仓储不是空的，我们需要先拉取到本地，然后解决冲突。
  - 5.把本地仓库里的代码提交到远程服务器
      + https
      + ssh
  - 6.继续更改我们的代码.
  - 7. 添加到暂存区，然后提交到本地仓库
  - 8.先pull，有冲突就解决冲突， 再提交到远程服务器。
  - 9.终于做完了

## bower
  - .bowerrc
    {
      "directory":"lib"
    }
  - 

## 开发问题
  - html,js ,css

## browser-sync
  - 用于浏览器刷新。
  - 安装:`npm install borwoser-sync -g`

  - 需要全局安装
  - 使用的命令:
    +`browser-sync start --server --files "./index.html" `
    + files参数的内容可以以逗号分割,*.html表示所html;
      css/*.css表示css目录下所有css   js/*.*

### browser-sync
  - 多浏览器兼容性同测试。

### 5.1.Gulp简介
- 链接：
    + [官网](http://gulpjs.com/)
    + [中文网](http://www.gulpjs.com.cn/)

- 构建前端自动化工作流
  + js压缩，混淆
    * 合并，css 字体图标，精灵，
  + css压缩
  + html压缩

- 依赖于npm
-  工具都全局安装的,`npm install -g gulp`

### grunt 也是用来构建自动化工作流。
### webpack


### gulp只有5个方法
  - task - gulp中每做一个件事情都认为是一个任务
    - task('任务名',function(){})
  - src('./test.js') //
    + src('./js/*.js')
  - dest('') 指定处理的文件的输出路径。
  - watch('./js/*js',['任务名']) // 监视文件的变化，自动执行相应任务.
  - run('任务名') // 运行，就是运行指定任务


### gulp还需要进行非全局安装
  - `npm install gulp --save-dev`

### 需要在当前项目目录新建一个名为gulpfile.js的文件
  - 在这个文件中写我们的代码

### 在开发环境中写代码
  - 然后在生产环境中调试代码(最终是要给用户看，是要架设到服务器上的代码c)
  - 在src目录中进行代码
  - 最终通过gulp之类的构建工具把代码生成到dist目录(publish)

### gulp插件
  - 1. gulp-uglify 
    +压缩，混淆js文件的
  - 2. gulp-concat
    + 合并js，或者css文件
  - 3. gulp-cssnano
    + 用来压缩css文件。
  - 4. gulp-htmlmin
  - 5. gulp-sass ,
  - 6. browserSync
  - 7. gulp-autoprefixer


https://www.imfreevpn.com