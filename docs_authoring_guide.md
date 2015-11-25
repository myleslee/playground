
# LeanCloud 文档样式指南（增补版）

## Cheat Sheet

- `<span style="white-space: nowrap;">`
- 中文不要用斜体（三个 *），表示强调用 **粗体** 和 <span style="text-decoration:'underline';">下划线</u>。
- 软回车使用 `<br>`，不要用**两个空格**代替。<br/>
  由于编辑器的个人设置不同，如 Sublime Text（`"trim_trailing_white_space_on_save": true`）会在保存时将空白移除，这样会造成版式混乱。
- 列表：标题**加粗**，后接 `：` （全角冒号），与后面的文字隔开；如想单独成行，将冒号改为 `<br/>`。
- 标题
  - 各级标题的 # 与文字之间加一个空格，与下面的正文内容隔一个空行。
- 层级菜单使用 `>` 分隔，不要用 `--`、`->` 或其他字符。
  - 说明文字使用 CSS class `note` 来标注：<br/>
    ` **控制台** ><span class="note">（选择一个应用）</span>>**存储** > **云引擎**<span class="note">（屏幕左侧）</span>`
  - **控制台** ><span class="note" style="color:#999;">（选择一个应用）</span>> **存储** > **云引擎**<span class="note">（屏幕左侧）</span><br/>
  - **控制台** /<span class="note" style="color:#999;">（选择一个应用）</span>/ **存储** / **云引擎**<span class="note">（屏幕左侧）</span>
- 屏幕文字或菜单使用粗体字，不要当成代码来标注：进入 `控制台` -- `存储` -- `云引擎`。
- 图片放在 **/images** 下，不要上传到七牛，一来便于维护，二来我们不用付费。
- 文件夹/目录、文件名不用 `代码块` 来表示，必要时可以加粗。
- 虽然有「千言万语不及一幅画」的说法，但如果图片可以用简短的文字描述清楚，尽量用文字，好处：
  - 对搜索引擎友好
  - 屏幕内容可能发生变化，但无法以文字方式搜索到或替换，难以及时更新
  - 文字加载比图片快
  - 节省流量和存储字节
- 对勾 &check;（`&check;`），`- [x]` 可表示为【&check;】 
- 外部链接：
  - 本站点链接：文档标题 + 中间点 + 锚点描述<br/>
    [iOS 推送指南 &middot; 清除 badge](ios_push_guide.html#清除_Badge)
  - 外部站点：`<div class="reference"></div>`
- 代码块使用 \``` 或 \`` 来组织，不要使用 tab 或 空格。
- AVObject 不要标为代码。

## Markdown 增强
- 加一些 html 属性，如 class、column width
- TABLE
  - 无法区分 thead，样式不明显
  - 无法使用 nowrap，文字挤在一起或错行，很不美观   
  - 必须要表头
  - 无开口 table 样式
  - 单元格内不能内嵌列表，只能用
- 不支持 attributes（如 class/style）等
- 不支持 `- [X]` 列表

Class 中的 function：方法/method
之外的为 function：函数
hook 
block



1. ```[应用控制台](/applist.html#/apps)```
2. 表格
  ```
  参数|类型|约束|说明
  ---|---|---|---

  参数|类型|约束|默认|说明
  ---|---|---|---|---
  &nbsp;&nbsp;&nbsp;&nbsp; a||||
  ```
 
## 格式

### 链接

链接文字与链接相同，使用 `<link>` ，而非 `[link](link)` 这种繁琐的语法。邮件地址也使用 `<email_address>`

- 内部链接：章节引用[查询 &middot; 条件查询 &middot; 约束](#约束)，或者 [查询 / 条件查询 / 约束](#约束)
- 不建议使用「请参考 [这里](./a.html)」、请参考 [这篇文章](./a.html)」这样泛泛的表达方式。缺点：
  - 如果链接失效，读者对引用的内容毫无头绪。如果加上具体内容，如文章题目，即使链接失效，读者可依据这一线索到搜索引擎里搜索。
- 外部链接
- 《文章》


#### 链接深度用法
<https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links>

#### 锚点链接

只支持字母[Aa-Zz]、数字[0-9]、下划线 `_` 和中划线 `-`。

比如 `### 对话（Conversation）` 会生成如下 HTML 代码：

```
<h3 id="对话_Conversation_"><a href="#对话_Conversation_">对话（Conversation）</a></h3>
```

H1-H6 标题文字| href 值
:---|:---
Node.js 概述|`#Node_js_概述`
LeanCloud 简介|`#LeanCloud_简介`
如何开发票？|`#如何开发票_`
重要概念<br/>重要概念|`#重要概念`<br/>`#重要概念-1`
全角标点及符号：·！……（）【】「」『』、《》，。？、|`#全角标点及符号____________________`
半角标点及符号:&grave;~!@#$%^&*()+-={}&verbar;\;':"&lt;&gt;?/.,|`#半角标点及符号_____________________________`

注意：标题在一文中出现多次，要更新引用

##### 大小写敏感

/docs/realtime_v2.html#web_hook

##### 不要用 URL-Encoded 格式

```单聊的情景相对也是比较简单的，用户可以选择向任何人发送相应的消息。如果应用开启 [签名认证](https://leancloud.cn/docs/realtime.html#%E6%9D%83%E9%99%90%E5%92%8C%E8%AE%A4%E8%AF%81)，```

更新比较麻烦：用 Find 全文搜索

push_guide.html#%E8%B7%9F%E8%B8%AA-android-%E6%8E%A8%E9%80%81%E5%92%8C-app-%E7%9A%84%E6%89%93%E5%BC%80%E6%83%85%E5%86%B5 

### 列表

#### 有序列表

结尾用分号，即使是一个短句子，最后一项用句号。

1. 打开菜单 **File**；
2. 勾选 **合并所有图层**，点击 **确认**；
3. 选择 **Save...** 来保存。
  
#### 无序列表

句子中有逗号，结尾加上句号，没有则结尾不加句号。

* 这是个短句子
* 上一条是短句子，所以不用加句号。
* 最后一条也是短句子

句子中出现了标点的话，结尾就加上句号。

### 快捷键

使用 HTML 标签 &lt;kbd&gt; 来标识键盘按键，比如 ```<kbd>Command</kbd>+<kbd>F3</kbd>``` 的效果是这样的： <kbd>Command</kbd>+<kbd>F3</kbd>。

### 表格

#### 基本样式

```
列 A|列 B|列 C
:---|:---|:---
```
- 每栏用三个下横线代替（不能少于三个）
- 栏内强行换行，行尾加上 HTML 标签 &lt;br/&gt;

```
列 A|列 B|列 C
:---|:---|:---
A<br/>B<br/>C<br/>|<kbd>D</kbd><kbd>E</kbd><kbd>F</kbd>|
...|...|...
```
列 A|列 B|列 C
:---|:---|:---
A<br/>B<br/>C<br/>|<kbd>D</kbd><kbd>E</kbd><kbd>F</kbd>|
...|...|...

列 A|列 B|列 C
:---|:---|:---
左对齐|

#### 参数列表

- 参数：按字母顺序排列
- 约束：可选值「必须」或留空，居中对齐。

参数|类型|约束|默认值|描述
:---|:---|:---:|:---|:---
enable|Boolean||`false`| 约束为「可选」时就不需要写出来。
type|String|必须|`"text"`|

```
参数|类型|约束|默认值|描述
:---|---|:---:|:---|:---
enable|Boolean||`false`| 约束为「可选」时就不需要写出来。
type|String|必须|`"text"`|
```
## 变量

系统变量有三个：appid、appkey、masterkey。
- appname？
  /docs/views/leanengine_guide-python.md
  `$ avoscloud add <appName> <appId>`
- 变量默认值
  未登录时显示为：`<APP-ID>`
  <APP-ID-登录控制台后可自动填充>
  >"X-LC-Key: ,master"这个参数怎么设置啊？不像键值对啊，没看过这种形似的参数
  >原文：`curl -X POST \ -H "X-LC-Id: {{appid}}" \ -H "X-LC-Key: {{masterkey}},master" \`

```
// 初始化参数依次为 this, AppId, AppKey
{{appid}}  //你的 App Id、
var id = '<已知任务 id>'; 
${已知任务 ID}、
{{id}}
/1.1/resetPasswordBySmsCode/:code
$PROJECT_DIR

[AVOSCloudSNS setupPlatform:AVOSCloudSNSSinaWeibo withAppKey:@"Weibo APP ID" andAppSecret:@"Weibo APP KEY" andRedirectURI:@""];

<script src="https://cdn1.lncld.net/static/js/av-core-mini-{版本号}.js"></script>

${timestamp} 触发推送的时间戳（Unix 时间戳）
如果想查询某个矩形框内的对象，可以使用 `within [西南坐标] and [东北坐标]` 的语法：
PHP 安装：将压缩文件解压并置于项目文件夹下，如 $APP_ROOT/vendor/leancloud

├── avoscloud-feedback-{version-number}.zip     // LeanCloud 用户反馈模块
├── avoscloud-sns-{version-number}.zip          // LeanCloud SNS 模块
├── <YOUR-APP-NAME>.iml 

AVOSCloud.requestSMSCodeInBackground(AVUser.getCurrentUser().getMobilePhoneNumber(), "某应用", "具体操作名称", 10, new RequestMobileCodeCallback() {
AV.User.verifyMobilePhone('6位数字验证码').then(function(){

var client = require('redis').createClient(process.env['REDIS_URL_<实例名称>']);  
```


对单引号和双引号不做要求

- 列表项目后的标点：；和 。
- 顿号

## 常见错别字
错误|正确|解释
---|---|---
登陆|登录|
帐户|账户|
做为|作为|


`fetch` 系方法 fetchXXX
`orderBy...`

缩写

## 修改标题、锚点、文件名、存档后的流程

修改前，要搜索并更新被引用过的地方，目录如下：

- `docs\views`
- `docs\md`
- `avfr`（官网）
/Users/myleslee/Documents/github/docs/md,
/Users/myleslee/Documents/github/docs/views,
/Users/myleslee/Documents/github/avfr

## 措词
  * `[NSNumber numberWithInt:50]` 换成 `@50`？（Parse 英文文档全部用简写格式，中文仅有 1 处）

## 其他

```
$ git clone git@github.com:leancloud/node-js-getting-started.git
$ git clone https://github.com/leancloud/node-js-getting-started.git
$ cd node-js-getting-started
```
把所有的仓库地址都改成 https 的，不然没配置 Github 私钥就没法下载（要密码）
  
```
  [query whereKey:@"wins" lessThan:[NSNumber numberWithInt:50]]
  [query whereKey:@"arrayKey" containsAllObjectsInArray:@[@2, @3, @4]]
```
  * 创建变量时，`*` 和变量名之间不加空格，乘法表达式加空格如：24 * 60 。
  
```
  AVQuery * query = [AVRelation reverseQuery:user.className relationKey:@"myLikes" childObject:post];

```
  * 账户 √ 帐户 x
    LeanCloud 账户中的「数据管理」页面
  
## Parse 文档新增：
   - Parse also supports NSDate, NSData, and **NSNull**.
   - 查询 - 用 NSPredicate 规定限制条件
   - swift code
   - 或 `[]` 下标索引访问任何字段

## 疑问
   * `whereKeyExists` 用来查询具备某一**键集**条件的对象…… 原文是 If you want to retrieve objects that have a particular **key set**，但举例不是健集：`[query whereKeyExists:@"score"];`
   * 
   
## 词汇表

原文|译文|备注
:---|:---|:---
built-in fields | 内置字段 |
utility function | 辅助方法 |
query | n.查询 v.检索 |
block | block|iOS，不用翻译
AND | [逻辑运算符](https://msdn.microsoft.com/zh-cn/library/ms189773.aspx) |
dot notation |点操作符、点语法 |
Primitive property types| 原始属性类型|
dev|开发（证书），测试 staging、生产 production


## 惯用词
推荐|不推荐|备注
:---|:---|:---
LeanCloud 云端|LeanCloud 服务端|
应用|app、App、APP|参考 Parse 英文文档
控制台|后台|
APNs|APNS|[Apple Push Notification service (APNs for short)](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html)
JSON|json|<http://json.org/>
例如|一个简单的例子|
Web 框架|web 框架|


## 其他
- 20150416 - double spaces can be taken as linebreak (MD)
- 替换变量用 大_写_字_母 加下划线表示，并加注释：  
  `cd $PROJECT_ROOT_DIR    # 请将 $PROJECT_ROOT_DIR 替换为你自己的项目根目录`  
   信息 `X-AVOSCloud-Session-Token: <sessionToken>`，该 `sessionToken` 在用户登录或注册时服务端会返回

## 引用 

- Demo 代码：`#L36`
- 

## 常见问题

FAQ 中的提问：用 h3 标题还是加粗？

```<div class="callout callout-info">蓝色外框</div>```

<img width="849" alt="screen shot 2015-08-28 at 17 35 31" src="https://cloud.githubusercontent.com/assets/108758/9543430/5a916eac-4dab-11e5-8164-65fec24d2e9a.png">

- 「的、地、得」用法
  - 的：名词前【例】
  - 地：动词前【例】认认真真地写
  - 得：动词/形容词**后**【例】看得清清楚楚、白得刺眼、关系处理得很好

## 待解决问题

- 如何在本地浏览 API 文档（localhost:3000 映射为 /dist，而 /api 与其在同一级目录）
- 过期文档移动到 /archive 目录中，更新搜索 index，也减少 overhead from parsing MD files

## 常用 HTML Entity

符号|Code|说明
---|---|---
&check;|`&check;`|
&middot;|`&middot;`|标注文章的层次，如：[iOS 推送指南 &middot; 清除 badge](ios_push_guide.html#清除_Badge)


## 替换

Find|Replace|Find RE|Replace RE
---|---|---|---
##标题|## 标题|`(#{2,6})([^\s|#].)`|`\1 \2`
