2015-10-28 3:24 PM

## app_search_guide.md

https://github.com/leancloud/docs/pull/638/files

当 `query.hasMore()` 返回 `true` 的时候，你可以不停地调用 `query.find()` 来向下翻页。

如果在不同请求之间无法保存查询的 query 对象，可以利用 sid 做到翻页，一次查询是通过 `query._sid` 来标示的，你可以通过 `query.sid("上次查询的query._sid")` 来重建查询 query 对象，继续翻页查询。sid 在 5 分钟内有效。
