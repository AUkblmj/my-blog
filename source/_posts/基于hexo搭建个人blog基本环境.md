---
title: 基于hexo搭建个人blog基本环境
date: 2024-08-19 21:37:49
author: AUkblmj
summary: 文章主要记录了我基于hexo搭建个人blog基本环境的步骤，便于自己以后的二次操作。

---

# 安装环境

> Nvm、Nrm、Node、Hexo、Git



## 1 安装nvm（可选）

> nvm（Node Version Manager）是 Nodejs 版本管理器，它能让我们方便的对 Node.js 的版本进行切换。
>

[Windows 版](https://github.com/coreybutler/nvm-windows)

[Mac 版](https://github.com/jerryc127/hexo-theme-butterfly)



### 1.1 下载安装包

<img src="https://img.picui.cn/free/2024/08/19/66c34fa1e1244.png" style="zoom: 67%;" />



### 1.2 完全删除之前的node（如果之前安装过的话）

1. 卸载[node](https://so.csdn.net/so/search?q=node&spm=1001.2101.3001.7020)本身、删除nodejs目录

   PS：可以在系统控制面板–>所有控制面板项–>程序和功能 卸载Node.js

2. 手动删除`C:\Program Files\nodejs\node_modules`(如果你的文件是在这里的话)

3. 手动删除`C:\users\`你的用户名`\node_modules`(如果你的文件是在这里的话)

4. 系统环境变量PATH中有关node和nvm的



### 1.3 运行 nvm-setup.exe 

> 文件路径可以自定义

<img src="基于hexo搭建个人blog基本环境.assets/66c3527ac2dd3.png" style="zoom:67%;" />



### 1.4 配置nvm环境变量

>  在 `自定义路径/nvm` 路径中创建nodejs文件夹（如果想要把node放在这里的话，默认应该是`C:\Program Files\nodejs`）

<img src="基于hexo搭建个人blog基本环境.assets/66c353971659e.png" style="zoom: 67%;" />

> 更改环境变量

<img src="基于hexo搭建个人blog基本环境.assets/66c3547fbdf8c.png" style="zoom:67%;" />



### 1.5 nvm换源

> `自定义路径/nvm/setting.txt` 文件末尾加入

```bash
node_mirror: https://npmmirror.com/mirrors/node/
npm_mirror: https://npmmirror.com/mirrors/npm/
```

<img src="基于hexo搭建个人blog基本环境.assets/66c353971659e.png" style="zoom: 67%;" />



### 1.6 检查nvm是否安装成功

```bash
nvm -v
```



---



## 2 安装node（npm）

### 2.1 安装node

> npm（Node Package Manager），Node.js 的包管理器，安装 Node.js 之后自带 npm，无需单独安装

> 方法一：通过node官网安装
> 
> [node官网]([Node.js — Download Node.js® (nodejs.org)](https://nodejs.org/en/download/package-manager))

> 方法二：通过nvm安装
>
> 安装node命令及nvm常用命令如下

```bash
nvm on							// 启用 Node.js 版本管理
nvm list available       		// 显示可以安装的所有 Node.js 的版本
nvm install <version>    		// 安装指定版本，可模糊安装，例如：nvm install v6.2.0 或 nvm install 6.2
nvm uninstall <version>  		// 删除已安装的指定版本，语法与 install 类似
nvm use <version>        		// 切换使用指定的版本 node
nvm ls                   		// 列出所有安装的版本（ * 指向当前使用版本）

nvm off                  		// 禁用 Node.js 版本管理(不卸载任何东西)
nvm								// 显示nvm其他命令（英文版）
```



### 2.2 检查node是否安装成功

```bash
node -v
```



### 2.3 配置node环境变量

> 在上文提到的nodejs目录`G:\AUSoftWare\nvm\nvm1.1.12\nvm\nodejs`中创建 `"node_global"` 和 `"node_cache"` 两个文件夹

<img src="基于hexo搭建个人blog基本环境.assets/66c35b5f9b7e4.png" style="zoom:67%;" />

>  进入 cmd 命令行，输入以下命令

```bash
npm config set prefix G:\AUSoftWare\nvm\nvm1.1.12\nvm\nodejs\node_global
npm config set cache G:\AUSoftWare\nvm\nvm1.1.12\nvm\nodejs\node_cache
```

设置全局模块的安装路径到 `"node_global"` 文件夹，
设置缓存到 `"node_cache"` 文件夹

> 设置环境变量

把 `G:\AUSoftWare\nvm\nvm1.1.12\nvm\nodejs\node_global` 加入到系统环境变量 PATH 中，方便直接使用命令行运行

> 添加管理员权限

找到先前创建的 `"node_global"` 和 `"node_cache"`两个文件夹
分别`右击`文件夹 --> 选择`属性` --> 点击`安全`，全部打勾

<img src="基于hexo搭建个人blog基本环境.assets/66c35ccc8c928.png" style="zoom:67%;" />



---



## 3 安装nrm（可选）

> nrm（NPM registry manager），国内使用 npm 官方源来安装包的时候比较慢，所以经常会需要修改 npm 源地址。npm 倒是提供了修改源的方法，但是 使用nrm 换源更加方便快捷。
>

### 3.1 安装nrm

```bash
npm install -g nrm   // 使用 npm 全局安装
```



### 3.2 nrm常用命令

```bash
nrm ls				// 显示全部镜像源
nrm use taobao		// 切换taobao镜像源
nrm test			// 测速
nrm -h				// 查看帮助
```



---



## 4 安装hexo

```bash
npm install -g hexo-cli

hexo -v						// 验证是否安装成功
```



---



## 5 创建GitHub仓库

在GitHub中创建一个名为`<用户名>.github.io`的仓库



---



## 6 连接GitHub

### 6.1 安装Git

[Git官网下载地址]([Git - Downloads (git-scm.com)](https://git-scm.com/downloads))

- Git CMD 是windows 命令行的指令风格
- Git Bash 是linux系统的指令风格（建议使用）
- Git GUI是图形化界面（新手学习不建议使用）



### 6.2 Git环境配置

```bash
git config -l  										//查看所有配置
git config --global user.name "你的用户名"		 	//配置用户名
git config --global user.email "你的邮箱"		 	//配置密码
```



### 6.3 GitHub的ssh配置

`ssh-keygen -t rsa -C "你的邮箱"`

生成ssh公钥，在提示文件夹中找到`id_rsa.pub`文件，复制其内容到`GitHub --> Settings --> SSH and GPG keys --> New SSH key`中

> 注意: 要是有【Key type】的选择项 ，选择默认Authentication Key 即可。



### 6.4 测试连接

```bash
ssh -T git@github.com
```

出现`Hi xxx! You've successfully ...`内容即连接成功