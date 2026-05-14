# getPageView

页面浏览埋点上报。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://ehall.nwafu.edu.cn/getPageView?_t={timestamp}&pageCode={pageCode}&originalUrl={urlEncoded}&lang=zh_CN` |

## 参数

| 参数 | 说明 | 示例 |
|------|------|------|
| `pageCode` | 页面代码 | `""`(首页)、`hall`、`taskList`、`work`、`ywztc`、`search` |
| `originalUrl` | URL 编码的原始 URL | `https%3A%2F%2Fehall.nwafu.edu.cn%2Findex.html%23%2F` |
