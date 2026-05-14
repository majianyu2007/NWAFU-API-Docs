# base/getPortalConfig

获取门户配置项。首页会多次调用此接口。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/base/getPortalConfig` |
| 鉴权 | Cookie |

## 示例响应

```json
{
  "errcode": "0",
  "errmsg": "请求成功",
  "data": {
    "wid": null,
    "configKey": "casp_ioc_domin",
    "configValue": null,
    "defaultValue": null,
    "configDesc": null
  }
}
```
