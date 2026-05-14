# GET /authserver/reAuthCheck/reAuthLoginView.do — 二次验证页面

获取二次验证（2FA）页面。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://authserver.nwafu.edu.cn/authserver/reAuthCheck/reAuthLoginView.do?isMultifactor=true&service=...` |

## 说明

密码登录成功后，如果服务器要求二次验证，会 302 重定向到此页面。页面包含可用的验证方式选项（TOTP 安全令牌、FIDO 生物识别等）。
