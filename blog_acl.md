# 将数据安全捍卫到底：权限管理（ACL）文档全新发布
(原标题：ACL 文档独立发布，权限管理从小做起)

随着使用 LeanCloud 的开发者越来越多，大家慢慢注意到一些在开发初期容易被忽视的漏洞，其中最容易被忽略但在我们的文档中又占据了重要地位的内容就是：权限管理（ACL）的使用。

ACL 全称为 Access Control List，维基百科解释为：

>存取控制串列，是使用以访问控制矩阵为基础的访问控制方法，每一个对象对应一个串列主体。访问控制表描述每一个对象各自的访问控制，并记录可对此对象进行访问的所有主体对象的权限。

<p style="text-align:center;"><img src="https://blog.leancloud.cn/wp-content/uploads/2015/10/09210Bb8-3.png" /></p>

等等，这个听上去怎么一阵头晕，这跟我的应用数据安全到底有什么关系？先别着急，我们当然不会用这么晦涩的语言来讲解 ACL，来看下面的例子：

公司的保险柜只有财务人员才能打开，那么对于保险柜来说，其 ACL 可以表示为：

```
{
    "role:finance": {
        "access": true
    }
}
```

即只有角色（role）为 **财务**（finance）的人才拥有打开保险柜的权限（access ＝ true）。

这便是实现 ACL 的一种方式。实际上 ACL 就是一张清单，罗列出谁都可以访问和操作什么，其机制相当于操作系统中「用户」和「用户组」—— 你若指定只有某个用户或用户组才能查看或修改文件或文件夹的内容，那不相干的人就被拒之门外了。在数据库系统中这种控制管理也很常见，比如，工资表只能由人事部专员来读取和修改，库存表可以让销售人员读取，但不能修改等等。

那回到「应用数据安全」这个话题上来。在使用 LeanCloud 对数据进行增删改查的时候，你是否想过也应该在应用中实施 ACL 机制来保护数据呢？

答案是肯定的，而且是非常必要的。

## 使用 ACL 的必要性
  
大家知道，我们在使用 LeanCloud SDK 时，需要在初始化代码中明文写入 AppId 和 AppKey。如果你的竞争对手或是恶意用户，反编译了你的 apk 或者打包好的安装程序，就能提取出 AppId 和 AppKey，这样就可以模拟客户端身份来提交请求，非法篡改数据。

而用 JavaScript SDK 做开发都涉及不到反编译，只要在浏览器中查看源代码，这些信息就都暴露无疑。再者，已离职的开发团队成员也曾经使用或仍知晓这些关键信息，这也是隐患。所以很显然，我们不能把 AppId 和 AppKey 作为应用仅有的防御体系，更何况有些高手还能直接从应用链接或网络请求中截获敏感数据来伪造请求。

但是，如果使用了 ACL，以上的安全隐患就都可以避免了！

整体上讲，因为使用了 ACL 的数据只允许指定的用户或者指定的角色来读取，而这种用户或角色信息在反编译的代码中是不存在的，所以即使请求被模拟发送到 LeanCloud 服务端，也会因为鉴权失败而被拒绝执行，从而数据安全有了保障。

具体来看，在 LeanCloud 后端的数据表中，每一个 AVObject 都会有自己的 ACL，这个 ACL 就是提供给开发者用来管理权限的。例如，一个对象的默认的 ACL 如下：

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

关于 ACL 的深入使用，我们还编写好了详细的开发指南，欢迎围观。

- 《ACL 快速入门：[iOS](https://leancloud.cn/docs/acl_quick_start-ios.html) | [Android](https://leancloud.cn/docs/acl_quick_start-android.html) | [JavaScript](https://leancloud.cn/docs/acl_quick_start-js.html)》：ACL 原理和使用的必要性
- 《权限管理使用指南：[iOS](https://leancloud.cn/docs/acl_guide-ios.html) | [Android](https://leancloud.cn/docs/acl_guide-android.html) | [JavaScript](https://leancloud.cn/docs/acl_guide-js.html)》：ACL 的具体使用细则和代码示例

最后，作为开发者永远的小伙伴，LeanCloud 在此向你温馨提示：

> 飞驰在道路上的时候别忘了给车加个保险杆！
