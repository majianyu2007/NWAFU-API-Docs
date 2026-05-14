# newehall: jsonp/ywtb/getUnreadMessageCount — 未读消息数

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/getUnreadMessageCount?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 响应

```json
{
  "result": "success",
  "data": {
    "wid": "message",
    "cardName": "未读消息",
    "cardSeq": 4,
    "totalSize": 0
  }
}
```
