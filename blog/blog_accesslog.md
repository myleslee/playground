通用的数据存储（AVObject）提供了很便捷的操作方式，可以随时对云端数据进行任意的增删改查。LeanCloud 云端从功能和性能考虑，一直按照缓存＋持久化的「热数据」模式进行存储，这一方案需要相对较高的实现成本。

我们了解到，LeanCloud 用户有不少业务需要保存日志、统计事件一类的数据，这种数据的特点是写入之后不会修改，而使用时用户只关注整体数据的统计结果，这种使用方式是一种典型的「冷数据」模式。实现该模式可以进一步提高云端数据的写入速度，让数据存储发挥出更大的并发吞吐能力。因此，我们特别推出了新的日志型（Log）数据存储类型。

日志型数据是冷数据，LeanCloud 云端会用不同方式来保存这类数据，那么在使用上它与普通的 AVObject 有什么差别呢？

## Class 的创建方式

用户在创建日志型的 Class（即云端的数据表）时，需要额外指定「是否为日志类型」这一标识，如下图所示：

<img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/CreateAccessLog.png" alt="CreateAccessLog" width="600" height="256" class="alignnone size-full wp-image-3839" />

勾选「是否为日志类型」选项后，创建出来的数据表即为日志类型。从下图中我们可以看到 AccessLog 表后面出现了一个 <span style="padding:4px 6px; font-size:0.85em; color:#f5a122; background-color:#fffaec;">LOG</span> 标签，它就是日志型数据表的标志。

<img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/AccessLogList.png" alt="AccessLogList" width="284" height="305" class="alignnone size-full wp-image-3840" />

## API 的使用方式

接下来，我们在 SDK 内调用正常的 AVObject 的 API 就可以创建和保存对象，写入到 AccessLog 表：

```objc
// for Objective-C
AVObject *accessRecord = [AVObject objectWithClassName:@"AccessLog"];
[accessRecord setObject:@"首页" forKey:@"page"];
[accessRecord setObject:@"小明" forKey:@"user"];
[accessRecord saveInBackground];
```

```java
// for Android
AVObject accessRecord = new AVObject("AccessLog");
accessRecord.put("page", "首页");
accessRecord.put("user", "小明");
accessRecord.saveInBackground();
```

注意，我们使用 API 只能向 AccessLog 表中插入新数据，但无法删除或修改其中任意一行数据。

我们在控制台中也可以看到，对日志型数据表的大部分修改操作选项都不可用：

<img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/ModifyAccessLog-625x183.png" alt="ModifyAccessLog" width="625" height="183" class="alignnone size-medium wp-image-3841" />

可用的选项有：删除全部数据、删除表、添加行、添加列。

另外，鉴于日志型数据表会存储大量数据，因此在以上记录明细的界面中仅会显示出最新的 20 条记录，以及所有记录的总数。

## 总结

总体说来，与标准的 AVObject 相比，日志型数据有如下不同：
<ul>
<li>Class 表只能在控制台中手工创建，不能通过 SDK 创建，但 SDK 可以向已建好的表内保存数据。</li>
<li>不支持 Class 绑定，即应用之间无法共享日志类型表中的数据。</li>
<li>列（column）不支持 Pointer、Relation 等复杂数据类型。</li>
<li>列只能增加，不能减少，不能重命名。</li>
<li>API：行数据不支持 update、delete。</li>
<li>API：不支持使用 query 来查询结果。</li>
<li>不支持应用内搜索。</li>
</ul>

那么既然不支持 API 的 query 查询，我们又如何使用这些日志型的数据呢？答案就是使用 LeanCloud 免费的 <a href="https://blog.leancloud.cn/2559/" target="_blank">离线分析</a>。

<img src="https://blog.leancloud.cn/wp-content/uploads/2015/11/queryAccessLog-625x254.png" alt="queryAccessLog" width="625" height="254" class="alignnone size-medium wp-image-3843" />

按照日志型数据表的设计初衷，我们知道开发者使用这一类型，主要是记录一些日志或事件，之后就是对其进行一些关键数据的统计分析。所以，对于日志类型数据，不管应用是否开启了「离线分析」这一选项，LeanCloud 云端都会自动将这部分数据按天导入离线分析平台。

现在，我们提供了不同的存储类别来满足不同的用户需求，包括用于频繁访问数据的通用存储 AVObject，和用于长期存档数据的日志型 AVObject (Log)。对于日志型数据的存储，我们能提供更高的并发吞吐能力，也默认为它开启了离线分析功能，欢迎大家试用并做出反馈！
