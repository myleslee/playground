过完年了，大伙都回来上班了。这里跟大家汇报下年前年后这四周我们都做了什么事情。

## 主要变更

闲话不提，这里介绍下开发者可能比较关心的改动。

首先，我们拆分了短信购买和帐户余额，你可以在财务菜单单独购买短信额度，这些额度在购买后，将不会在每月的账单里扣除，防止因为每月账单扣除可能导致短信余额不足的问题。建议使用了短信的用户尽快购买额度，我们会有一个过渡时间来让用户购买短信额度。在余额使用完成之前，也会通过短信和邮件的形式通知到你，为了收到短信，强烈建议你在开发者账户信息里填写手机号码。

其次，我们正式对外发布了 JavaScript Push SDK，你可以在网页上接收和推送消息，实现弹幕和在线客服之类的应用将非常方便，源码开放在 [leancloud/js-push-sdk](https://github.com/leancloud/js-push-sdk)，开发指南文档在[这里](https://leancloud.cn/docs/js_push.html)。我们还改进了 JavaScript SDK 的 AV.Promise 实现，兼容标准，增加 `done,catch,AV.Promise.race` 等方法，并增加了文档说明。

最后，我们合并了文档项目，不再区分内部和外部项目，并开放了文档生成程序。还发布了 [Awesome LeanCloud](http://sunng.info/awesome-leancloud/) 网站，可以查看和提交 LeanCloud 开源生态周边的工具或软件。 

## 网站和文档

网站我们做了非常多的细节改进，可能你未必能注意到。例如 API 统计专门增加了从云代码平台发起的调用统计、应用选项勾选会提示保存成功、改了 [API 在线测试工具](https://leancloud.cn/apionline/)支持 keys 和 include 查询等等。许多小的调整希望能让你使用管理功能更容易，更方便。

网站的其他改动：

* 在应用设置里，增加了转让应用功能。
* 创建应用时候可以选择拷贝一个来源应用的数据 Schema
* API 统计里 ，加了饼状图展现，可以根据平台、Class 或者操作类型做对比展示。
* 拆分短信购买，可以通过支付宝或账户余额购买短信，短信额度不会从每月账单里扣除。

(API 饼状图分析）
<a href="https://blog.leancloud.cn/wp-content/uploads/2015/03/Snip20150313_3.png" rel="attachment wp-att-2955"><img src="https://blog.leancloud.cn/wp-content/uploads/2015/03/Snip20150313_3-625x360.png" alt="Snip20150313_3" width="625" height="360" class="alignnone size-medium wp-image-2955" /></a>

最重要的事情是我们合并了内外文档项目，不再区分内部文档和外部文档项目，统一为 [LeanCloud/docs](https://github.com/leancloud/docs)，并且开放了文档生成代码，我们还对文档做了大量的优化，我们的新同事开始对各个 sdk 的开发指南做深入的 Review 和优化，希望能带给大家更好的阅读和使用体验。特别欢迎 fork 我们的项目，并提出改进意见。

最后，我们的工程师还发布了一个 [Awesome LeanCloud](http://sunng.info/awesome-leancloud/) 的聚合网站，在这里你可以看到社区维护的 LeanCloud 开源生态周边：多语言 SDK，最佳实践库，UI 组件，云代码模块等，欢迎更多的开发者们提交多语言 SDK，最佳实践库，UI 组件，云代码模块等类库。

## API 服务

* 短信模板的上限调整为 10 个。
* 增加 `/date` API 返回服务器时间。
* 修复匿名用户转换正式用户相关问题，匿名用户将在两种情况下转换为正式用户：提供用户名和密码注册或者更新、链接到一个第三方登录账号。
* 改进应用内搜索：不需要填写组件配置就可以使用应用内搜索，支持 `include` 查询，增加重建索引 API。
* 查询的 `keys` 参数支持反向选择，加上减号的字段将不在查询结果里返回，例如 `keys=-name,-age` 则查询结果不返回 `name` 和 `age` 字段。
* 改进了 `/push` 接口的错误提示，当推送涉及 iOS 设备且没有上传证书或者没有安装 Installation 的时候提早报错。
* 改进了数据导入，如果出错，在通知邮件里说明详细的错误信息。
* CQL 做了改进： limit 和 order by 子句可以任意排序，支持 `select -name,-age from Player` 的过滤选择不返回 `age` 和 `name`。
* 短信签名增加长度校验，要求在 10 个字符内。


## 消息推送及聊天

* iOS 推送支持 iOS 8 引入的 `title,title-loc-key,title-loc-args` 等新字段，并更新了文档。
* 发布了 [JavaScript Push SDK](https://github.com/leancloud/js-push-sdk)，支持网页推送。
* 实时通信增加[错误码文档](https://leancloud.cn/docs/realtime.html#服务器端错误码说明)。
* 消息推送增加[问题排查文档](https://leancloud.cn/docs/push_guide.html#推送问题排查)，方便自助分析推送问题。
* 聊天持续增强稳定性和性能。

## 云代码

* 彻底解决了 nginx 偶尔 502 的问题。
* 测试环境和生产环境做了分离。
* 命令行工具发布 0.6.6 —— 0.6.8 版本，详细更新日志请看[这里](https://github.com/leancloud/avoscloud-code-command/blob/master/changelog.md)。

## iOS SDK v2.6.11

* 聊天修复 `session` 关闭后重新打开导致 `group.session` 为 `nil` 的问题
* 添加创建 `transient` 属性群组的接口，可用作临时聊天室
* 用户反馈添加推送答复给用户功能。
* 修复匿名用户转换正式用户的相关问题。
* 修复离线时被邀请入群后接收离线消息的问题
* 添加缓存获取失败后请求重试次数限制

## Android SDK v2.7

* 增加了匿名用户转化为正式用户的处理逻辑
* 提高了统计的使用时长的准确性
* 修正了社交组件的 WebView 实现在 Android 4.2 以后出现的卡在 WebView 上的问题
* 修正了 `AVObject.toJSONObject` 方法中，遇到 Pointer 时的序列化异常
* 聊天 `onMessageSent` 中获取的 `AVMessage` 对象补齐 `fromPeerId`
* 聊天正确更新 `SessionManager` 中 `onlinePeerIds` 的数据

## JavaScript SDK v0.5.0
* 增强 AV.Promise，增加 `done,catch,finally,AV.Promise.race` 等方法，兼容 Promise/A+，并更新了开发指南和 API 文档。
* 修复更新对象可能更新没有变更的属性的 Bug，减少请求流量。
* 拆分 sdk，按照模块划分成多个文件。
* 使用 gulp 构建 sdk，清理代码。
* 修复事件流无法发送带有 AV.File、AV.Object 等类型的 Status。
* 修复 node.js 环境下上传文件没有扩展名的 Bug。

## Unity3D SDK

* 修复 AVQuery 查询中文字符时的错误
* 升级支持 Unity 5.0
