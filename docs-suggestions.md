1. 查询比较中，`[NSNumber numberWithInt:50]` 换成 `@50`
  
   ```
  [query whereKey:@"wins" lessThan:[NSNumber numberWithInt:50]]
  ```

2. 创建变量时，`*` 和变量名之间不加空格，乘法表达式加空格如：24 * 60 。
  ```
  AVQuery * query = [AVRelation reverseQuery:user.className relationKey:@"myLikes" childObject:post];
  ```
  
3. Parse 文档新增：
   1. Parse also supports NSDate, NSData, and **NSNull**.
   2. 查询 - 用 NSPredicate 规定限制条件
