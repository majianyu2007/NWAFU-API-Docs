# getUserPermissionRouters

获取用户权限路由，决定导航菜单的可见性。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://ehall.nwafu.edu.cn/getUserPermissionRouters?_t={timestamp}&langCountry=zh_CN` |
| 鉴权 | Cookie |

## 响应字段

| 字段 | 说明 |
|------|------|
| `wid` | 方案 ID |
| `siteName` | 方案名称 |
| `siteRoute` | 路由标识 |
| `languageKey` | 多语言 key |
| `isMaster` | 是否主方案 |
| `orderIndex` | 排序 |

## 示例响应

```json
{
  "errcode": "0",
  "errmsg": "success",
  "data": [
    {
      "wid": "-100",
      "siteName": "默认展示方案",
      "siteRoute": "default",
      "languageKey": "1224380996762206208",
      "isMaster": 1,
      "orderIndex": 1
    }
  ]
}
```
