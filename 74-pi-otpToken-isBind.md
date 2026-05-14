# personalInfo/otpToken/isBind — OTP 令牌绑定状态

检查用户是否已绑定 TOTP 安全令牌。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/otpToken/isBind` |
| 响应格式 | `code`/`message`/`data` |

## 响应

```json
{ "code": "0", "data": true, "message": null }
```

`data: true` 表示已绑定 TOTP 安全令牌。
