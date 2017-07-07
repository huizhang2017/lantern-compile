# lantern-compile
蓝灯,Mac版编译

## Homebrew
*Homebrew*,macOS 缺失的软件包管理器,没用过的可以过去了解一下[Homebrew](https://brew.sh/index_zh-cn.html)
lantern之前先安装一下*Homebrew*,终端输入
~~~
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
~~~
*Homebrew*安装完成以后,安装git,已安装的可以忽略
~~~
$ brew install git
~~~

## Node安装
* Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境
* Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型,使其轻量又高效
* Node.js 的包管理器 npm,是全球最大的开源库生态系统
[Node下载](http://nodejs.cn/download/),选择Mac版下载,安装下一步下一步就行....

## 其他预安装
~~~
$ brew install go
$ npm i gulp-cli -g
$ npm install -g appdmg
$ npm install -g svgexport
~~~

## lantern Mac编译
找个文件夹把lantern下载下来
可以直接用GitHub下载,cd到你放置lantern的文件夹,终端输入命令如下
~~~
$ git clone --depth=1 https://github.com/getlantern/lantern.git
~~~
下载以后
~~~
$ cd lantern
$ export VERSION=9.9.9
$ make darwin
~~~
编译的时候回出现以下错误
![编译是错误图片](http://ogpq2zwg5.bkt.clouddn.com/WechatIMG7.jpeg)
根据错误信息指出的路径在lantern文件夹中找到对应的文件及行数
1 只需要把*MaxIdleTime*改为*IdleConnTimeout"
2 然后把下面紧接的调用*EnforceMaxIdleTime()*这个方法的语句注释掉

就改这两个文件中的4行就行,重新编译
~~~
$ make darwin
~~~
编译完成后,你会在你的lantern文件夹中找到名为*lantern_darwin_amd64*的文件,说明完全没问题了

### 运行
然后在你的Mac上搜索一下*lantern_darwin_amd64*,双击打开就可以了