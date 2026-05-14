# SYS_CARD_SERVICEITEMCOUNT — 服务事项统计

办事大厅顶部的统计数据卡片。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/7248912938469971/SYS_CARD_SERVICEITEMCOUNT` |
| 鉴权 | Cookie |

## 响应

```json
{
  "data": {
    "columns": 5,
    "serviceItemList": [
      {"dataId": "currentItem",  "dataName": [{"langValue": "当前进驻事项"}], "count": "387"},
      {"dataId": "onlineItem",   "dataName": [{"langValue": "可在线办理事项"}], "count": "198"},
      {"dataId": "currentCount", "dataName": [{"langValue": "当前正在办件"}], "count": "8412"},
      {"dataId": "doneCount",    "dataName": [{"langValue": "已完成办件"}], "count": "131824"},
      {"dataId": "allCount",     "dataName": [{"langValue": "总办件数量"}], "count": "140236"}
    ]
  }
}
```
