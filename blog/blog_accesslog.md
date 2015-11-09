通用的数据存储（AVObject）提供了很便捷的操作方式，可以随时支持任意的增删改查，LeanCloud 云端从功能和性能考虑，一直按照缓存＋持久化的「热数据」模式进行存储，这一方案会需要较高的实现成本。而有不少业务需要保存日志、统计事件一类的数据，这种数据的特点是，写入之后不会修改，且产品中只会关注数据整体的统计结果。这种使用方式，是一种典型的「冷数据」模式。为了更好地支持这一需求，提供更大的并发吞吐能力，我们特别推出了日志型数据存储类型。

日志型数据，与普通的数据类型相比，有什么区别呢？从接口上来说它们还是使用 AVObject 的 API，只是日志型数据，在创建的时候，需要指明「是否为日志类型」这一额外标识。操作截图如下：
<a href="https://blog.leancloud.cn/wp-content/uploads/2015/11/CreateAccessLog.png" rel="attachment wp-att-3839"><img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/CreateAccessLog.png" alt="CreateAccessLog" width="600" height="256" class="alignnone size-full wp-image-3839" /></a>
只要勾选上「是否为日志类型」这个特性，那么新创建的 AVObject 就是日志型数据了。我们可以在数据列表页面，看到这样的结果：
<a href="https://blog.leancloud.cn/wp-content/uploads/2015/11/AccessLogList.png" rel="attachment wp-att-3840"><img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/AccessLogList.png" alt="AccessLogList" width="284" height="305" class="alignnone size-full wp-image-3840" /></a>
这里可以看到 AccessLog 后面加上了一个「LOG」标签，来提示我们这是一种日志类型的数据。

创建之后，我们在 SDK 内调用原来的 AVObject API 就可以正常新建、保存数据了，其示意代码如下：

```objc
// for objective-c
AVObject *accessRecord = [AVObject objectWithClassName:@"AccessLog"];
[accessRecord setObject:@"首页" forKey:@"page"];
[accessRecord setObject:@"whoami" forKey:@"user"];
[accessRecord saveInBackground];
```

```java
// for android
AVObject accessRecord = new AVObject("AccessLog");
accessRecord.put("page", "首页");
accessRecord.put("user", "whoami");
accessRecord.saveInBackground();
```

既然日志型数据是冷数据，LeanCloud 云端会用不同方式来保存，那么在使用上与普通的 AVObject 有什么差别呢？我们可以从控制台看到，日志型数据展示的时候，大部分修改操作都是禁用了的：
<a href="https://blog.leancloud.cn/wp-content/uploads/2015/11/ModifyAccessLog.png" rel="attachment wp-att-3841"><img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/ModifyAccessLog-625x183.png" alt="ModifyAccessLog" width="625" height="183" class="alignnone size-medium wp-image-3841" /></a>

总的说来，日志型数据与标准的 AVObject 相比，有如下不同：
<ul>
<li>不支持在 SDK 内创建，SDK 内只可以保存</li>
<li>不支持 class 绑定</li>
<li>column 不支持 pointer，releation 等复杂数据类型</li>
<li>column只能加不能减，不能重命名</li>
<li>不支持 query</li>
<li>行数据不支持 update、delete</li>
<li>不支持应用内搜索</li>
</ul>

那么，对于日志型数据，我们能支持哪些操作呢？最主要的就是<a href="https://blog.leancloud.cn/2559/" target="_blank">离线分析</a>。从日志型数据的设计来源我们可以看到，开发者使用这一类型，主要是记录一些日志或者事件，之后最主要的目的就是从中进行一些关键数据的统计分析，所以，对于日志类型数据，不管应用是否开启了「离线分析」这一选项，LeanCloud 云端都会自动将这部分数据按天导入离线分析平台。从下面的截图可以看到：
<a href="https://blog.leancloud.cn/wp-content/uploads/2015/11/queryAccessLog.png" rel="attachment wp-att-3843"><img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/queryAccessLog-625x254.png" alt="queryAccessLog" width="625" height="254" class="alignnone size-medium wp-image-3843" /></a>

除了离线分析之外，对于日志型数据还支持如下功能：
<ul>
<li>查询最近20条和总数</li>
<li>删除表</li>
<li>清除所有表数据</li>
<li>增加新的 column</li>
</ul>

现在 LeanCloud 提供了不同的存储类别，用于满足不同的需求：包括用于频繁访问数据的通用存储 AVObject，和用于长期存档数据的 AVObject(Log)。对于日志型数据，我们能提供更高的并发吞吐能力，也默认为它们开启了离线分析功能，所以大家可以尽快试一下。
