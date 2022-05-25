## 今日知识点

##### 一、GIT

1.分布式版本控制系统

2.作用：项目集中管理（多人协同开发，历史版本回滚）

3.版本控制系统：GIT，SVN，CVS...

4.工作原理：



5.GitHub：使用git做管理的仓库，面向所有人开放，免费版本的项目必须是开放性的，国内使用码云

6.使用git前期准备：1.下载安装

​						   2.注册码云/GitHub账号：个人中心-》提交邮箱设置

7.如何使用git管理代码：1.命令行（Git Bash）

​										  2.图形化工具（Git GUI，SourceTree）

8.如何使用命令行操作：

```js
仓库为空，本地创建git项目之后提交到仓库中
1.创建项目文件夹（本地git仓库）
2.在项目文件夹中右键：选择Git Bash
3.初始化项目：git init  -- 会出现一个.git的隐藏文件夹
4.将项目文件拷贝到本地仓库中
5.链接远程仓库（GitHub或码云上的仓库）
  git remote add origin 仓库地址
6.查看当前git仓库状态：git status
7.添加上传文件：git add 文件名  或 git add .(全部提交)
8.添加上传文件说明：git commit -m "说明"
9.推送文件到远程仓库：git push -u origin master  -- 仓库为空，第一次推送
10.推送：git push [origin 分支名]

配置全局环境：当前客户端信息（提交账号和用户）
1.git config -l ：查看当前配置
2.git config --global user.email "你的提交邮箱"
3.git config --global user.name "用户"

已有仓库，直接从仓库拉取代码到本地仓库中
1.在本地创建git仓库：创建git仓库文件夹，通过Git Bash的git init命令初始化仓库
2.连接远程仓库：git remote add origin 仓库地址
3.拉取代码：git pull [origin 分支名]-- 从默认地址拉取
		   git pull [origin 分支名] 仓库地址  -- 从指定仓库拉取

本地仓库和远程仓库不一致时，如何解决：
1.拉取远程仓库内容：git pull origin master --allow-unrelated-histories   --  本地仓库和远程仓库不一致时，先拉取远程仓库
2.输入合并信息：输入完成后，按Esc退出Insert模式，然后输入:后再输入：wq  --  保存退出
3.将本地仓库推送到服务器：git push origin master

分支
1.创建分支：git branch 分支名
2.切换分支：git checkout 分支名
3.合并分支：git checkout 主分支
		  git merge 分支名
4.删除分支：git branch -d 分支名

创建公钥
1.本地生成公钥：ssh-keygen -t rsa -C "xxxx@qq.com"
2.最终会生成文件：id_rsa  id_rsa.pub
3.id_rsa.pub中的内容就是公钥
```

9.HTTPS：需要将开发者加入到仓库中

10.SSH：将开发者的SSH Key添加到仓库中（只对当前项目有拉取的权限）或者添加到git账号中（对当前账户下的所有仓库具有拉取和推送的权限）

##### 二、Webpack

1.是一个用于现代 JavaScript 应用程序的静态模块打包工具，当 webpack 处理应用程序时，它会递归地构建一个依赖关系图，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个 bundle

2.作用：解决前端开发中为了提高效率而额外多出的文件、代码、依赖包

   合并，压缩，打包

3.相关概念

```
1.入口(entry point)：指示webpack应该从哪个文件开始构建依赖图，默认的为./src/index.js，可通过配置文件的entry进行配置
2.输出(output)：webpack打包之后的文件放置在什么目录下，叫什么名字，默认的是./dist/main.js，其他文件都会放在dist目录下，通过output设置
  output:{
  	path:"输出文件保存目录"  -- Node.js中，使用path模块指定
  	filename:"输出文件的名字"
  }
3.loader：webpack本身只能处理JavaScript和Json文件，如果需要转换其他文件那么就需要对应的loader。loader需要根据转换的文件安装对应的loader，然后在配置文件中，通过module.rules进行配置
4.插件(plugin)：打包优化，资源管理，注入环境变量，通过require引入，然后在配置中由plugins设置
5.模式(mode)：启用webpack在相应模式下的优化，可以设置为production，development或none，默认为production
```

4.安装：

```
npm install webpack [-g]
npm install webpack-cli [-g]
```

5.配置文件：webpack.config.js 

```
webpack4以上，可以不用配置文件，会使用默认配置
module.exports = {
	entry:"入口文件",
	output:{
		path:"打包文件目录",
		filename:"打包文件名"
	},
	mode:"production"
}
```

##### 三、FTP

1.FTP协议：文件传输协议，由ftp服务器和ftp客户端组成

2.FTP服务器：存储文件

3.FTP客户端：可以通过ftp协议访问ftp服务器上的资源，实现对ftp服务器资源的上传下载

4.端口号：20和21

   20用于传输数据，21用于传输控制信息