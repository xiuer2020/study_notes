
# 1.排除不用的文件夹
打开everything，点击菜单上的工具→选项，也可以直接按快捷键Ctrl+P，弹出的界面，左侧单击排除列表，右侧勾选排除隐藏文件和目录、排除系统文件和目录；还要继续添加一些不会去搜索的文件夹，点击添加文件夹，把我们安装软件的目录，微信的缓存之类的目录也添加进去， 添加好了以后单击确定，结束添加。



# 2.美观优化
1)首先在打开选项，在结果里勾选双击路径打开目录
2)在视图里，勾选交错行颜色和高亮光标经过行；
3)在字体与颜色里，设置喜欢的字体和字号在下方项目状态里，选择鼠标悬停选项，将背景色改为你喜欢的颜色，我设置的是R:147 G: 226 B: 197；
4)选择未选中的交错行，将背景色改为你喜欢的颜色，我设置的是R:231 G: 237 B: 236


# 3.基本使用与语法
1)可以在标题栏上单击鼠标右键，弹出的菜单选择合适的属性来显示，也可以关闭不需要的属性。
#2)指定目录搜索：如只搜索d盘下的文件，可以在搜索框中输入d:后面加一个空格，再输入要搜索的文件名，就能只在d盘内搜索了；
3)多目录内搜索：如果在两个以上目录搜索，在目录中间加上|符号 如d:|e: 学，在Ｄ、Ｅ盘内搜索带学字的文件；
4)不搜索指定目录，目录前加英文！号即可，如下图所示
5)指定日期内的文件：文件名后加dm指定，如2020年4到5月，可以这样表示dm:2020/4-2020/5，
6)特定类型的文件
audio: 搜索音频文件、 zip: 搜索压缩文件、doc: 搜索文档文件、exe: 搜索可执行文件、 pic: 搜索图片文件、video: 搜索视频文件；
如找到电脑中包含的视频文件只需输入video:
7)已知后缀名的搜索可以用 *.后缀名来搜索
8)指定文件的大小来搜索：在要搜索的文件名后，加一个空格，然后输入size:文件大小
9)通过文档内容来搜索文档：通过文档内容来搜索文档用content:文档内容，这种搜索一定要限定一个小一点的范围不然搜索的很慢很慢。
10)搜索重名文件用dupe: 后面跟文件名即可
其他语法：everything里面还有很多其他有用的语法，大家可以查看帮助下的搜索语法，我就不一一演示了。


# 4.搜索局域网内的共享文件与筛选器
要想搜索局域网共享文件时，先要对局域网文件进行索引，有两种办法，第一种，先点击工具菜单下的文件列表编辑器；
打开文件列表编辑器后，打开局域网，把要搜索的共享文件夹拖放进去
然后Ctrl+s，将文件列表保存起来，记好路径；
然后打开everything选项，找到文件列表，将刚保存的文件列表添加进去，然后点击确定；
这是我们在主界面里输入\\ 两个英文反斜杠，就能看到刚添加的共享文件了，在后面加个空格，输入要搜索的文件名，就可以在共享文件里搜索要查找的文件了。
除了用文件列表编辑器添加共享文件外，还可在选项→文件夹里直接添加网络共享文件夹；
筛选器的用法
上面设置了搜索共享文件，这个时候，如果不想搜索共享文件，只想搜索本地的文件，就需要输入!\\ 来排除共享文件夹，但每次都这么输入有点麻烦，可以使用筛选器，首先我们先在输入框中输入!\\ ，然后点击菜单上的搜索→添加到筛选；
在弹出的窗口里，将名称改为本地文件，并设置一个快捷键，那么你下次需要搜索本地时，只需要按下快捷键，或者在搜索菜单里点击本地文件即可；
你也可以用同样的方法为网络共享或者你常用的文件设置一个筛选器，来方便搜索；注意使用一个筛选器后，下次搜索会默认保留这个筛选器，使用完之后，最好将筛选器改为所有。


其它
everything还可以实现Http共享，可以让你不在电脑前，就能搜索到自己电脑上的东西，不过有一定风险，有兴趣的朋友可以自行搜索一下。
