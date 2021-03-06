https://developers.weixin.qq.com/miniprogram/dev/framework/

# 起步
小程序注册页 https://mp.weixin.qq.com/wxopen/waregister?action=step1
[1]申请AppID https://mp.weixin.qq.com/wxopen/waregister?action=step1
[2]小程序开发
[3]小程序发布 https://mp.weixin.qq.com/wxamp/home/guide?lang=zh_CN&token=125706696

# 页面生命周期
渲染层: 
[1]初始化 
[2]初始化完成发送`通知`给逻辑层
[3]等待`逻辑层数据创建完`返回数据, 即`data及setData数据`
[4]收到`逻辑层数据创建完`返回数据， 进行首次渲染
[5]首次渲染完成， 发送`渲染层准备就绪`通知给逻辑层
[6]收到`数据更新`数据, 重新渲染

逻辑层
[1]创建数据中
[2]页面`onLoad回调`
[3]页面`onShow回调`
[4]`逻辑层数据创建完`发送数据到渲染层
[5]收到`渲染层准备就绪`通知, 出发`onReady回调`
[6]页面隐藏触发`onshow回调`
[7]页面出栈触发`onUnload回调`

# 目录结构
`app.json, app.wxss, app.js `
`page.wxml, page.js, page.wxss, page.json`

# 全局配置 app.json
https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#window


# 小程序技术发展史
当微信中的 [WebView] 逐渐成为移动 [Web] 的一个重要入口时，微信就有相关的 `JS API` 了
2015年初，微信发布了一整套网页开发工具包，称之为 [JS-SDK]
JS-SDK 的模式并没有解决使用移动网页遇到的[体验不良]的问题, 设计了一个 [JS-SDK] 的[增强]版本

# 小程序与普通网页开发的区别
网页开发者可以使用到各种浏览器暴露出来的 `DOM API`，进行 DOM [选中和操作]。小程序的逻辑层和渲染层是分开的，逻辑层运行在 i 中，并没有一个完整浏览器对象，因而缺少相关的`DOM API`和`BOM API`。这一区别导致了前端开发非常熟悉的一些库，例如 `jQuery、 Zepto` 等，在小程序中是无法运行的


# 渲染层和逻辑层
[WXML] 模板和 [WXSS] 样式工作在渲染层，[JS] 脚本工作在逻辑层。渲染层的界面使用了[WebView] 进行渲染；逻辑层采用[JsCore]线程运行JS脚本。这两个线程的通信会经由[微信客户端]（下文中也会采用[Native]来代指微信客户端）做中转，逻辑层[发送网络请求]也经由Native转发

# 程序与页面
[1]微信客户端在打开小程序之前，会把[整个小程序的代码包]下载到本地。 
[3]客户端就会装载这个页面的 [WXML] 结构和 [WXSS] 样式 最后客户端会装载 [js]
[4]Page 页面构造器把 [data] 数据和 [index.wxml] 一起渲染

# 协同工作
https://developers.weixin.qq.com/miniprogram/dev/framework/quickstart/release.html#%E5%8D%8F%E5%90%8C%E5%B7%A5%E4%BD%9C
虚拟项目管理: 产品组, 设计组, 开发组, 测试组
项目管理成员负责统筹整个项目的进展和风险、把控小程序对外发布的节奏，产品组提出`需求`，设计组与产品讨论并对需求进行抽象，设计出可视化流程与图形，输出`设计方案`。开发组依据设计方案，进行程序`代码的编写`，代码编写完成后，产品组与设计组体验小程序的整体流程，测试组编写`测试`用例并对小程序进行各种边界测试。

# 小程序的版本
https://mp.weixin.qq.com/wxamp/wacodepage/getcodepage?token=125706696&lang=zh_CN

# 发布上线
预览-> 上传代码 -> 提交审核 -> 发布


# 运营数据
方式1: 后台查看: https://mp.weixin.qq.com/
方式2: 小程序数据助手


# sitemap 配置
配置其小程序页面是否允许微信索引

# 场景值
https://developers.weixin.qq.com/miniprogram/dev/reference/scene-list.html

# 页面间的通讯
微信小程序页面间通的5种方式
https://www.cnblogs.com/chris-oil/p/10108859.html

所谓通信，要满足下面两个条件：
[1]激活对方的一个方法调用
[2]能够向被激活的方法传递数据

通信分类
按页面层级（或展示路径）可以分为：
兄弟页面间通信。如多Tab页面间通信，PageA，PageB之间通信
父路径页面向子路径页面通信，如PageA向PageC通信
子路径页面向父路径页面通信，如PageC向PageA通信

按通信时激活对方方法时机，又可以分为：
[1]延迟激活，即我在PageC做完操作，等返回到PageA再激活PageA的方法调用
[2]立即激活，即我在PageC做完操作，在PageC激活PageA的方法调用

方式一：`onShow/onHide + localStorage`
优点：实现简单，容易理解
缺点：如果完成通信后，没有即时清除通信数据，可能会出现问题。另外因为依赖localStorage，而localStorage可能出现读写失败，从面造成通信失败
注意点：页面初始化时也会触发onShow

方式二：`onShow/onHide + 小程序globalData`
优点：实现简单，实现理解。因为不读写localStorage，直接操作内存，所以相比方式1，速度更快，更可靠
缺点：同方式1一样，要注意globalData污染

方式三：eventBus(或者叫PubSub)方式
这种方式要先实现一个PubSub，通过订阅发布实现通信。在发布事件时，激活对方方法，同时传入参数，执行事件的订阅方法
缺点：要非常注意重复绑定的问题

方式四：gloabelData watcher方式
前面提到方式中，我们有利用globalData完成通信。现在数据绑定流行，结合redux单一store的思想，如果我们直接watch一个globalData,那么要通信，只需修改这个data值，通过water去激活调用。
同时修改的data值，本身就可以做为参数数据。
优点：数据驱动，单一数据源，便于调试
缺点：重复watch的问题还是存在，要想办法避免

方式五：通过hack方法直接调用通信页面的方法
直接缓存页面PageModel, 通信时，直接找到要通信页面的PageModel,进而可以访问通信页面PageModel所有的属性，方法。简直不能太cool,感谢小组内小伙伴发现这么amazing的方式。
有人肯定会问了，怎么拿到这个所有的PageModel呢。其它很简单，每个页面有onLoad方法，我们在这个事件中，把this（即些页面PageModel）缓存即可，缓存时用页面路径作key，方便查找。那么页面路径怎么获取呢，答案就是page__route__这个属性
[]
优点：一针见血，功能强大，可以向要通信页面做你想做的任何事。无需要绑定，订阅，所以也就不存在重复的情况
缺点：使用了__route__这个hack属性，可能会有一些风险

# WXML
绑定: <Dom attr="{{data}}">{{data}}</Dom>
<Dom wx:for="{{data}}"></Dom>
<Dom wx:if="{{data}}"></Dom>
<Dom wx:elif="{{data}}"></Dom>
<Dom wx:else></Dom>
page(Options)
Options.data 定义
Options.data.data: Object

# 模板
<template name="datas"><Dom>{{data}}</Dom></template>

# WXS
注意项: https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxs/
定义或引入: <wxs module="wxs" src="./test.wxs"></wxs>
绑定: <Dom>{{wxs}}</Dom>

# 事件系统
事件是视图层到逻辑层的通讯方式。
事件可以将用户的行为反馈到逻辑层进行处理。
事件可以绑定在组件上，当达到触发事件，就会执行逻辑层中对应的事件处理函数。
事件对象可以携带额外信息，如 id, dataset, touches
绑定: <Dom bind:even></Dom>
page(Options) 
Options[even]定义
或者
Component(Options)
Options.methods 定义
Options.methods: Object

# 简易双向绑定
绑定:<input model:value="{{data}}"></input>

# 网络
服务器域名配置： `「小程序后台-开发-开发设置-服务器域名」`


# ECMAScript
`语法 类型 语句 关键字 操作符 对象`
小程序中的 JavaScript 是由`ECMAScript 以及小程序框架和小程序 API` 来实现的


# 小程序的执行环境
`iOS平台，包括iOS9、iOS10、iOS11 Android平台 小程序IDE`
这种区别主要是体现三大平台实现的 [ECMAScript] 的标准有所不同


# 模块化
小程序中可以将`任何一个JavaScript 文件`作为一个模块，通过`module.exports` 或者 `exports` 对外暴露接口。


# 脚本的执行顺序
小程序的执行的入口文件是 [app.js] 。并且会根据其中 [require] 的模块顺序决定文件的运行顺序


# 作用域
文件中声明的变量和函数`只在该文件中有效`，`不同的文件`中可以声明相同名字的变量和函数，`不会互相影响`


# 数据驱动
`WXML结构`实际上等价于`一棵Dom树`，通过`一个JS对象`也可以来表达`Dom树`的结构
`WXML`可以先转成`JS对象`，然后再`渲染`出真正的Dom树
通过setData把msg数据从“Hello World”变成“Goodbye”，产生的`JS对象对应的节点`就会发生变化，此时可以对比前后两个JS对象得到变化的部分，然后把这个`差异`应用到原来的Dom树上，从而达到`更新`UI的目的，这就是“数据驱动”的原理


# 双线程下的界面渲染
小程序的逻辑层和渲染层是分开的两个线程。在渲染层，宿主环境会把`WXML转化成对应的JS对象`，在逻辑层发生数据变更的时候，我们需要通过宿主环境提供的setData方法`把数据从逻辑层传递到渲染层`，再经过对比前后`差异`，把差异应用在原来的`Dom树`上，`渲染`出正确的UI界面



# 事件类型和事件对象
`bind`事件绑定不会阻止冒泡事件向上冒泡，`catch`事件绑定可以阻止冒泡事件向上冒泡
evenObjec: {type, timeStamp, target, currentTarge, detail, touches}
type: String
timeStamp: Integer
currentTarget: Object
detail: Object
touches: Arry
target和currentTarget:{id, tagName, dataset}
touch和changedTouches: {identifier, pageX, pageY, clientX, clienY}

# 事件绑定与冒泡捕获
以下示例中，点击 `inner view` 会先后调用`handleTap2、handleTap4、handleTap3、handleTap1`。

代码清单3-20 事件的冒泡和捕获

<view
  id="outer"
  bind:touchstart="handleTap1"
  capture-bind:touchstart="handleTap2"
>
  outer view
  <view
    id="inner"
    bind:touchstart="handleTap3"
    capture-bind:touchstart="handleTap4"
  >
    inner view
  </view>
</view>

# 兼容



# 服务器接口
开发者服务器必须提供[HTTPS]服务的接口
`请求的域名`需要在`小程序管理平台`进行配置


# 请求参数
两种方法把数据传递到服务器：通过`url上的参数`以及通过`data`参数
`get请求中url是有长度限制`的，其最大长度是`1024`字节，同时url上的参数需要拼接到字符串里，参数的值还需要做一次`urlEncode`
传一些比较`复杂的数据`结构到后台的时候，用JSON格式会更加合适 在`wx.request的header`参数设置`content-type头部为application/json`

# 收到回包
wx.request({success: res => {}})
res: {data, status, header}
data: Object | String
statusCode: Number
header: Object
success回调的参数data字段类型是根据header['content-type']决定的，默认header['content-type']是'application/json'

# 一般使用技巧
app.json
networkTimeout: Object
networkTimeout.request: Number 可以指定request的超时时间


# 排查异常的方法
检查手机网络状态以及wifi连接点是否工作正常。
检查小程序是否为开发版或者体验版，因为开发版和体验版的小程序不会校验域名。
检查对应请求的HTTPS证书是否有效，同时TLS的版本必须支持1.2及以上版本，可以在开发者工具的console面板输入showRequestInfo()查看相关信息。
域名不要使用IP地址或者localhost，并且不能带端口号，同时域名需要经过ICP备案。
检查app.json配置的超时时间配置是否太短，超时时间太短会导致还没收到回报就触发fail回调。
检查发出去的请求是否302到其他域名的接口，这种302的情况会被视为请求别的域名接口导致无法发起请求。

# 微信登录
主要对象： `小程序, 微信服务器， 第三方服务器`
[1]通过`wx.login` 到 `微信服务器`获取到微信登录凭证code
[2]通过`wx.request`把`code`带到`自己的服务器`
[3]通过`code和其他信息`与`微信服务器`换取用户ID
[4]绑定微信用户ID和自己业务用户ID
[5]生成自己业务登录凭证SessionID
[6]返回业务登录凭证`SessionID`到`小程序`
[7]下一次wx.request带上SessionID

# 到微信服务器换取微信用户身份id
https://api.weixin.qq.com/sns/jscode2session?appid=<AppId>&secret=<AppSecret>&js_code=<code>&grant_type=authorization_code
return obj
obj: {openid, session_key, uionid}

# 绑定微信用户身份id和业务用户身份
业务侧用户还没绑定微信侧身份时，会让用户填写业务侧的`用户名密码`，这`两个值会和微信登录凭证`一起请求开发者服务器的登录接口，此时开发者后台通过`校验用户名密码`就拿到了`业务侧的用户身份id`，通过code到微信服务器`获取微信侧的用户身份openid`。微信会建议开发者把这两个信息的对应关系存起来，我们把这个对应关系称之为`绑定`。

# 业务登录凭证SessionId
在开发者服务端保持`SessionId对应的用户身份信息`，同时把`SessionId`返回给小程序。小程序后续发起的请求中携带上`SessionId`，开发者服务器就可以通过服务器端的`Session`信息`查询到当前登录用户的身份`

# 缓存限制和隔离
小程序宿主环境会管理`不同小程序`的数据缓存，不同小程序的本地缓存空间是`分开`的，每个小程序的缓存空间上限为`10MB`，如果当前缓存已经达到10MB，再通过wx.setStorage写入缓存会触发`fail`回调。
考虑到同一个设备可以登录不同微信用户，宿主环境还对`不同用户`的缓存进行了隔离，避免用户间的数据隐私泄露

# 缓存用户登录态SessionId
利用`本地缓存`的能力来持久化存储SessionId


# 协同工作


# 人员组织结构和权限分配


# 小程序的版本


# 用户体验审视


# 产品和运营思路


# 体验和设计评估


# 用户体验测试和完善体验


# 发布


# 发布前最后的检查


# 发布模式


# 小程序码


# 运营


# 数据分析


# 运维中心


# 微信开发者社区




# 技术选型
用纯客户端原生技术来渲染
用纯 Web 技术来渲染
介于客户端原生技术与 Web 技术之间的，互相结合各自特点的技术（下面统称 Hybrid 技术）来渲染 例如`JSSDK`


# 管控与安全
我们必须阻止开发者使用一些浏览器提供的，诸如跳转页面、操作DOM、动态执行脚本的开放性接口,  JavaScript 的解释引擎（在iOS下是用内置的 JavaScriptCore框架，在安卓则是用腾讯x5内核提供的JsCore环境）

# 天生的延时
小程序是基于双线程模型，那就意味着任何数据传递都是线程间的通信，也就是都会有一定的延时


# 组件系统
一套组件框架——Exparser

# Exparser框架
Exparser是微信小程序的组件组织框架，内置在小程序基础库中，为小程序的各种组件提供基础的支持

# 内置组件
组件内置到小程序框架里的一个重要原则是：这个组件是基础的。换句话说，没有这个组件的话，在小程序架构里无法实现或者实现不好某类功能

# 自定义组件
组件创建的过程大致有以下几个要点：
[1]根据组件注册信息，从组件原型上创建出组件节点的JS对象，即组件的this；
[2]将组件注册信息中的data 复制一份，作为组件数据，即this.data；
[3]将这份数据结合组件WXML，据此创建出Shadow Tree，由于Shadow Tree中可能引用有其他组件，因而这会递归触发其他组件创建过程；
[4]将ShadowTree拼接到Composed Tree上，并生成一些缓存数据用于优化组件更新性能；
[5]触发组件的created生命周期函数；
[6]如果不是页面根组件，需要根据组件节点上的属性定义，来设置组件的属性值；
[7]当组件实例被展示在页面上时，触发组件的attached 生命周期函数，如果Shadw Tree中有其他组件，也逐个触发它们的生命周期函数
使用triggerEvent触发事件时，可以指定事件的bubbles、composed和capturePhase属性，用于标注事件的冒泡性质


# 原生组件运行机制
原生组件内部创建会经历以下几个步聚：
[1]组件被创建，包括组件属性会依次赋值。
[2]组件被插入到DOM树里，浏览器内核会立即计算布局，此时我们可以读取出组件相对页面的位置（x, y坐标）、宽高。
[3]组件通知客户端，客户端在相同的位置上，根据宽高插入一块原生区域，之后客户端就在这块区域渲染界面
[4]当位置或宽高发生变化时，组件会通知客户端做相应的调整

引入原生组件主要有3个好处：
[1]扩展Web的能力。比如像输入框组件（input, textarea）有更好地控制键盘的能力。
[2]体验更好，同时也减轻WebView的渲染工作。比如像地图组件（map）这类较复杂的组件，其渲染工作不占用WebView线程，而交给更高效的客户端原生处理。
[3]绕过setData、数据通信和重渲染流程，使渲染性能更好。比如像画布组件（canvas）可直接用一套丰富的绘图接口进行绘制

# 原生组件渲染限制
原生组件脱离在WebView渲染流程外，这带来了一些限制. 最主要的限制是一些CSS样式无法应用于原生组件


# 视图层组件
内置组件中有部分组件是利用到客户端原生提供的能力

# 逻辑层接口
逻辑层与客户端原生通信机制与渲染层类似

# 启动


# 代码包下载


# 分包加载流程


# 代码包加载


# 页面层级准备


# 数据通信


# 页面初始数据通信


# 更新数据通信


# 用户事件通信


# 视图层渲染


# 初始渲染


# 重渲染


# 原生组件通信



# 基础库载入时机


# 基础库的版本号


# 异常


# JS运行异常


# 捕捉JS异常的方法


# 基础库的更新


# 基础库版本变动


# 推送基础库过程



# 编译WXML
二进制的WXML编译器, 编译过程将所有的WXML代码最终变成一个JavaScript 函数

# 编译WXSS
内置了一个二进制的WXSS编译器，这个编译器接受WXSS文件列表，分析文件之间的引用关系，同时预处理rpx，输出一个样式信息数组

# 编译JavaScript
在服务器编译过程将每个JS文件的内容分别包裹在define域中，再按一定的顺序合并成 app-service.js 

# 逻辑层模拟
微信开发者工具上我们采用了一个隐藏着的Webivew来模拟小程序的逻辑运行环境

# 渲染层模拟
开发者工具底层搭建的HTTP本地服务器在收到这个请求的时候，就会编译WXML文件和WXSS文件，然后将编译结果作为HTTP请求的返回包。当确定加载页面的路径之后，如index页面，开发工具会动态注入如下一段脚本：

# 客户端模拟
微信客户端为丰富小程序的功能提供了大量的API。在微信开发者工具上，通过借助BOM（浏览器对象模型）以及node.js访问系统资源的能力，同时模拟客户端的UI和交互流程，使得大部分的API能够正常执行。

# 通讯模拟
微信开发者工具的有一个消息中心底层模块维持着一个WebSocket服务器，小程序的逻辑层的WebView和渲染层页面的WebView通过WebSocket与开发者工具底层建立长连，使用WebSocket的protocol字段来区分Socket的来源

# 调试器
开发者工具上显示的调试器是调试逻辑层WebView，主要使用Chrome Devtools的Sources面板调试逻辑层JS代码


小程序配置
全局配置
页面配置
sitemap 配置
场景值
框架接口
小程序 App
App
getApp
页面
Page
getCurrentPages
自定义组件
Component
Behavior
模块化
require
module
exports
requirePlugin
requireMiniProgram
基础功能
wx
wx.env
console
console.debug
console.error
console.group
console.groupEnd
console.info
console.log
console.warn
定时器
setTimeout
clearTimeout
setInterval
clearInterval
WXML 语法参考
数据绑定

# 列表渲染
wx:for="{{data}}"
绑定数据
wx:for-index="index"
指定index标识符
wx:for-item="item"
指定item的标识符

条件渲染
模板
引用
WXS 语法参考
模块
变量
注释
运算符
语句
数据类型
基础类库












# 组件模板
[定义]<Dom><slot></slot>
[使用]<component-tag-name>default slot </component-tag-name>
  注意，在模板中引用到的[自定义组件]及其对应的节点名需要在 [json] 文件中[显式定义]，否则会被当作一个[无意义]的节点。除此以外，节点名也可以被声明为抽象节点。
  
# 模板数据绑定
  与普通的 WXML 模板类似，[可以]使用数据绑定，这样就可以向子组件的属性传递动态数据。
[定义]<component-tag-name prop-a="{{dataFieldA}}" prop-b="{{dataFieldB}}"></component-tag-name>
[多 slot] 时，可以在组件 js 中[声明启用]。
  Component(compenent)
  compenent: Object
  compenent.options: Object
  compenent.options.multipleSlot: Boolean  [启用多slot支持]
[使用] <slot name="after"></slot>
 
 # 组件样式
  组件对应 wxss 文件的样式，[只对组件wxml内的节点生效]。编写组件样式时，需要注意以下几点：
  
  组件和引用组件的页面不能使用id选择器（#a）、属性选择器（[a]）和标签名选择器，请改用class选择器。
  组件和引用组件的页面中使用后代选择器（.a .b）在一些极端情况下会有非预期的表现，如遇，请避免使用。
  子元素选择器（.a>.b）只能用于 view 组件与其子节点之间，用于其他组件可能导致非预期的情况。
  继承样式，如 font 、 color ，会从组件外继承到组件内。
  除继承样式外， app.wxss 中的样式、组件所在页面的的样式对自定义组件无效（除非更改组件样式[隔离选项]）。
  
  # 组件样式隔离
  Component(compenent)
    compenent: Object
    compenent.options: Object
    compenent.options.styleIsolation: String  [启用多slot支持]
  app.wxss 或页面的 wxss 中使用了标签名选择器（或一些其他特殊选择器）来直接指定样式，这些选择器会[影响到页面和全部组件]。通常情况下这是[不推荐]的做法。
  
  styleIsolation 它支持以下取值：
  [isolated, apply-shared, shared, page-isolated, page-apply-shared, page-shared]
  isolated 表示启用样式隔离，在自定义组件内外，使用 class 指定的样式将不会相互影响（一般情况下的默认值）；
  apply-shared 表示页面 wxss 样式将影响到自定义组件，但自定义组件 wxss 中指定的样式不会影响页面；
  shared 表示页面 wxss 样式将影响到自定义组件，自定义组件 wxss 中指定的样式也会影响页面和其他设置了 apply-shared 或 shared 的自定义组件。（这个选项在插件中不可用。）
  使用后两者时，请务必注意组件间样式的相互影响。
  
  如果这个 Component 构造器用于构造页面 ，则默认值为 shared ，且还有以下几个额外的样式隔离选项可用：
  
  page-isolated 表示在这个页面禁用 app.wxss ，同时，页面的 wxss 不会影响到其他自定义组件；
  page-apply-shared 表示在这个页面禁用 app.wxss ，同时，页面 wxss 样式不会影响到其他自定义组件，但设为 shared 的自定义组件会影响到页面；
  page-shared 表示在这个页面禁用 app.wxss ，同时，页面 wxss 样式会影响到其他设为 apply-shared 或 shared 的自定义组件，也会受到设为 shared 的自定义组件的影响。
  
  {
    "styleIsolation": "isolated"
  }
  
  代码示例：
  
  在开发者工具中预览效果
  
  /* 组件 custom-component.js */
  Component({
    options: {
      addGlobalClass: true,
    }
  })
  <!-- 组件 custom-component.wxml -->
  <text class="red-text">这段文本的颜色由 `app.wxss` 和页面 `wxss` 中的样式定义来决定</text>
  /* app.wxss */
  .red-text {
    color: red;
  }
  外部样式类
  基础库 1.9.90 开始支持，低版本需做兼容处理。
  
  有时，组件希望接受外部传入的样式类。此时可以在 Component 中用 externalClasses 定义段定义若干个外部样式类。
  
  这个特性可以用于实现类似于 view 组件的 hover-class 属性：页面可以提供一个样式类，赋予 view 的 hover-class ，这个样式类本身写在页面中而非 view 组件的实现中。
  
  注意：在同一个节点上使用普通样式类和外部样式类时，两个类的优先级是未定义的，因此最好避免这种情况。
  
  代码示例：
  
  /* 组件 custom-component.js */
  Component({
    externalClasses: ['my-class']
  })
  <!-- 组件 custom-component.wxml -->
  <custom-component class="my-class">这段文本的颜色由组件外的 class 决定</custom-component>
  
  代码示例：
  
  在开发者工具中预览效果
  
  <!-- 页面的 WXML -->
  <custom-component my-class="red-text" />
  <custom-component my-class="large-text" />
  <custom-component my-class="red-text large-text" />
  .red-text {
    color: red;
  }
  .large-text {
    font-size: 1.5em;
  }
  引用页面或父组件的样式
  
  即使启用了样式隔离 isolated ，组件仍然可以在局部引用组件所在页面的样式或父组件的样式。
  
  例如，如果在页面 wxss 中定义了：
  
  .blue-text {
    color: blue;
  }
  在这个组件中可以使用 ~ 来引用这个类的样式：
  
  <view class="~blue-text"> 这段文本是蓝色的 </view>
  如果在一个组件的父组件 wxss 中定义了：
  
  .red-text {
    color: red;
  }
  在这个组件中可以使用 ^ 来引用这个类的样式：
  
  <view class="^red-text"> 这段文本是红色的 </view>
  也可以连续使用多个 ^ 来引用祖先组件中的样式。
  
  注意：如果组件是比较独立、通用的组件，请优先使用外部样式类的方式，而非直接引用父组件或页面的样式。
  
  虚拟化组件节点
  
  默认情况下，自定义组件本身的那个节点是一个“普通”的节点，使用时可以在这个节点上设置 class style 、动画、 flex 布局等，就如同普通的 view 组件节点一样。
  
  <!-- 页面的 WXML -->
  <view style="display: flex">
    <!-- 默认情况下，这是一个普通的节点 -->
    <custom-component style="color: blue; flex: 1">蓝色、满宽的</custom-component>
  </view>
  但有些时候，自定义组件并不希望这个节点本身可以设置样式、响应 flex 布局等，而是希望自定义组件内部的第一层节点能够响应 flex 布局或者样式由自定义组件本身完全决定。
  
  这种情况下，可以将这个自定义组件设置为“虚拟的”：
  
  Component({
    options: {
      virtualHost: true
    },
    properties: {
      style: { // 定义 style 属性可以拿到 style 属性上设置的值
        type: String,
      }
    },
    externalClasses: ['class'], // 可以将 class 设为 externalClasses
  })
  这样，可以将 flex 放入自定义组件内：
  
  <!-- 页面的 WXML -->
  <view style="display: flex">
    <!-- 如果设置了 virtualHost ，节点上的样式将失效 -->
    <custom-component style="color: blue">不是蓝色的</custom-component>
  </view>
  <!-- custom-component.wxml -->
  <view style="flex: 1">
    满宽的
    <slot></slot>
  </view>
  需要注意的是，自定义组件节点上的 class style 和动画将不再生效，但仍可以：
  
  将 style 定义成 properties 属性来获取 style 上设置的值；
  将 class 定义成 externalClasses 外部样式类使得自定义组件 wxml 可以使用 class 值。


# npm 支持
 [1] 在小程序 [package.json] 所在的目录中执行命令 [npm install] 安装 npm 包：
 构建 npm 
 [3]勾选“使用 npm 模块”选项：
 [4]require()
 可使用 npm 包
 [5]使用 npm 包中的自定义组件
 
 # 默认的构建 npm 方式
 [构建 npm 前]
 ├── miniprogram
 │   ├── app.js
 │   ├── app.json
 │   ├── app.wxss
 │   ├── index
 │   │   ├── 略
 │   ├── node_modules // 可被默认方式构建 npm，因为它在 miniprogramRoot 内
 │   ├── package.json
 │   └── sub_package
 │       ├── node_modules // 可被默认方式构建 npm，因为它在 miniprogramRoot 内
 │       ├── package.json
 │       └── sub_package_page
 ├── node_modules // 不被默认方式构建 npm，因为它不在 miniprogramRoot 内
 ├── package.json
 └── project.config.json // 其中存在配置 `"miniprogramRoot": "./miniprogram"`
 
 [构建 npm 后]
 ├── miniprogram
 │   ├── app.js
 │   ├── app.json
 │   ├── app.wxss
 │   ├── index
 │   │   ├── 略
 │   ├── miniprogram_npm
 │   ├── node_modules // 可被默认方式构建 npm，因为它在 miniprogramRoot 内 --> 同级的 miniprogram_npm 是这份 node_modules 的构建结果
 │   ├── package.json
 │   └── sub_package
 │       ├── miniprogram_npm 
 │       ├── node_modules // 可被默认方式构建 npm，因为它在 miniprogramRoot 内 --> 同级的 miniprogram_npm 是这份 node_modules 的构建结果
 │       ├── package.json
 │       └── sub_package_page
 ├── node_modules // 不被默认方式构建 npm，因为它不在 miniprogramRoot 内 --> 它并没有对应的 miniprogram_npm 生成
 ├── package.json
 └── project.config.json // 其中存在配置 `"miniprogramRoot": "./miniprogram"`
 
 #自定义 node_modules 和 miniprogram_npm 位置的构建 npm 方式
 与 “默认的构建 npm 方式” 不一样，此种方式需要开发者在 project.config.json 中指定 node_modules 的位置 和目标 miniprogram_npm 的位置。参考demo
 
 [使用方法]
 配置 project.config.json 的 [setting.packNpmManually] 为 [true]，开启自定义 node_modules 和 miniprogram_npm 位置的构建 npm 方式
 配置 project.config.json 的 [setting.packNpmRelationList] 项，指定 packageJsonPath 和 miniprogramNpmDistDir 的位置
 其中 [packNpmRelationList] 的格式为
 
 packageNpmRelationList: Array<{
   "packageJsonPath": string,
   "miniprogramNpmDistDir": string
 }>
[packageJsonPath] 表示 node_modules 源对应的 package.json
[miniprogramNpmDistDir] 表示 node_modules 的构建结果目标位置
 构建 npm 前
 .
 ├── miniprogram
 │   ├── app.js
 │   ├── app.json
 │   ├── app.wxss
 │   ├── index
 │   ├── sitemap.json
 │   └── sub_package
 │       └── sub_package_page
 ├── project.config.json
 ├── src_node_modules_1
 │   ├── node_modules
 │   └── package.json
 └── src_node_modules_2
     ├── node_modules
     └── package.json
 其中 project.config.json 存在配置
 
 "setting": {
   "packNpmManually": true,
   "packNpmRelationList": [
     {
       "packageJsonPath": "./src_node_modules_1/package.json",
       "miniprogramNpmDistDir": "./miniprogram/"
     },
     {
       "packageJsonPath": "./src_node_modules_2/package.json",
       "miniprogramNpmDistDir": "./miniprogram/sub_package"
     }
   ]
 }
 构建 npm 后
 .
 ├── miniprogram
 │   ├── app.js
 │   ├── app.json
 │   ├── app.wxss
 │   ├── index
 │   ├── miniprogram_npm // 由 src_node_modules_1/node_modules 构建得到
 │   ├── sitemap.json
 │   └── sub_package
 │       ├── miniprogram_npm // 由 src_node_modules_2/node_modules 构建得到
 │       └── sub_package_page
 ├── project.config.json
 ├── src_node_modules_1
 │   ├── node_modules
 │   └── package.json
 └── src_node_modules_2
     ├── node_modules
     └── package.json
 
 
 # api
 App(Object object)
 Object:{[onLaunch[, onshow[, onHide[, onError[, onPageNotFound[, PageNotFound[, onThemeChange[, 其他]]]]]]]])
 onLaunch: (Object) => {}
 生命周期回调——监听小程序初始化。 参数[Object]也可以使用 [wx.getLaunchOptionsSync] 获取
 onShow: (Object) => {}
 生命周期回调——监听小程序启动或切前台。 也可通过[wx.onAppShow]绑定监听
 onHide: () => {}
 生命周期回调——监听小程序切后台。	也可通过[wx.onAppHide]绑定监听
 onError: (String) => {}
 错误监听函数。	也可通过[wx.onError]绑定监听
 onPageNotFound: (Object) => {}
 页面不存在监听函数。	1.9.90 也可通过[wx.onPageNotFound]绑定监听
 onUnhandledRejection: (Object) => {}
 onThemeChange: () => {}
 其他:	any
 开发者可以添加任意的函数或数据变量到 Object 参数中，用 this 可以访问

getApp()
 获取到小程序全局唯一的 [App 实例]
 
 Page(page)
  模块提供了[控制小程序页面]的方法
 page:{path, query, $}
 
 page.path: string
 [页面路径]。
 page.query: Object
 [页面参数]。
 page.$(selector: string): Promise<Element>
 获取[页面元素]。 page.$$(selector: string): Promise<Element[]>
 page.waitFor(condition: string | number | Function): Promise<void>
 等待[直到指定条件成立]。
 page.data(path?: string): Promise<Object>
 page.setData
 [设置]页面渲染数据。
 page.size(): Promise<Object>
 获取[页面大小]。
 page.scrollTop(): Promise<number>
 获取页面[滚动位置]。
 page.callMethod(method: string, ...args: any[]): Promise<any>
 调用[页面指定方法]。
 
  