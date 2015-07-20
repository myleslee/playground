
# LeanCloud 文档样式指南（增补版）

## Cheat Sheet

## 格式

### 列表

#### 标点

- **有序列表**：结尾用分号，即使是一个短句子，最后一项用句号。

1. 打开菜单 **File**；
2. 勾选 **合并所有图层**，点击 **确认**；
3. 选择 **Save...** 来保存。
  
- **无序列表**：句子中有逗号，结尾加上句号，没有则结尾不加句号。

* 这是个短句子
* 上一条是短句子，所以不用加句号。
* 虽然这是最后一条，如果不是长句子，也不用加句号。

### 表格

#### 基本样式

```
列 A|列 B|列 C
:---|:---|:---
```
- 每栏用三个横线代替

列 A|列 B|列 C
:---|:---|:---
左对齐|

#### 参数列表

- 参数：按字母顺序排列
- 约束：可选值「必须」或留空，居中对齐。
- 

参数|类型|约束|默认值|描述
:---|:---|:---:|:---|:---
type|String|必须|`"text"`|
enable|Boolean||`false`| 约束为「可选」时就不需要写出来。



```
参数|类型|约束|默认值|描述
:---|---|:---:|:---|:---
type|String|必须|`"text"`|
enable|Boolean||`false`| 约束为「可选」时就不需要写出来。
```


写作标准
变量名
{{appid}} //你的 App Id、
var id = '<已知任务 id>'; ${已知任务 ID}、{{id}}
对单引号和双引号不做要求
章节引用
[查询 - 条件查询 - 约束](#约束)
注意：标题在一文中出现多次，要更新引用
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

## 其他
- 20150416 - double spaces can be taken as linebreak (MD)
- 深圳华强北 Hua Qiang Bei 
- 替换变量用 大_写_字_母 加下划线表示，并加注释：  
  `cd $PROJECT_ROOT_DIR    # 请将 $PROJECT_ROOT_DIR 替换为你自己的项目根目录`  
   信息 `X-AVOSCloud-Session-Token: <sessionToken>`，该 `sessionToken` 在用户登录或注册时服务端会返回



