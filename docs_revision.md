# 文档平台改进

## 内容

- 订阅更新
- 手工定位锚点，不一定是标题，中英文均可：`<a id="customize_notification_for_offline_message" data-author="2015-11-15@myleslee@Da Li">`

## 结构重构

- 回到顶部
  - 固定到底部
  - 平滑移动
- 书签
  - 返回原来章节
  - 定制 anchor 来定位每个段落
- 最后更新日期（放顶部）

### 快速入门

- 没有主标题，导航也不高亮
- Step 3 的内容只能从 H4 开始（H3 有下横线）
- 如果不登录，「选择应用」不出现（鼓励用户登录）
- 不登录状态下 {{AppId}} 要显示为 `<APP_ID>`

## 样式

- 自定义下划线（`<em>`?）：<http://36kr.com/p/210772.html>  
  1. **加粗标题一**  
    这是一个正常的段落，**但有些文字也要加粗，看起来关注层次比较乱**。
  2. **加粗标题二**  
    如果用下划线来取代加粗，效果就会好很多。<span style="border-bottom:1px solid #333; padding-bottom:2px">斜体仅对西文有效，中文没有斜体，但下划线是通用的</span>。另外传统的 underline 样式过于接近字体的底部，所以推荐用 border。
 
- 加粗中的代码不要加粗：**加粗的中文与加粗的代码 `thisFunction()` 混合在一起**。 
- 图片加外边框。
- 代码块：底色（乱）、行号、指定行加亮
- inline-note、shy:
- External links
- External Reference: floating right 


```
$ avoscloud add <APP-NAME> <APP-ID>
```

```
2015-10-12T02:04:50.179Z    dreday  将逻辑放到前端： 1 如果android，ios，web都有的话，一个逻辑做三份，严重加大了前端程序员负担 2 三个接口无法统一 3 后期逻辑更改必须重新上线
```

## 控制台

- 在上方加入 docs 导航
- 


