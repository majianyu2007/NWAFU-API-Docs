# POST /authserver/login — 密码登录

提交 AES 加密密码完成登录。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/authserver/login?service=...` |
| Content-Type | `application/x-www-form-urlencoded` |

## 表单字段

| 字段 | 说明 |
|------|------|
| `username` | 学号/工号 |
| `password` | AES-128-CBC 加密后的密码（64字符随机前缀 + 16字符 IV） |
| `execution` | 来自登录页面 |
| `_eventId` | `"submit"` |
| `cllt` | `"userNameLogin"` |
| `dllt` | `"generalLogin"` |
| `lt` | `""` (空) |
| `rememberMe` | `"true"` |

## 成功响应

302 重定向 → TOTP 二次验证页 或 service callback URL（含 ST）。

## 失败响应

200 带错误提示（`<div id="formErrorTip">` 或 JSON `resultCode`）。
