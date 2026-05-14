# newehall: jsonp/ywtb/card/getNewsTypeByCode — 按类型获取资讯

获取指定分类的新闻通知。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/card/getNewsTypeByCode?type={typeCode}&pageSize=6&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 已知 type 值

| type | 分类 |
|------|------|
| 4 | 新闻焦点 |
| 5 | 热点聚焦 |
| 6 | 媒体我校 |
| 7 | OA通知公告 |
| 8 | 全部 |
