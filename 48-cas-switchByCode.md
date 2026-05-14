# GET /authserver/switchByCode — 切换身份

在关联账号之间切换（多身份用户）。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://authserver.nwafu.edu.cn/authserver/switchByCode?switchCode={code}` |

## 说明

`switchCode` 来自 `bindingUserList` 响应中的 `redirectUrl`。
