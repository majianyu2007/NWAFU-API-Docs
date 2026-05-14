# personalInfo/UserData/user/queryUserData — 查询用户数据

获取个人资料数据。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/UserData/user/queryUserData?t={unix_timestamp}` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": {
    "birthday": null,
    "uploadFace": false,
    "facePicIcon": "",
    "userAttrEditAttrs": ["password", "birthday", "securityEmail", "telephoneNumber"],
    "nickName": null,
    "headImageIcon": null
  }
}
```
