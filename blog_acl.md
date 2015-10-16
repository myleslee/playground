#ACL 文档独立发布，权限管理从小做起

随着 LeanCloud 开发者越来越多，诸多开发者在开发中发现了初期容易被忽视的小漏洞。粗心的开发者很容易就忽略了我们文档中一章比较重要的内容—— ACL 的使用。

ACL 全称为 Access Control List ，维基百科解释为：存取控制串列，是使用以访问控制矩阵为基础的访问控制方法，每一个对象对应一个串列主体。访问控制表描述每一个对象各自的访问控制，并纪录可对此对象进行访问的所有主体对对象的权限。

等等，这个听上去怎么一阵头晕，这个跟我的应用数据安全到底有什么关系？

![chenglongdage](https://blog.leancloud.cn/wp-content/uploads/2015/10/09210Bb8-3.png)

先别着急，我们从一个案例入手：

公司的门禁系统只有刷工卡才能进出，此时的 ACL 就简单的可以理解为：

```
{
    "role:staff": {
        "access": true
    }
}
```

翻译成中文就是：所有角色（role）为 员工（staff）的人拥有进入公司的权限（access ＝ true）。

这仅仅是实现 ACL 的一种方式。

我们回到应用数据安全这个话题上，在使用 LeanCloud 进行数据增删改查的时候，开发者是否也想过，数据应该也有类似于门禁卡的系统来保障，我的数据的安全呢？

答案是有的，细心的用户会发现，每一个 AVObejct 都会有自己的 ACL，这个 ACL 就是提供给开发者用来管理权限的。例如，一个对象的默认的 ACL 如下：

```
{
    "*": {
        "read": true,
        "write": true
    }
}
```
这表示这个数据是开放的，只要是合法的修改请求（AppID 以及 AppKey 是正确的）都会被执行。

如果正确的设置了 ACL 话，我们可以让某些特定的角色发来的修改请求才能生效：

```
{
    "*": {
        "read": true
    },
    "role:Administrator": {
        "write": true
    }
}
```
以上的内容表示：所有人都可读，但是只有角色是 Administrator 的用户才能修改。

「我的应用如果不设置 ACL 会有什么坏处呢？」

关于这一点，LeanCloud 官方特地编写了一个 ACL 快速入门的文档:[iOS](https://leancloud.cn/docs/acl_quick_start-ios.html) | [Android](https://leancloud.cn/docs/acl_quick_start-android.html) | [JavaScript](https://leancloud.cn/docs/acl_quick_start-js.html) ，我相信，各位看完文档可以对 ACL 有更进一步的理解。


关于 ACL 的深入使用，我们特地编写了详细的开发指南：

权限管理使用指南: [iOS](https://leancloud.cn/docs/acl_guide-ios.html) | [Android](https://leancloud.cn/docs/acl_guide-android.html) | [JavaScript](https://leancloud.cn/docs/acl_guide-js.html)


作为开发者永远的小伙伴，LeanCloud 友情提示

> 飞驰在道路上的时候别忘了给车加个保险杆
