# personalInfo/common/getUserConf — 用户配置

获取个人中心用户配置。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/common/getUserConf` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": {
    "agentAuthDisplay": false,
    "nickName": "",
    "languageEnabled": true,
    "personalDisplay": true,
    "cn": "张三",
    "uid": "2024012001",
    "sexCode": "0",
    "schoolLogEnabled": true,
    "logoutUrl": "https://authserver.nwafu.edu.cn:443/authserver/logout?service=...",
    "theme": "default"
  }
}
```
