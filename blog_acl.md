# 将数据安全捍卫到底：权限管理（ACL）文档全新发布

随着使用 LeanCloud 的开发者越来越多，大家慢慢注意到一些在开发初期容易被忽视的小漏洞，其中最容易被忽略但在我们的文档中又占据了比较重要的地位的内容就是：权限管理 ACL 的使用。

ACL 全称为 Access Control List，维基百科解释为：

>存取控制串列，是使用以访问控制矩阵为基础的访问控制方法，每一个对象对应一个串列主体。访问控制表描述每一个对象各自的访问控制，并纪录可对此对象进行访问的所有主体对象的权限。

<p style="text-align:center;">![chenglongdage](https://blog.leancloud.cn/wp-content/uploads/2015/10/09210Bb8-3.png)</p>

等等，这个听上去怎么一阵头晕，这跟我的应用数据安全到底有什么关系？先别着急，我们自然不会用这么晦涩的语言来讲解 ACL，来看下面的例子：

公司的门禁系统只有刷工卡才能进出，此时的 ACL 就可以简单地理解为：

```
{
    "role:staff": {
        "access": true
    }
}
```

用文字表述就是：所有角色（role）为 **员工**（staff）的人拥有进入公司的权限（access ＝ true）。

这便是实现 ACL 的一种方式。

回到「应用数据安全」这个话题上来。在使用 LeanCloud 进行数据增删改查的时候，你是否想过，自己的应用也应该应用类似于门禁卡这样的系统来保护数据呢？

答案是肯定的。详读过文档的用户会发现，每一个 AVObject 都会有自己的 ACL，这个 ACL 就是提供给开发者用来管理权限的。例如，一个对象的默认的 ACL 如下：

```
{
    "*": {
        "read": true,
        "write": true
    }
}
```

这表示该对象的数据对所有人都是开放的，只要是合法的修改请求（即 AppId 和 AppKey 正确），都会被 LeanCloud 云端执行。

如果正确设置了 ACL，我们可以只让具有某些特定角色的用户发来的修改请求生效：

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

以上设置代表：所有人都可读，但是只有角色是 Administrator 的用户才能修改。

**「我的应用如果不设置 ACL 会有什么坏处呢？」**

我们将不使用 ACL 的危险和隐患放在了《ACL 快速入门：[iOS](https://leancloud.cn/docs/acl_quick_start-ios.html) | [Android](https://leancloud.cn/docs/acl_quick_start-android.html) | [JavaScript](https://leancloud.cn/docs/acl_quick_start-js.html)》的文档中，相信大家看过文档后便会对其使用的必要性有更清楚的认识了。

关于 ACL 的深入使用，我们还编写好了详细的开发指南，欢迎围观。

权限管理使用指南：[iOS](https://leancloud.cn/docs/acl_guide-ios.html) | [Android](https://leancloud.cn/docs/acl_guide-android.html) | [JavaScript](https://leancloud.cn/docs/acl_guide-js.html)

最后，作为开发者永远的小伙伴，LeanCloud 在此向你温馨提示：

> 飞驰在道路上的时候别忘了给车加个保险杆！
