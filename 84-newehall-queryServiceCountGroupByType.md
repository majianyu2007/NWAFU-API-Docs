# newehall: jsonp/ywtb/queryServiceCountGroupByType — 服务分类统计

按用户类型查询各分类下的服务数量。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/queryServiceCountGroupByType?userType=1&queryType=1&maxItems=7&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 参数

| 参数 | 说明 |
|------|------|
| `userType` | 用户类型（0/1，1=学生） |
| `queryType` | 查询类型 |
| `maxItems` | 最大返回项 |

## 响应

```json
{
  "result": "success",
  "data": [
    {
      "typeId": "eae2b314-f5ba-4255-9895-8205a5889f7d",
      "typeName": "游客访问",
      "iconUrl": "http://newehall.nwafu.edu.cn/ywtb-manage/icons/theme/icons012.png",
      "serviceCount": 4,
      "serviceName": ["网上确认", "考研报名", "研究生初试成绩复核", "..."],
      "sort": 2
    }
  ]
}
```
