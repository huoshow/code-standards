code-standards
==============

编码规范

文件相关规范
1、文件名必须由小写字母、数字、中划线-组成
2、文件必须用utf-8编码
3、文件引入可通过外联或内联方式引入：
3.1 外联方式：<link rel=”stylesheet” href=”…” />（类型声明type=”text/css”可以忽略）
3.2 内联方式：<style>…</style> （类型声明type=”text/css”可以忽略）
4、原则上，不允许在html上直接写样式
5、link和style标签都应该放入head中
注释规范
1、文件顶部注释（推荐使用） 1
2
3
4
5  /*
 * @description: xxxxx中文说明
 * @author: zhifu.wang
 * @update: zhifu.wang (2012-10-17 18:32)
 */

2、模块注释（推荐使用） 1
2
3	/* module: module1 by zhifu.wang */
 …
/* module: module2 by zhifu.wang */


模块注释必须单独写在一行
3、简单注释 
3.1 单行注释 1	/* this is a short comment */


单行注释可以写在单独一行，也可以写在行尾
3.2 多行注释 1
2
3
4	/*
  * this is comment line 1.
  * this is comment line 2.
  */


多行注释必须写在单独行内
4、特殊注释（推荐使用） 1
2	/* TODO: xxxx by zhifu.wang 2012-10-18 18:32 */
/* BUGFIX: xxxx by zhifu.wang 2012-10-18 18:32 */


用于标注修改、待办等信息
5、长度要求：注释中的每一行长度不超过40个汉字，或者80个英文字符
排版规范
1、一个tab设置为四个空格宽度。
2、规则可以写成单行，或者多行，但是整个文件内的规则排版必须统一。如果是在html中写内联的css，则必须写成单行。
3、单行形式书写风格的排版约束
3.1 每一条规则的大括号 { 前后加空格
3.2 多个selector共用一个样式集，则多个selector必须写成多行形式
3.3 每一条规则结束的大括号 } 前加空格
3.4 属性名冒号之前不加空格，冒号之后加空格
3.5 每一个属性值后必须添加分号; 并且分号后空格
例如： 1
2
3	div.test { width: 100px; height: 200px; }
 a:focus, 
 a:hover { position: relative; right: 1px; }

4、多行形式书写风格的排版约束
4.1 每一条规则的大括号 { 前添加空格
4.2 多个selector共用一个样式集，则多个selector必须写成多行形式
4.3 每一条规则结束的大括号 } 必须与规则选择器的第一个字符对齐
4.4 属性名冒号之前不加空格，冒号之后加空格
4.5 属性值之后添加分号;
5、其他规范
5.1 使用单引号，不允许使用双引号
5.2 如果使用CSS3的属性，如果有必要加入浏览器前缀，则按照1	-webkit- / -moz- / -ms- / -o- / std

的顺序进行添加，标准属性写在最后，并且属性名称要对齐，例如： 1
2
3
4
5
6	div.animation-demo {
     -webkit-animation: mymove 5s infinite; 
        -moz-animation: mymove 5s infinite; 
          -o-animation: mymove 5s infinite; 
             animation: mymove 5s infinite;
}

规则书写规范

除16进制颜色和字体设置外，CSS文件中的所有的代码都应该小写。
规则书写规范
 1、规则命名中，一律采用小写加中划线的方式，不允许使用大写字母或 _
 2、命名避免使用中文拼音，应该采用更简明有语义的英文单词进行组合
 3、命名注意缩写，但是不能盲目缩写，具体请参见常用的CSS命名规则
 4、不允许通过1、2、3等序号进行命名
 5、避免class与id重名
 6、id用于标识模块或页面的某一个父容器区域，名称必须唯一，不要随意新建id
 7、class用于标识某一个类型的对象，命名必须言简意赅。
 8、尽可能提高代码模块的复用，样式尽量用组合的方式
 9、规则名称中不应该包含颜色（red/blue）、定位（left/right）等与具体显示效果相关的信息。应该用意义命名，而不是样式显示结果命名。例如： 1
2	.red { color: red }（错误）
.important-news { color : red }（正确）

 10、除了重置浏览器默认样式外，禁止直接为html tag添加css样式设置，例如： 1
2
3
4	div {
     width: 200px;
     font-size: 16px;
}

 11、每一条规则应该确保选择器唯一，禁止直接为全局.nav/.header/.body等类设置属性
属性编写顺序

推荐的样式编写顺序
1、显示属性 1	display/list-style/position/float/clear

2、自身属性（盒模型） 1	width/height/margin/padding/border

3、背景 1	background

4、行高 1	line-height

5、文本属性 1
2	color/font/text-decoration/text-align/
text-indent/vertical-align/white-space/content

6、其他 1	cursor/z-index/zoom

7、CSS3属性 1	transform/transition/animation/box-shadow/border-radius

8、链接的样式请严格按照如下顺序添加： 1	a:link -> a:visited -> a:hover -> a:active（LoVeHAte）

性能优化
1、合并margin、padding、border的-left/-top/-right/-bottom的设置，尽量使用短名称。
2、选择器应该在满足功能的基础上尽量简短，减少选择器嵌套，查询消耗。但是一定要避免覆盖全局样式设置。
3、注意选择器的性能，不要使用低性能的选择器，例如： 1
2
3	div > * {}
 ul > li > a {}
 body.profile ul.tabs.nav li a {}

4、禁止在css中使用*选择符
5、除非必须，否则，一般有class或id的，不需要再写上元素对应的tag，例如： 1	div#test { width: 100px; }

6、0后面不需要单位，比如0px可以省略成0，0.8px可以省略成.8px
7、如果是16进制表示颜色，则颜色取值应该大写。
8、如果可以，颜色尽量用三位字符表示，例如#AABBCC写成#ABC
9、如果没有边框时，不要写成border:0，应该写成border:none
10、尽量避免使用AlphaImageLoader
11、在保持代码解耦的前提下，尽量合并重复的样式，例如： 1
2
3
4
5	h1 { color: black; }
 p { color: black; }
 -->
 h1, 
 p { color: black; }

12、background、font等可以缩写的属性，尽量使用缩写形式 1
2	background: color image repeat attachment position;
font: style weight size/lineHeight family;

CSS属性取值规范
字体大小font-size

font-size目前人人CSS取值的几种类型如下：1	12px/9pt/1.2em/150%/1.7


现将font-size取值的单位类型约束如下：
1、font-size必须以px或pt为单位，推荐用px（注：pt为打印版字体大小设置）
2、不允许使用xx-small/x-small/small/medium/large/x-large/xx-large等值
字体系列font-family

目前font-family取值类型丰富多样，比如home-frame2-all-min.css中：body	Tahoma, Verdana, STHeiTi, simsun, sans-serif
.fselect-pager li a	Arial
a.mini-share	mingliu
.small	tahoma, mingliu
select, label, textarea, input	“lucida grande”, tahoma, verdana, arial, STHeiTi, simsun, sans-serif
.m-autosug small	MingLiU
#appsMenuPro .menu-apps-side a.add-app-btn	宋体
.site-footer .haoes	tahoma, mingliu


为了对font-family取值进行统一，更好的支持各个操作系统上各个浏览器的兼容性，现将font-family统一约束如下：
1、font-family不允许在业务代码中随意设置
2、font-family目前取值为1
2
3
4
5
6
7
8
9
10
11
12
13
14	body {
     font: 12px Tahoma, Verdana, STHeiTi, simsun, sans-serif;
}

 input,
 label,
 select,
 option,
 textarea,
 button,
 fieldset,
 legend {
     font-family: "lucida grande", tahoma, verdana, arial, STHeiTi, simsun, sans-serif;
}

hack使用规范

重要原则：尽量少用hack，能不hack坚决不hack，不允许滥用hack。

如果需要使用hack，请参考以下hack方式：
区分规则IE6	* html selector { … }
IE7	*+html selector { … }
非IE6	html>body selector { … }
firefox	@-moz-document url-prefix() { … }
safari3+/chrome	@media screen and (-webkit-min-device-pixel-ratio:0) { … }
opera	@media all and (-webkit-min-device-pixel-ratio:10000), not all and (-webkit-min-device-pixel-ratio:0) { … }
iPhone/mobile webkit	@media screen and (max-device-width: 480px) { … }

区分属性IE6	_property: value
IE7	+property: value
IE6/7	*property: value
IE6/7/8/9	property: value\9

z-index取值规范

目前人人页面中的弹层较多，z-index取值也比较随意，导致相互覆盖的情况，有的弹层直接覆盖了顶部导航条。

以下是首页的一些z-index取值比较大的属性设置统计：header头部导航条	1999
账号菜单	10001
通知提醒	10000
顶部搜索结果弹窗	10001
页面内容顶部/publisher	1998
publisher电影搜索提示	1000
用户等级与登录信息提醒	1999
回到顶部按钮	999 in css, 1001 in html
@	10001
表情	10001
名片卡	9999
底部工具条与webpager/radio	1000 in css, 1999 in html
照片浏览弹层	5000
照片多张上传弹层	3001
XN默认弹层组件	10000
首页应用中心推荐弹层	1002
HTML5拖拽上传	999998


其他z-index设置：.dropmenu-holder 	999999
.appsMenuPro	10001
.search-Result	10002 !important
.menu-dropdown	200
.site-nav .navigation	981
.mentionFrdList	10002!important
.app-center-popup	1002
.feed-back-v6	1999
#appcardcontent	1998
.feed-comment-attach	1000
.message-box	1000
#friendcreate-box	100


这些z-index设置，极有可能造成相互覆盖，存在潜在的问题风险。例如：
1、publisher在导航条以下，但是在publisher中弹出的@、表情却在导航条以上。
 
2、XN的默认弹层样式穿透导航条
 
3、@组件与名片卡组件相互重叠
 

因此，有必要对z-index取值进行规范和约束。避免前端开发人员为了自己开发的功能能够正确展示，而忽略了其他组件的展示需求。 

如果要为弹层设置z-index，请务必按照给定的取值区间来进行设置。

这里只是初稿，可能还需要精确到某一个组件的z-index分配，需要大家集思广益（可以参考cookie的设置流程，在使用z-index时必须经过审批）头部导航区域	[1999 - 2100]
publisher所在的内容head区	[1998]
页面主要内容区域	[-1 - 1997]
页面底部	[1999 - 2100]
首页应用弹层	[1000]
全站公共组件	[-1 - 1999]
全页面蒙层弹窗组件	[10000-11000]

常用的 CSS 命名头	header	内容	content	尾	footer	导航	nav
子导航	subnav	栏目	column	主体	main	新闻	news
版权	copyright	文章列表	list	加入	joinus	合作伙伴	partner
标志	logo	侧栏	sidebar	横幅	banner	状态	status
菜单	menu	子菜单	submenu	滚动	scroll	搜索	search
标签页	tab	提示信息	msg	小技巧	tips	标题	title
指南	guild	服务	service	热点	hot	下载	download
注册	regsiter	登录条	loginbar	按钮	btn	投票	vote
注释	note	友情链接	friend-link	外套	wrap	面包屑	bread-crumb
当前的	current	购物车	shop	图标	icon	文本	txt
待补充… 							

其他
1、字体名称请映射成对应的英文名，例如：黑体(SimHei) 宋体(SimSun) 微软雅黑 (Microsoft Yahei)，如果字体名称中有空格，则必须加单引号。
2、背景图片请合理使用csssprites，按照模块、业务、页面来划分均可
3、css背景图片的文件类型，请按照以下原则来保存： 
3.1 如果背景图片有动画，则保存成gif
3.2 如果没有动画，也没有半透明效果，则保存成png-8
3.3 如果有半透明效果，则保存成png-24
4、不要在html中加入标签来清理浮动，通过在浮动元素的父元素上添加.clearfix来清除浮动
5、为了SEO和页面可用性，请使用text-indent来隐藏文本内容。
6、制作csssprites时，尽量把颜色相近的图标放在一起，存储为png8格式，存储完以后还能用一些压缩工具进行无损压缩。
7、避免过小的背景图片平铺。
8、尽量少用!important
9、避免使用非一次性expression
参考资料

 浏览器CSS3特效支持规范
http://www.w3schools.com/cssref/css3_browsersupport.asp 

Google CSS guidelines
http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml#CSS_Style_Rules

Mozilla官方推荐CSS书写顺序
http://www.mozilla.org/css/base/content.css

bootstrap.css
http://twitter.github.com/bootstrap/assets/css/bootstrap.css

浏览器兼容性问题汇总
http://wiki.d.xiaonei.com/pages/viewpage.action?pageId=16090142

CSS hack区分Firefox、Opera、Safari、IE
http://leeiio.me/css-hack-for-firefox-opera-safari-ie/

说说CSS Hack 和向后兼容
http://sofish.de/1331

常用的css命名
http://www.03964.com/read/bbfd0a70fc1602583e1038d7.html