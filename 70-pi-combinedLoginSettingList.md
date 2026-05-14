# personalInfo/accountRelation/combinedLoginSettingList — 联合登录设置

获取第三方账号绑定（微信等）设置。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://authserver.nwafu.edu.cn/personalInfo/accountRelation/combinedLoginSettingList` |
| 响应格式 | `code`/`message`/`datas` |

## 响应

```json
{
  "code": "0",
  "datas": {
    "prefix": "https://authserver.nwafu.edu.cn/authserver/",
    "combinedTypes": "weixin",
    "showBindTypes": "weixin",
    "bindCombinedList": [],
    "bindWeiXinList": [],
    "bindUserCombinedList": []
  }
}
```
