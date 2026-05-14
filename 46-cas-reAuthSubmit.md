# POST /authserver/reAuthCheck/reAuthSubmit.do — 提交二次验证

提交 TOTP 验证码完成二次验证。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/authserver/reAuthCheck/reAuthSubmit.do` |

## 参数

| 参数 | 说明 |
|------|------|
| `code` | TOTP 6 位验证码 |

## 成功响应

302 重定向到 service callback URL。
