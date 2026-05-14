# POST /authserver/reAuthCheck/changeReAuthType.do — 切换验证类型

在二次验证页面切换验证方式。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/authserver/reAuthCheck/changeReAuthType.do` |

## 参数

| 参数 | 说明 |
|------|------|
| `reAuthType` | 验证类型（`10` = TOTP 安全令牌） |
