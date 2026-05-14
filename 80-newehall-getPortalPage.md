# newehall: jsonp/ywtb/home/getPortalPage — 门户页面列表

获取旧版门户所有页面配置（首页、办事大厅、任务中心、工作台、直通车、资讯中心）。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/home/getPortalPage?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 响应

```json
{
  "result": "success",
  "data": [
    {
      "pageId": "lite_23",
      "pageCode": "Lite_zxzx",
      "pageName": "资讯中心",
      "pageUrl": "/information_center",
      "pageType": 0,
      "homePage": 0,
      "sort": 1,
      "moduleCode": "Lite"
    },
    {
      "pageId": "lite_19",
      "pageCode": "Lite_home",
      "pageName": "任务中心",
      "pageUrl": "/home/Lite_home",
      "homePage": 0,
      "sort": 2
    },
    {
      "pageId": "lite_20",
      "pageCode": "Lite_hall",
      "pageName": "办事大厅",
      "pageUrl": "/cusHall",
      "homePage": 1,
      "sort": 3
    }
  ]
}
```

| 字段 | 说明 |
|------|------|
| `pageCode` | 页面代码（用于 API 参数） |
| `pageUrl` | Hash 路由路径 |
| `homePage` | 是否首页（1=是） |
