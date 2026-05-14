# personalInfo/accountSecurity/accountSetting — 账号安全设置

获取账号安全信息（密码强度、手机号、邮箱绑定状态等）。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/accountSecurity/accountSetting` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": {
    "id": "2024012001",
    "userid": "2024012001",
    "alias": "",
    "isEmailValidated": "0",
    "securityEmail": "",
    "isPhoneValidated": "1",
    "telephoneNumber": "138****8888",
    "isMobileEdit": true,
    "isAliasEdit": true,
    "viewWidgets": "PLACEHOLDER,PWD,ALIAS,MOBILE,EMAIL",
    "pwdEncryptSaltModifyPwd": "bU5f1pOVYFLbh7P6"
  }
}
```

| 字段 | 说明 |
|------|------|
| `alias` | 登录别名 |
| `isEmailValidated` | 邮箱是否已验证 |
| `isPhoneValidated` | 手机是否已验证 |
| `telephoneNumber` | 手机号（脱敏） |
| `pwdEncryptSaltModifyPwd` | 修改密码用的加密盐 |
