# h5-project

web前端开发规范文档
https://mp.weixin.qq.com/s/Rh_LD-XXDmCS-0fub-q1UQ

一、文件规范：
html,css,images文件均归档至<系统开发规范>约定的目录中；
html文件命名：英文命名，后缀.html，同时将对应界面融方于同目录中，若界面稿命名为中文，请重命名与html文件同名，以方便后端添加功能时查找对应的页面
css文件命名：英文命名，后缀.css，共用样式命名为common.css，首页index.css，其他页面依实际模块需求命名
js文件命名：英文命名，后缀.js，共用common.js，其他依照实际模块需求命名

二、html书写规范：
文档类型声明及编码：统一为html5声明类型<!doctype  html>编码统一为utf-8<meta charset="utf-8">书写时利用IDE实现层次分明的缩进
非特殊情况下样式文件必须外链至<head>...</head>之间，非特殊情况下javascript文件必须外链至页面底部
引入样式文件或javascript文件时，须略去默认类型声明，书写如下：
<link rel="stylesheet" href="..." />
<style>...</style>
<script  src="..."></script>
引入js库文件，文件名须包含库名称及版本号及版本号是否为压缩版，比如：jquery-1.2.1.min.js；引入插件，文件名格式为库名称，比如jQuery.cookie.js
所有编码均遵循xhtml标准，标签&属性&属性命名，必须由小写字母及下划线数字组成，且所有标签必须闭合，包含br（<br />）<hr>(</hr>)等，属性值必须用双引号包括
充分利用无兼容性问题的html自身标签，比如span，strong，label等等，需要为html元素添加自定义属性的时候，首先要考虑下有没有默认的已有合适标签去设置如果没有，可以使用须以"data-"为前缀来添加自定义属性，避免使用"data"等其他命名方式
语义化html如标题h1~h6（同一个页面只有一个h1），段落标记用p，列表用ul，内联元素中不可嵌套块级元素
尽可能减少div嵌套，如：<div  class="box"><div class="welcome">欢迎访问xxx，您的用户名是<div class="name">用户名</div></div>完全可以使用如下代码替代<div class="box"><p>欢迎访问xxx，您的用户名是<span>用户名</span></p></div>
书写链接地址时，必须避免重定向，例如href="http://baodu.com/";即须在URL地址后面加上"/"
在页面中尽量避免使用style属性,即：<p style="..."></p>
必须为含有描述性表单元素（input，textarea）添加label如：<div class="form-group"><label for="username">用户名</label><input  type="text" id="username" placeholder="请输入用户名"/></div>
能以背景形式呈现的图片，尽量写入css样式中
重要图片必须加上alt属性；给重要的元素和截断的元素加上title
给区块代码及重要功能（比如循环）加上注释，方便后台添加功能
特殊符号的使用：尽可能使用代码替代：比如<(<)&>(>)空格()
书写页面过程中请考虑向后的扩展性
class&id 参见css书写规范

三、css书写规范：
编码统一为utf-8
协作开发及分工：会根据各个模块，同时根据页面相似程序，事先写好大体框架文件，分配给前端人员实现内部结构表现&行为，共用css文件common.css由i书写协作开发过程中每个页面请务必都要引入，此文件包含reset及头部底部样式，此文件不可随意修改
class与id的使用：id是唯一的并是父级的，class是可以重复的并是子级的，所以id仅使用在大的模块上,class可用在重复使用率高，以及子级中；id原则上都是由分发框架文件时命名的，为javascript预构子的除外；
为javascript预留钩子的命名，请以js_起始，比如：js_hide，js_show
class与id命名：大的框架命名比如header/footer/wrapper/left/right之类的在2中由i统一命名，其他样式名称由小写英文&数字&_来组合命名，如i_comment，fontred,width200；避免使用中文拼音，尽量使用简易的单词组合；总之，命名要语义化，简明化；
规避class与id命名
通过从属写法规避，示例见d
取父级元素id/class命名部分命名，示例见d
重复使用率高的命名，请以自己代号加下划线起始，比如i_clear
eg：要在2中已建好框架的页面代码<div  id="mainnav"></div>中加入新的div元素
按a的命名法则：<div id="mainnav"><div class="firstnav">...</div></div>样式写法：#mainnav  .firstnav{...}
按b命名法则：<div id="mainnav"><div class="main_firstnav">...</div></div> 样式写法：.main_firstnav{...}
css属性书写顺序，建议遵循：布局定位属性-》自身属性-》文本属性-》其他属性。此条可根据自身习惯书写，但尽量保证同类属性写在一起。
属性列举：
布局定位属性主要包括：display&list-style&position（相应的top，right，bottom，left）&float&clear&visibility&overflow
自身属性主要包括：width&height&margin&padding&border&background
文本属性主要包括：color&font&text-decoration&text-align&vertical-align&white-space
其他属性&content
书写代码前，考虑并提高样式重复使用率
充分利用html自身属性及样式继承原理减少代码量比如：
<ul class="list"><li>这是标题列表<span>2016-09-15</span></li></ul>样式：ul.list li{position:relative} ul.list li span{position:absolute;right:0}即可实现日期居右显示
样式表中中文字体名，请务必转码成unicode码，以避免编码错误时乱码
背景图片请尽可能使用sprite技术，减少http请求，考虑到多人协作开发，sprite按模块制作
使用table标签时（尽量避免使用table标签）请不要用width/height/cellpadding/cellspacing等，table属性直接定义表现，应尽可能的利用table自身私有属性分离结构与表现，如
table,tr,td,th,tbody,tfoot,colgroup,scope;
cellspacing及cellpadding的css控制方法：table{border:0;border-collapse:collapse;}table th,table td{padding:0}
base.css文件中我会初始化表格样式

四、图片规范
所有页面元素类图片均放入img文件夹，测试用图片放于img/demoimg文件夹；
图片格式仅限于gif/png/jpg
命名全部用小写英文字母/数字/_的组合，其中不得包含汉字、空格、特殊字符；尽量用易懂的词汇，便于团队其他成员理解，另命名分头尾两部分，用下划线隔开
比如:ad_left01.gif、btn_submit.gif
在保证视觉效果的情况下选择最小的图片格式与图片质量，以减少加载时间
尽量避免使用半透明的png图片（若使用，请参考css规范相关说明）
运用css sprit技术集中小的背景图或图标，减少页面http请求，请务必在对应的sprite psd原图中划参考线，并保存至img目录下

五、注释规范
html注释：注释格式<!--这是注释-->，‘--’只能在注释的始末位置，不可置入注释文字区域
css注释：注释格式/*这是注释*/
javascript注释：单行注释使用//这是单行注释；多行注释使用/*中间是注释内容*/

六、开发及测试工具约定
建议使用Aptana/DW/Vim，也可根据自己喜好选择，但须遵循如下原则
不可利用IDE的视图模式"画"代码
不可利用IDE生成相关功能代码，比如DW内置的一些功能js
编码必须格式化，比如缩进
测试工具：前期开发仅测试FireFox&IE6&IE7&IE8，后期优化时加入Opera&Chrome&Safari
建议测试顺序：FireFox->IE7->IE6->Opera->chrome->safari，建议安装firebug及IE Tab Plus插件

七、其他规范
开发过程中严格按分工完成页面，以提高css复用率，避免重复开发
减少沉冗代码，书写所有人都可以看的懂的代码，简洁易懂是一种美德，为用户着想，为服务器着想


