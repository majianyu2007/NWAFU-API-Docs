# personalInfo/UserOnline/user/queryUserOnline — 在线用户 & 登录历史

获取当前在线会话列表和完整登录历史记录。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/UserOnline/user/queryUserOnline?t={unix_timestamp}` |
| 响应格式 | `code`/`message`/`datas` |

## 响应结构

```json
{
  "code": "0",
  "datas": {
    "configIpAddress": "https://ip.cn/?ip=",
    "userOnline": [
      {
        "id": "93D598E5959D442DB61615614C6CD6DC",
        "ip": "10.x.x.x",
        "useragent": "Mozilla/5.0 (Macintosh; ...) Chrome/124.0...",
        "logintype": 8,
        "loginTypeDesc": "fido生物识别登录",
        "loginname": "2024012001",
        "logintimeStr": "2026-05-14 13:35:36",
        "ipAddress": "陕西省咸阳市",
        "loginLocation": "内网",
        "clientType": 1,
        "countryName": "中国",
        "rememberme": 0
      }
    ],
    "userOnlineRememberMe": [
      {
        "logintype": 2,
        "loginTypeDesc": "免登录",
        "rememberme": 1
      }
    ],
    "currentBrowserTGC": "TGT-xxxx-REDACTED",
    "remoteLoginEnabled": true
  }
}
```

## loginType 枚举

| 值 | loginTypeDesc | 说明 |
|----|--------------|------|
| 1 | 账号密码登录 | username + password |
| 2 | 免登录 | remember me |
| 8 | fido生物识别登录 | FIDO2 passkey |

## 会话字段

| 字段 | 说明 |
|------|------|
| `ip` | IP 地址 |
| `useragent` | 浏览器 UA |
| `ipAddress` | IP 归属地 |
| `loginLocation` | 登录位置（内网/外网） |
| `clientType` | 客户端类型（1=PC） |
| `currentBrowserTGC` | 当前浏览器的 TGC ticket |
