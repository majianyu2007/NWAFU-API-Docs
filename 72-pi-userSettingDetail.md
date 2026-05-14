# personalInfo/accountRelation/userSettingDetail — 用户设置详情

获取认证策略设置（异地登录提醒、二次验证等）。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/accountRelation/userSettingDetail` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": {
    "reAuthTypes": [],
    "reAuthEnabled": true,
    "isShowOneLogin": true,
    "isShowOutsideSchoolLogin": true,
    "outsideSchoolLoginNotify": true,
    "authserverAppList": [],
    "requiredAuthserverAppList": [
      {"id": "823596576143310848", "name": "科研系统"},
      {"id": "1195049987727986688", "name": "数据门户"},
      {"id": "1314304862126780416", "name": "帆软报表"}
    ],
    "remoteLoginEnabled": true,
    "remoteLoginCommonPlace": "当前常用地：陕西省咸阳市、陕西省西安市、陕西省延安市",
    "remoteLoginNotice": "您的账号在异地登录时会进行消息提醒，提醒方式为邮箱",
    "remoteLoginNoticeEnabled": true,
    "resultMap": {"pwNotify": "false", "oneLogin": "false"}
  }
}
```

| 字段 | 说明 |
|------|------|
| `reAuthEnabled` | 是否启用二次验证 |
| `remoteLoginEnabled` | 是否启用异地登录提醒 |
| `remoteLoginCommonPlace` | 常用登录地 |
| `remoteLoginNotice` | 提醒方式说明 |
| `requiredAuthserverAppList` | 需要二次验证的应用列表 |
