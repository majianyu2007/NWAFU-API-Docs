# SYS_CARD_RECOMMENDAPP — 推荐应用

工作台/直通车页面的推荐应用列表。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/25448223298112294/SYS_CARD_RECOMMENDAPP` |
| 鉴权 | Cookie |

## 响应

```json
{
  "data": {
    "recommendAppList": [
      {
        "serviceId": "7506770411202346",
        "serviceName": "校园网邮箱自助申请",
        "iconLink": "https://ehall.nwafu.edu.cn/oss/iconLab/...",
        "pcAccessUrl": "https://emailapply.nwafu.edu.cn/",
        "favorite": false,
        "permission": true,
        "classifyInfos": [{"classifyName": "公共服务", "sortNum": 2}],
        "serviceDesc": "个人校内邮箱申请"
      }
    ],
    "config": {
      "isShowAllService": 1,
      "columns": 5,
      "allServiceUrl": "/index.html#/apps",
      "autoRecommendRange": {"autoRecommend": "0", "autoRecommendCount": 20}
    }
  }
}
```
