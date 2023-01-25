# Docsify+markdown+githubpage 开发

[返回程序开发笔记](Coding.md)

## 背景知识

这里介绍三项背景知识，分别是 markdown, docsify 和 github page。熟悉它们的小伙伴可以直接跳到下一节“下载模板”

### Markdown 

Markdown 是一种标记语言。早期的HTML开发通常要在网页内容的基础上用标记语言写明格式和排版。这样的创作方法不仅降低了效率，而且容易让人在创作时打乱思维，无法聚焦于写作。

Markdown 的出现是为了解决这个问题。比如，以下的代码

``` 
### Title
```
会直接有以下效果
> ### Title

如果要写一个表格，只需要

```
Row 1| Row 2
-|-
Cell 1|Cell 2
Cell 3|Cell 4
```

它的效果是

> Row 1| Row 2
> -|-
> Cell 1|Cell 2
> Cell 3|Cell 4


这一篇笔记，就是用Markdown 写成。它既能做到不打断创作者的写作思路，又能自动给创作内容以格式用于展示。同时做到让读者和作者都舒服。

资源|地址|说明
-|-|-
Markdown 学习资源|[Markdownguide.org](https://www.markdownguide.org/basic-syntax/)|
Marddown 实验沙盒|[Hackmd.io](https://hackmd.io)|在这里试试写markdown

### Docsify

我们在写好markdown 文件后，其展示页面是需要编译的。如果说一个markdown源文件是作者友好的，那么编译的意义在于把它排版成一个读者友好的文件。Docsify 可以帮助我们的markdown文件**自动编译**成为具有相互链接的网页。这里的自动是指我们不需要任何额外的操作过程，只需要上传markdown文件，我们所得到的就是一个网页。完全不需要我们特意的写任何程序或者标记语言。

资源|地址|说明
-|-|-
Docsify 开发项目效果展示|[Awesome Docsify](https://github.com/docsifyjs/awesome-docsify)|
Docsify 主页|[Docsify](https://docsify.js.org/)|

### Github Page

当我们写好自己的博客后，Github的角色相当于服务器。Github page 是最简单的hosting。我们只需要将我们的作品push到github上，github page就能自动生成我们的页面。

Github Page 的操作十分简单，基本上只需要建立一个一个github账号，比如 `username`，然后再建立一个 repository, 名字恰好是 `username.github.io`, 比如如果你的名字是 `honeymath`，那你需要建立的库是 `honeymath.github.io`。之后只需要将你所有的docsify里的源文件push到这个 repository里面，等待10分钟，你的github page就available了，并且可以通过 `username.github.io`访问。不需要特别的其他步骤。

资源|地址|说明
-|-|-
Github Page 官方说明|[Github Page settings](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)|
Github 使用说明||


## 下载模板

[点击下载](http://qirui.li/DocsifyTemplate.zip)我为新手准备的模板。这是一个zip文件，下载后可以看到一个文件夹名为 `test`有四个文件。其中 `index.html`和`.nojekyll`文件都是已经配置好的文件不需要管。我们的内容创作在 `README.md`中完成，可以看到还有一个文件是`test.md`，这些文件都是通过超链接互相可以跳转的。系统默认进入的第一个页面是`README.md`，在这个模板里 `README.md`和 `test.md`都是可以任意修改的。

## 测试页面

接下来我们需要搭建简单的 LocalHTTPServer环境来测试我们的页面。下面仅仅讲MacOS 的测试方法。

在文件夹下运行命令行，如果你不知道如何运行命令行，请右键点击`index.html`所在的文件夹，然后在弹出菜单中选择 Service> 然后点击 New Terminal At Folder。

之后在命令行提示符后输入 `python -m SimpleHTTPServer`，回车之后，会看到系统显示

```
% python -m SimpleHTTPServer
Serving HTTP on 0.0.0.0 port 8000 ...
```

这里的8000 是端口号码。打开浏览器，在地址栏中输入 `localhost:8000` 就能看到我们的页面了。然后修改 `README.md` 中的内容，刷新页面，就能看到网站更新。

## 网站发布

完成网站测试后，我们只需要把我们文件夹里的所有内容，上传到我们的github 账户的github Page。

如果你已经有github账户并了解如何新建 repository，请继续往下看，否则，请点击 [https://github.com/signup](https://github.com/signup) 注册一个新账号，并了解github的基础使用方法。

如果您的github用户名叫`username`，那这些文件只需上传到 `username.github.io` 这个 public repository 就完成了我们的网站发布，如果没有这个名字的repository只需新建即可。

上传完成之后，从地址栏输入访问 `username.github.io`就能看到我们的网站了。

如果你使用的是我提供的模板，只需在`index.html`所在文件夹下打开命令行并进行如下操作，但需要注意把`username`替换成你的用户名

```
git init
git add --all
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/username/username.github.io.git
git push -u origin main
```

之后每次更新后，只需要进行如下操作

```
git add --all
git commit -m "commit message"
git push
```

即可将你的网页更新到github page的服务器上。每次更新需要等待10分钟即可从你的网页上看到变化。


## 配置编写博客的IDE

上面的步骤既然都做好了，那么你要怎么写博客？总不能在word里写吧？这里介绍一个非常好用的软件，叫VIM。这是一个所有Mac上都自带的一个工具，也是所有 Unix系统自带的。

我推荐下载[MacVim](https://macvim-dev.github.io/macvim/)

打开MacVim之前，你要确保你熟悉Vim 的一些基本操作,请在网上找教程学习。

在Vim上面的菜单中，可以找到 Edit > StartupSettings，点击后你会打开根目录下的 `.vimrc`文件。在这里可以添加很多系统设置。比如我特别喜欢把VIM设置成半透明的样子，并且设置成大字体。只需要将下面代码加入 `.vimrc`文件中即可
```vimrc
colorscheme torte
set transparency=40
set guifont=Courier_new:h18
```

接下来，在我们写博客的时候，和在我们看博客的时候，区别在于看博客的时候可以随时点击超级链接跳转，但写博客的时候不行。新建一个文件夹和文档都是很累人的事情。因此我们想在写博客的时候也能随时跳转，岂不是很爽？我们用以下的VIM配置来实现编辑器内的链接跳转。

先写一个vim脚本 `enter.vim`

```vim
let line=getline('.')
let linead = '0'.line

let flag = 0 " A flag to indicate if enter successfully

if flag == 0
	try
		let filename=split(split(linead,"](")[1],")")[0]
		let filetitle=split(split(linead,"](")[0],"0[")[0]
		let flag = 1 "a flag indicating successfully find the file to enter
	catch
	endtry
endif
if flag == 1
	let backfilename = repeat('../',len(split(filename,'/'))-1).expand('%p') "this step remembers what the original name
	let temp="e ".expand('%:p:h')."/".filename "expand('%:p:h') represents current folder
	call insert(counter,expand('%:p'),0) "remember the folder address of the current file name
	call insert(position,line('.'),0) "remembering the cursor position of the current file
	execute temp
	execute "silent !mkdir -p %:h"
elseif line('.')==1 && getline('.')==""
	call append(1,"[返回](".backfilename.")")
	call setline(1,"# ".filetitle)
else
	echo "Not able to enter!"
endif
```
这个Vim 脚本的功能是能在光标所在行搜索 markdown格式的链接，然后进入这个链接，同时如果文件夹或文件不存在时还能自动创建文件夹或文件，直接省去了新建文件或新建文件夹的烦恼。同时如果光标在一个空文件首行的时候调用此脚本，还可以创建标题，这个脚本会智能的利用我们进入的信息来制作我们的标题。

我们除了进入命令，我们再来写一个返回上一级的命令`escape.vim`

```vim
if(len(counter)>0)
	let a=expand('%:t')
	execute "e ".counter[0]
	call remove(counter,0)
	execute position[0]
	call remove(position,0)
	call search(a)
endif
```
为了配置好这两个脚本，可以把这两个脚本储存到一个固定的文件夹中，比如我存放的地址是`~/Dropbox/Latex/escape.vim`和`~/Dropbox/Latex/enter`，然后在`.vimrc` 中加入如下命令
```vimrc
:let counter=[]
:let position=[]
:map « :source ~/Dropbox/Latex/escape.vim<CR>
:map \ :source ~/Dropbox/Latex/enter.vim<CR>
```
这里，符号`«`代表的是 `option + \`. 在使用的时候，你只需要写好一个markdown格式的链接`[title](file.md)`, 然后按一下 `\`就能直接跳转进入这个文件，再按一下`\` 就能自动给这个文件加上title这个名字。并且会自动生成返回链接。

有了这些脚本，并结合这两个按键，你就可以在vim里自由的编辑markdown文件树了。 

