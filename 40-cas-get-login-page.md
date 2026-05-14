# GET /authserver/login — CAS 登录页

获取 CAS 登录页面 HTML，含关键隐藏字段。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://authserver.nwafu.edu.cn/authserver/login` |
| URL (带 service) | `https://authserver.nwafu.edu.cn/authserver/login?service={urlEncoded}` |

## 页面关键字段

| 字段 | name/id | 说明 |
|------|---------|------|
| execution | `name="execution"` | 表单提交 token（每次请求唯一） |
| pwdEncryptSalt | `id="pwdEncryptSalt"` | AES 密码加密盐值 |

## 行为

- 无 TGC Cookie → 返回登录表单
- 无 service 有 TGC → 302 到 `/authserver/index.do`
- 带 service 有 TGC → 302 签发 ST 到 service URL
