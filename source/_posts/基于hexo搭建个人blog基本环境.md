---
title: 基于hexo搭建个人blog
date: 2024-08-19 21:37:49
author: AUkblmj
description: 文章主要记录了我基于hexo搭建个人blog基本环境的步骤，便于自己以后的二次操作。
cover: https://s2.loli.net/2024/09/27/RVqdXEJaw57Iiy6.jpg

---

# 前言

> 本文是一篇记录笔记，只记录主要步骤，细节问题可自行搜索
>
> 主要参考教程：[基于 Hexo 从零开始搭建个人博客系列 | 唐志远 (fe32.top)](https://fe32.top/articles/hexo1600/)



# 安装环境

> Nvm、Nrm、Node、Hexo、Git



## 1 安装nvm（可选）

> nvm（Node Version Manager）是 Nodejs 版本管理器，它能让我们方便的对 Node.js 的版本进行切换。
>

[Windows 版](https://github.com/coreybutler/nvm-windows)

[Mac 版](https://github.com/jerryc127/hexo-theme-butterfly)



### 1.1 下载安装包

![Snipaste_2024-09-27_16-55-07.png](https://s2.loli.net/2024/09/27/pZdOb9PBiRujCq2.png)

![Snipaste_2024-09-27_16-56-39.png](https://s2.loli.net/2024/09/27/NZEActl2ogSp5k1.png)



### 1.2 完全删除之前的node（如果之前安装过的话）

1. 卸载[node](https://so.csdn.net/so/search?q=node&spm=1001.2101.3001.7020)本身、删除nodejs目录

   PS：可以在系统控制面板–>所有控制面板项–>程序和功能 卸载Node.js

2. 手动删除`C:\Program Files\nodejs\node_modules`(如果你的文件是在这里的话)

3. 手动删除`C:\users\`你的用户名`\node_modules`(如果你的文件是在这里的话)

4. 系统环境变量PATH中有关node和nvm的



### 1.3 运行 nvm-setup.exe 

> 文件路径可以自定义



### 1.4 配置nvm环境变量

>  在 `自定义路径/nvm` 路径中创建nodejs文件夹（如果想要把node放在这里的话，默认应该是`C:\Program Files\nodejs`）（随着使用缓存会越来越大，不建议放在C盘）

![Snipaste_2024-09-27_16-57-43.png](https://s2.loli.net/2024/09/27/QqC9xlAedOEUwTS.png)

> 更改环境变量

![image.png](https://s2.loli.net/2024/09/27/fu3NhkFsUZxdRlY.png)



### 1.5 nvm换源

> `自定义路径/nvm/setting.txt` 文件末尾加入

```bash
node_mirror: https://npmmirror.com/mirrors/node/
npm_mirror: https://npmmirror.com/mirrors/npm/
```

![Snipaste_2024-09-27_16-58-59.png](https://s2.loli.net/2024/09/27/fWN4J3TuBlsc9GV.png)



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

![Snipaste_2024-09-27_17-02-45.png](https://s2.loli.net/2024/09/27/MU2PsH6Id8SVOLa.png)

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



---



## 3 安装nrm（可选）

> nrm（NPM registry manager），国内使用 npm 官方源来安装包的时候比较慢，所以经常会需要修改 npm 源地址。npm 倒是提供了修改源的方法，但是 使用nrm 换源更加方便快捷。
>

### 3.1 安装nrm

```bash
npm config set registry https://registry.npmmirror.com	//npm换源
npm install -g nrm   // 使用 npm 全局安装
```



### 3.2 nrm常用命令

> 刚安装好指令无法找到，重启cmd即可

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



---



# 初始化项目

## 1 初始化Hexo项目

```bash
cd /g/AUBlog/AUkblmj
hexo init my-blog				//初始化项目
cd my-blog
npm i							//安装相关依赖
hexo s							//本地运行
```

> 项目结构如下：

| 文件名                | 功能                                   |
| --------------------- | :------------------------------------- |
| node_modules          | 依赖包                                 |
| scaffolds             | 生成文章的一些模板                     |
| source                | 用来存放你的文章                       |
| themes                | 主题                                   |
| .npmignore            | 发布时忽略的文件（可忽略）             |
| _config.landscape.yml | 主题的配置文件                         |
| _config.yml           | 博客的配置文件                         |
| package.json          | 项目名称、描述、版本、运行和开发等信息 |



---



## 2 将静态博客挂载到 GitHub Pages

```bash
npm install hexo-deployer-git --save		//安装hexo-deployer-git
```



> 修改`_config.yml`文件，建议使用vs code编辑

```yml
deploy:
  type: git
  repository: git@github.com:AUkblmj/AUkblmj.github.io.git
  branch: main
```



> 部署到GitHub
>
> 注：之后修改文件，重新部署到GitHub均为此操作

```bash
hexo clean 
hexo g
hexo d
```

如果出现`Deploy done`，则说明部署成功。

访问网址：`aukblmj.github.io`



---



## 3 设置个人域名

购买个人域名后，在域名云解析中添加解析记录

{% image https://img.picui.cn/free/2024/08/20/66c4905b034cf.png %}

> 这时候你的项目根目录应该会出现一个名为CNAME的文件。如果没有的话，打开my-blog/source目录，新建CNAME文件，注意没有后缀。然后在里面写上域名(例如：aukblmj.top)，保存。最后运行hexo g、hexo d上传到github。这样到最后当你在地址栏输入xxx.github.io时，才会自动跳转到你的域名。

打开github博客项目，点击`settings`，点击`Pages`，拉到下面`Custom domain`处，填上你自己的域名 ，Save保存。

> 注意：这一步之后每次重新部署可能都要操作一遍



----



# 主题安装

> 本站使用[hexo-theme-butterfly]([jerryc127/hexo-theme-butterfly: 🦋 A Hexo Theme: Butterfly (github.com)](https://github.com/jerryc127/hexo-theme-butterfly))主题

> Git安装

```bash
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

使用Git安装后续魔改时更改的文件都是`G:\AUBlog\AUkblmj\my-blog\themes\butterfly`文件夹中的文件

> 升级方法：在主题目录下，运行git pull



> 安装渲染器

```bash
npm install hexo-renderer-pug hexo-renderer-stylus --save
```



> 升级建议

把主题文件夹中的 `_config.yml` 复制到 Hexo 根目录里，同时重新命名为 `_config.butterfly.yml`。

以后只需要在 `_config.butterfly.yml`进行配置就行。

Hexo会自动合併主题中的`_config.yml`和 `_config.butterfly.yml`里的配置，如果存在同名配置，会使用`_config.butterfly.yml`的配置，其优先度较高。



---



# 基础页面配置

## Front-matter

> Front-matter 是 markdown 文件最上方以---分隔的区域，用于指定个别档案的变数。
>

```markdown
---
title:
date:
updated:
type:
comments:
description:
keywords:
top_img:
mathjax:
katex:
aside:
aplayer:
---
```

| 写法             | 解释                                                         |
| :--------------- | ------------------------------------------------------------ |
| title            | 【必需】页面标题                                             |
| date             | 【必需】页面创建日期                                         |
| type             | 【必需】标签、分类和友情链接三个页面需要配置                 |
| updated          | 【可选】页面更新日期                                         |
| description      | 【可选】页面描述                                             |
| keywords         | 【可选】页面关键字                                           |
| comments         | 【可选】显示页面评论模块(默认 true)                          |
| top_img          | 【可选】页面顶部图片                                         |
| mathjax          | 【可选】显示mathjax(当设置mathjax的per_page: false时，才需要配置，默认 false) |
| katex            | 【可选】显示katex(当设置katex的per_page: false时，才需要配置，默认 false) |
| aside            | 【可选】显示侧边栏 (默认 true)                               |
| aplayer          | 【可选】在需要的页面加载aplayer的js和css,请参考文章下面的音乐 配置 |
| highlight_shrink | 【可选】配置代码框是否展开(true/false)(默认为设置中highlight_shrink的配置) |



---



## 标签页

1.前往Hexo博客根目录，打开cmd命令窗口执行`hexo new page tags`。

2.在【my-blog/source/】会生成一个含有index.md文件的tags文件夹。

3.修改【my-blog/source/tags/index.md】，添加`type: "tags"`



---



## 分类页

1.前往Hexo博客根目录，打开cmd命令窗口执行`hexo new page categories`。

2.在【my-blog/source/】会生成一个含有index.md文件的categories文件夹。

3.修改【my-blog/source/tags/index.md】，添加`type: "categories"`



---



## 文章

```bash
hexo n 文章名称
```

即会在`G:\AUBlog\AUkblmj\my-blog\source\_posts`中生成文章名称.md文件，可在其中书写文章内容


