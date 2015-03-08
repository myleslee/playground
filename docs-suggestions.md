1. 格式：
  * `[NSNumber numberWithInt:50]` 换成 `@50`？（Parse 英文文档全部用简写格式，中文仅有 1 处）
  
   ```
  [query whereKey:@"wins" lessThan:[NSNumber numberWithInt:50]]
  [query whereKey:@"arrayKey" containsAllObjectsInArray:@[@2, @3, @4]]
  ```

  * 创建变量时，`*` 和变量名之间不加空格，乘法表达式加空格如：24 * 60 。
  ```
  AVQuery * query = [AVRelation reverseQuery:user.className relationKey:@"myLikes" childObject:post];
  ```
  
3. Parse 文档新增：
   - Parse also supports NSDate, NSData, and **NSNull**.
   - 查询 - 用 NSPredicate 规定限制条件
   - swift code
   - 或 `[]` 下标索引访问任何字段

4. 疑问：
   * `whereKeyExists` 用来查询具备某一**键集**条件的对象…… 原文是 If you want to retrieve objects that have a particular **key set**，但举例不是健集：`[query whereKeyExists:@"score"];`
   * 
   
5. 词汇表：

   | 原文  | 译文 |
   | ------------- | ------------- |
   | built-in fields | 内置字段 |
   | utility function | 辅助方法 |
   | query | n.查询 v.检索 |
   | block | block |
   | AND | [逻辑运算符](https://msdn.microsoft.com/zh-cn/library/ms189773.aspx) |
   | dot notation |  点操作符、点语法 |



