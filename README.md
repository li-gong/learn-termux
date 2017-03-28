# learn-termux
RE:从零开始的termux学习生活

## 前言 ##
>Termux是一款强大的安卓终端模拟APP，无需root直接启动，自动安装最小化linux系统，使用APT作为包管理工具并提供各种各样的软件包。
高级终端Termux组合了强大的终端模拟和拓展Linux包收集支持。
• 享受bash 和 zsh。
• 使用nano 和 vim编辑文件。
• 通过ssh访问服务器。
• 使用gcc和clang编译代码。
• 使用python控制台来作为口袋计算器。
• 使用git 和 subversion检查项目。
• 使用frotz运行基于文本的游戏。
[官方网站](https://termux.com/)

这个应用真的很有意思，不过对于新手而言确实不太友好。比如说我可以说是从零开始学习这些知识。一大堆之前从未接触过的概念直接甩在脸上，让我相当蒙逼。在这里把我折腾这个应用的经历写一写，希望可以给后来的人一些参考吧。

目前我的水平是能够简单地使用这个软件并使用它做一些简单的操作。比如说我的这篇文章就完全是在termux里完成、修改和上传的。那么我以一个萌新的身份来讲讲termux的一些基础使用以及用termux进行书写的方法。顺带一提我现在对这个应用的理解依然不够深，之后还会不断地进行补充和修改。

## 第一章 一切歧途，自此而始 ##

#### 1.1 termux的安装 ####

软件的下载推荐去下面的三个地方。酷安基本上是国内最良心的应用市场了吧，如果出现问题在评论区里留言也有热心的酷友帮忙解决，真的很不错。当然如果你有条件翻墙的话也是很推荐去play下。搜索termux除了能找到本体，还有各种插件。可以根据介绍按需下载。f-droid是开源应用的应用市场，同样可以下载插件，而且无需翻墙。

1. [酷安](http://www.coolapk.com/apk/com.termux)
2. [Google play](https://play.google.com/store/apps/details?id=com.termux)
3. [f-droid](https://f-droid.org/repository/browse/?fdid=com.termux)

下载后你会发现termux的安装包仅仅只有172.71K。那么这么小的体积是如何实现这么多功能的？其实除了基础的一些功能。上面提到的需要通过自带的包管理器来下载和安装。所以在初次配置时是必须要联网来下载的。当然现在我是有网络，所以直接安装就行了。完成后打开看见的没有配置过的termux是这样的……
![假装这里有图片](./pic/1。png)

可以看到上面出现了几行termux的介绍，而且界面看起来很简陋。这在之后可以进行更改，这里就先不做介绍。现在先试试一些基本的操作。

比如说用ls查看一下目录，可以看到当前目录下只有一个文件夹。用 cd storage 命令进入文件夹，再次ls可以看到这些。




还有一个基础的操作就是更新一下软件源以及升级一下软件。

    apt update
    apt upgrade

这两步操作可以经常做，可以保证你的软件都是最新的。

输入clear命令可以清除上面的内容。


然后用一下这个指令

    apt list

列表里的是可以直接用apt install 命令进行安装的软件。你可以尝试自己安装看看。

基础的安装方面就讲的差不多了。这一节就这样结束吧。

如果不是新手的话，在使用这个应用时是不是觉得少了几个关键的按键？比如说用来补全命令的TAB键。显然termux也考虑到了这种情况。所以在应用里是提供了这些这些按键的。只不过默认关闭，需要我们自己动手打开。

打开的方式也很简单。我们按音量上键+键盘的Q就可以看到：输入法的上方出现了一个按键条，上面就有使用命令行时频繁使用的几个键。

当然，也是有其他的方法可以使用这几个按键的，比如说黑客键盘就自带有这些按键，但是我的目标是在termux里写东西，所以输入中文是必须的。而黑客键盘并不支持中文的输入。而频繁切换输入法显然也不是什么高效的方法。所以还是自带的这个按键条更加符合我的要求。而且百度输入法虽然流氓，但是可以自己修改皮肤确实很方便。或许可以自定义出一个更加方便在termux里试用的输入法。不过具体的方法我还在学习当中。只能之后再更新了。

#### 1.2 颜值是第一生产力 ####

一个赏心悦目(~~逼格满满~~)的外表是愉快地使用一个应用的必要前提，显然现在的termux颜值并不高。怎么样才能让我们的termux跟电影里的黑客那样呢……不要着急，我们现在就开始让termux的颜值上升(๑•̀ㅂ•́)و✧

首先我们要做的是去除每次打开termux都会出现的几行文字。方法在0.48版本的更新日志里有说明。
>Remove the dialog for new users in favour of an inline help message at startup (unless ~/.hushlogin exists).

也就是说只要有 ~/.hushlogin 文件存在就不会显示了。要创建文件方法也很简单。因为现在的目录就是 ~ ，所以只要直接用创建命令就好了。而我第一次的错误就是发生在这里。我误以为需要创建的是文件夹，所以我当时的操作是这样的。

    mkdir .hushlogin

结果自然是不行……接着我尝试创建一个文件。

    vi .hushlogin

然后输入:wq保存退出。(VIM之后再详细介绍)

输入exit退出，重新打开。可以看到那几行字已经消失不见了。这就清爽多了(๑•̀ㅂ•́)و✧

之后就是安装可以说是目前最强shell的ZSH以及用来配置ZSH的oh-my-zsh。不过这个下载和安装酷友给出了一个比较方便的方法。具体介绍可以看[这里](https://github.com/Cabbagec/termux-ohmyzsh)

那么根据README.md的介绍我们首先要安装的是curl工具。很简单，直接apt install curl就可以了。在滚完之后就可以安装termux-ohmyzsh了。

    sh -c "$(curl -fsSL https://github.com/Cabbagec/termux-ohmyzsh/raw/master/install.sh)"

接着一路确认、回车就好了。不需要修改，因为默认的主题我还挺喜欢的。当然如果不喜欢在之后可以进行更改。
完成后可以看到，终端已经变成了彩色。
![这是一个图片](.pic/3)

一款简单美化过的应用就这样完成了。真是可喜可贺，可喜可贺。

接下来稍微放松一下，来点有趣的小玩意吧！

这里推荐一个tree命令，他可以以树形结构显示文件目录结构。输入tree 回车。因为这时候我们并没有安装，所以会有这样的一个提示。![假装这里有图片](./pic/2)提示上写的很清楚，我们需要先进行安装。而且还很贴心地给出了安装的命令。我们对照着打就是了。


    apt install tree

这时候试试tree命令。可以看到有一个storage文件夹以及它的子文件夹所链接的文件夹......![假装这里又有一张图片](.pic/3。png)


再来个小玩意

    apt install cmatrix

然后运行一下这个命令

    cmatrix

![这是一个动态图片](.pic/4)

看那满满的逼格😂感觉都可以拿来做动态壁纸了🤔

这里来个小提示:在命令后加上-h可以查看命令的一些简单的提醒。

试试cmatrix -h命令会有下面的提示:


可以看到各种可添加的后缀的作用。这是学习一个陌生命令很好的一个方式。除此之外还有man命令：只要在一个命令前加上个man，就能看到这个命令的详细介绍。（当然，全都是英文😂）

#### 1.2 简单易懂的ZSH配置方法 ####

>Zsh 是一款功能强大终端（shell）软件，既可以作为一个交互式终端，也可以作为一个脚本解释器。它在兼容 Bash 的同时 (默认不兼容，除非设置成 emulate sh) 还有提供了很多改进，例如：更高效、更好的自动补全、更好的文件名展开（通配符展开）、更好的数组处理、可定制性高.——[archwiki](https://wiki.archlinux.org/index.php/Zsh)

除了Zsh还需要一个方便配置Zsh的强大工具，oh-my-zsh。除了可以提高颜值，它还拥有很多的提高效率的插件。真的非常重要。(不过这两个在安装termux-ohmyzsh时已经安装好了学会使用即可#(二哈))

首先介绍一下Zsh的强大之处。
