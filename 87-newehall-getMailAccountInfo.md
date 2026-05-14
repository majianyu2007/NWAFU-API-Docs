# newehall: jsonp/personalRemind/getMailAccountInfo.do — 邮箱账号信息

获取用户校园邮箱账号信息。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/personalRemind/getMailAccountInfo.do?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 响应

```json
{
  "mailAccountsList": [],
  "mailDomainList": ["nwafu.edu.cn"],
  "hasLogin": true
}
```
