# personalInfo/accountSecurity/accountSetting — 账号安全设置（重复调用）

此接口在个人中心多处被调用，返回基础设置、三方账号、关联账号、生物识别、安全令牌、可信设备等子模块的配置。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/accountSecurity/accountSetting` |
| 响应格式 | `code`/`message`/`datas` |

## 与 68-pi-accountSetting 的关系

两个文档指向同一接口，68 侧重于密码/手机/邮箱字段，本页强调该接口在多个 Tab 中被重复调用的特性。

| Tab | datas 侧重 |
|-----|-----------|
| 基础设置 | `viewWidgets: "PLACEHOLDER,PWD,ALIAS,MOBILE,EMAIL"` |
| 三方账号 | 联合登录绑定 |
| 关联账号 | bindingUserList |
| 生物识别 | 生物识别设置 |
| 安全令牌 | OTP 令牌绑定 |
| 可信设备 | 设备列表 |
