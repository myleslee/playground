
# LeanCloud 文档样式指南（增补版）

## Cheat Sheet

1. ```[应用控制台](/applist.html#/apps)```
2. 表格
  ```
  参数|类型|约束|说明
  ---|---|---|---

  参数|类型|约束|默认|说明
  ---|---|---|---|---
  &nbsp;&nbsp;&nbsp;&nbsp; a||||
  ```
3. 
## 格式

### 超链接

链接文字与链接相同，使用 `<link>` ，而非 `[link](link)` 这种繁琐的语法。邮件地址使用 `<email_address>`

- 内部链接：章节引用[查询 - 条件查询 - 约束](#约束)
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

##### 不要 escape

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

```
{{appid}}  //你的 App Id、
var id = '<已知任务 id>'; 
${已知任务 ID}、
{{id}}
/1.1/resetPasswordBySmsCode/&lt;code&gt;
$PROJECT_DIR

[AVOSCloudSNS setupPlatform:AVOSCloudSNSSinaWeibo withAppKey:@"Weibo APP ID" andAppSecret:@"Weibo APP KEY" andRedirectURI:@""];

<script src="https://cdn1.lncld.net/static/js/av-core-mini-{版本号}.js"></script>

${timestamp} 触发推送的时间戳（Unix 时间戳）
```


对单引号和双引号不做要求

列表项目后的
标点：；和 。
`fetch` 系方法 fetchXXX
缩写

## 措词
  * `[NSNumber numberWithInt:50]` 换成 `@50`？（Parse 英文文档全部用简写格式，中文仅有 1 处）
  
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

## 惯用词
推荐|不推荐|备注
:---|:---|:---
LeanCloud 云端|LeanCloud 服务端|
app|App、APP|参考 Parse 英文文档
控制台|后台|
APNs|APNS|[Apple Push Notification service (APNs for short)](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html)
JSON|json|<http://json.org/>

## 其他
- 20150416 - double spaces can be taken as linebreak (MD)
- 深圳华强北 Hua Qiang Bei 
- 替换变量用 大_写_字_母 加下划线表示，并加注释：  
  `cd $PROJECT_ROOT_DIR    # 请将 $PROJECT_ROOT_DIR 替换为你自己的项目根目录`  
   信息 `X-AVOSCloud-Session-Token: <sessionToken>`，该 `sessionToken` 在用户登录或注册时服务端会返回

## 常见问题

是 h3 标题还是加粗问话？

```<div class="callout callout-info">蓝色外框</div>```
<img width="849" alt="screen shot 2015-08-28 at 17 35 31" src="https://cloud.githubusercontent.com/assets/108758/9543430/5a916eac-4dab-11e5-8164-65fec24d2e9a.png">

