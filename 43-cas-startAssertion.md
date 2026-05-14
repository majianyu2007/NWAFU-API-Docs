# POST /authserver/startAssertion — FIDO2 开始验证

向 AuthServer 请求 FIDO2/WebAuthn 认证挑战。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/authserver/startAssertion` |
| Content-Type | `application/json;charset=utf-8` |

## 请求体

```json
{
  "userId": "MjAyNTAxMzY2NQ==",
  "id": "48c5c86aac514c8e8d4c8eed618ae101"
}
```

| 字段 | 说明 |
|------|------|
| `userId` | Base64 编码的学号 |
| `id` | deviceBindingId（`anonbiometricsd`，从浏览器 localStorage 获取） |

## 响应

```json
{
  "result": {
    "success": true,
    "request": {
      "publicKeyCredentialRequestOptions": {
        "extensions": {"appid": "https://authserver.nwafu.edu.cn"},
        "userVerification": "preferred",
        "challenge": "t-WmxzyloHtI9YP7Yb2OVtbioZO-ygjU7m6YzOFzpBE",
        "rpId": "authserver.nwafu.edu.cn",
        "allowCredentials": [
          {"id": "qZEYuwS6Qv2DdGUFbJj2xg", "type": "public-key"}
        ]
      },
      "requestId": "7zXtPWwE6Q83Q82vKmfn68DnHCE9PJKZBWYfOUXRJ8E"
    }
  }
}
```

## 后续步骤

1. 使用 challenge 构建 WebAuthn assertion
2. 用 ECDSA P-256 私钥签名
3. POST 到 `/authserver/login`（FIDO2 模式）
