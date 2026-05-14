# POST /authserver/login — FIDO2 登录

提交签名后的 WebAuthn assertion 完成无密码登录。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/authserver/login`（无 service） |
| Content-Type | `application/x-www-form-urlencoded` |

## 表单字段

| 字段 | 说明 |
|------|------|
| `username` | Base64 编码的学号 |
| `responseJson` | JSON 字符串 `{"requestId":"...","credential":{...},"sessionToken":null}` |
| `_eventId` | `"submit"` |
| `cllt` | `"fidoLogin"` |
| `dllt` | `"generalLogin"` |
| `lt` | `""` (空) |
| `rememberMe` | `"true"` |
| `execution` | 来自无 service 的登录页面 |

## 成功响应

302 重定向到 `/authserver/index.do`，Set-Cookie 设置 CASTGC=REDACTED

## FIDO2 两步流程

1. 无 service 页面完成 FIDO2 获取 TGC
2. 带 TGC 访问 `?service=...` 获取 ST
