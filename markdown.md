发送邮件至 <support@leancloud.rocks> 。

* 对公账户付款

 公司名称：美味书签（北京）信息技术有限公司  
 > 开户　行：**中国银行北京大运村支行**  
 > 银行账号：**344159259324**  

```c#
public async void JerryReceiveMessageFromTom()
{
    //Jerry 用自己的名字作为 ClientId 建立了一个 AVIMClient
    AVIMClient client = new AVIMClient("Jerry");

    //Tom 登陆到系统
    await client.ConnectAsync();

    //Jerry 设置接受消息的方法，一旦有消息收到就会调用这个方法
    client.OnMessageReceieved += (s, e) =>
    {
        if (e.Message is AVIMTextMessage)
        {
            string words = ((AVIMTextMessage)e.Message).TextContent;
            //words 内容即为：Hello,Jerry!
        }
    };
}
```

```javascript
public async void JerryReceiveMessageFromTom()
{
    //Jerry 用自己的名字作为 ClientId 建立了一个 AVIMClient
    AVIMClient client = new AVIMClient("Jerry");

    //Tom 登陆到系统
    await client.ConnectAsync();

    //Jerry 设置接受消息的方法，一旦有消息收到就会调用这个方法
    client.OnMessageReceieved += (s, e) =>
    {
        if (e.Message is AVIMTextMessage)
        {
            string words = ((AVIMTextMessage)e.Message).TextContent;
            //words 内容即为：Hello,Jerry!
        }
    };
}
```
```
//2015-05-06 注意更新顺序
leanengine_guide-cloudcode.md
leanengine_guide-node.md
leanengine_guide-python.md
//----------------
views/leanengine_guide-node.md
views/leanengine_guide-cloudcode.md
views/leanengine_guide-python.md
views/leanengine_guide.tmpl
```


[https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links]

1. [./start.html](./start.html)
2. [start.html](start.html)
3. [/start.html](/start.html)
