# personalInfo/common/getMenuRole — 菜单角色

获取个人中心侧边栏的可见菜单项。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/common/getMenuRole` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": "PLACEHOLDER,accountSetting,combinedLogin,bindingUser,biometrics,otpToken,multiFactorAuth"
}
```

`datas` 是逗号分隔的菜单 key 列表，决定侧边栏显示哪些功能入口。
