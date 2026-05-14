# personalInfo/common/unTrustDeviceNotify — 不受信任设备通知

返回历史登录设备列表。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/common/unTrustDeviceNotify` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": [
    {
      "configId": "mac_os_x chrome_1778741823758",
      "deviceName": "mac_os_x chrome",
      "loginTime": "2026-05-14 14:57",
      "currentLoginDevice": false,
      "mobile": false
    }
  ]
}
```

| 字段 | 说明 |
|------|------|
| `configId` | 设备标识（格式：`{os}_{browser}_{timestamp}`） |
| `deviceName` | 设备名称 |
| `loginTime` | 登录时间 |
| `currentLoginDevice` | 是否当前设备 |
| `mobile` | 是否移动端 |
