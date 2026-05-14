# newehall: jsonp/ywtb/searchServiceItem — 搜索服务事项

全局搜索服务和应用。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/searchServiceItem?searchKey={keyword}&flag=0&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 参数

| 参数 | 说明 |
|------|------|
| `searchKey` | 搜索关键词（`flag=0` 时空字符串返回全部） |
| `flag` | 标志位 |
