# personalInfo/common/tenant/info — 租户信息

获取学校 Logo 等租户信息。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/common/tenant/info?t={unix_timestamp}` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": {
    "schoolLogoUrl": "https://ehall.nwafu.edu.cn/oss/schoolIcon/clientPcLogo.png"
  }
}
```
