# personalInfo/accountRelation/bindingUserList — 关联账号列表

获取绑定的多身份账号。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/accountRelation/bindingUserList` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "message": "接口调用成功",
  "bindingUserList": [
    {
      "userId": "2024012001",
      "defaultFlag": 1,
      "createTime": "2025-08-09 23:07:42",
      "activeFlag": 0,
      "redirectUrl": "https://authserver.nwafu.edu.cn/authserver/switchByCode?switchCode=...",
      "categoryName": "学生/本科生",
      "accountStatus": "账号正常"
    }
  ],
  "showPrompt": false
}
```

| 字段 | 说明 |
|------|------|
| `defaultFlag` | 是否默认账号（1=是） |
| `redirectUrl` | 切换到该账号的 URL（含 switchCode） |
| `accountStatus` | 账号状态 |
