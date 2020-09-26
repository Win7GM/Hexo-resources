---
title: 基于Hexo的博客的安装和配置
tags: [manual,unfinished]
categories: [杂项, 博客]
---

也不知道能写点啥，姑且写写博客配置的过程吧。

## 博客的安装

我使用的是 Debian 9 x64。安装 Hexo 需要先安装 Node.js 和 Git 。
:::note danger
**你需要 `root` 权限。**
:::

### 安装Git
```bash command:("[root@localhost] $":1)
sudo apt-get install git-core
```
### 安装Node.js
```bash command:("[root@localhost] $":1-2)
curl -sL https://deb.nodesource.com/setup_current.x | bash -
apt-get install -y nodejs
```

### 安装Hexo
在安装完 *Git* 和 *Node.js* 之后，我们便可以使用 npm 来安装 *Hexo* 。
```bash command:("[root@localhost] $":1)
npm install -g hexo-cli
```
## 初始化博客
在安装完后，你需要手动新建博客。
```bash command:("[root@localhost] $":1,4-5)
hexo init <folder>  #你想要的文件夹的名称
#该命令会使Hexo初始化一个新博客于你指定名称和路径的文件夹。
#例如你在~/下执行 hexo init blog，就会建立一个为~/blog的文件夹用于存放博客数据。
cd <folder> ·       #切换到博客根目录
npm install
```
程序运行完毕后，指定文件夹的目录应该会被初始化如
```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```
### _config.yml
该文件存放博客的配置信息。有些插件也需要在此处进行设置。

### package.json
应用程序的信息。EJS，Stylus 和 Markdown renderer 默认会被安装，你可以自由移除。
```
package.json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": ""
  },
  "dependencies": {
    "hexo": "^3.8.0",
    "hexo-generator-archive": "^0.1.5",
    "hexo-generator-category": "^0.1.3",
    "hexo-generator-index": "^0.2.1",
    "hexo-generator-tag": "^0.2.0",
    "hexo-renderer-ejs": "^0.3.1",
    "hexo-renderer-stylus": "^0.3.3",
    "hexo-renderer-marked": "^0.3.2",
    "hexo-server": "^0.3.3"
  }
}
```

### scaffolds
模板文件夹。新建文章时，Hexo 会根据其内容物来建立文件。
Hexo的模板指的是在新建的文章（.md）中默认填充的内容。

### source
资源文件夹。存放用户资源。除了`_posts`文件夹之外，开头命名为`_`的文件/文件夹和隐藏的文件将被忽略。Markdown 和 HTML 文件会被解析并放到 `public` 文件夹，其余文件会被直接拷贝。

### themes
主题文件夹。Hexo 会根据主题来生成静态页面。

## 使用 Git 同步博客源文件
在实际的使用中，你可能像我一样因为诸如ssh操作不便，希望能在远端修改配置等原因，想把文件上传到 Github 的私有仓库或自家 NAS 的 git 仓库里慢慢改。

### Git 使用
首先，确定你在博客的根目录下。执行：
```bash command:("[root@localhost] $":1)
git init
```
如此，你初始化了一个空的 Git 仓库。

使用`ls -a`命令可以查看当前目录下的所有文件/文件夹。你可以看到在你的博客根目录下生成了`.git`文件夹。

接下来，你可以使用
```bash command:("[root@localhost] $":1)
git add ./
```
来添加该目录下的所有文件/文件夹到你的git仓库暂存区中。

:::note warning
值得注意的是，如果该目录下的文件夹中包含`.git`文件夹，即该文件夹有另外一个git仓库，**该文件夹内的文件不会被添加到仓库中。**
:::

:::note warning
另外，每次你修改文件后想要推送，都需要先执行一次`git add ./`，来将修改后的文件添加到暂存区。
:::

在将文件推送至远端 git 仓库前，你需要先将暂存区提交到本地仓库。执行：
```bash command:("[root@localhost] $":1)
git commit -m "你的提交信息"
```
以将暂存区提交到本地仓库。

成功提交后，你可以执行：
```bash command:("[root@localhost] $":1)
git push <你的远端git地址> <分支名>
#例如 git push git@github.com:Win7GM/Hexo-resources.git master
```
以将本地仓库内容推送到远端 git 仓库。

## 配置博客
### _config.yml
_config.yml是博客的基础配置。















## 引用
+ [Hexo]
+ [Yume Shoka]




[Hexo]:https://hexo.io/zh-cn/docs/
[Yume Shoka]:https://shoka.lostyu.me/computer-science/note/theme-shoka-doc/
