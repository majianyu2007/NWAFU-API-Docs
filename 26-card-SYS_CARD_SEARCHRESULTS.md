# SYS_CARD_SEARCHRESULTS — 全局搜索结果

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/10713403191918569/SYS_CARD_SEARCHRESULTS` |
| 鉴权 | Cookie |

## 请求体

```json
{
  "cardId": "SYS_CARD_SEARCHRESULTS",
  "cardWid": "10713403191918569",
  "method": "renderData",
  "param": {
    "keyword": "成绩",
    "sortType": 1,
    "serviceSortType": 1,
    "agentSortType": 1,
    "serviceItemSortType": 1,
    "lang": "zh_CN",
    "platformType": 0
  }
}
```

## 响应结构

```json
{
  "data": {
    "keyword": "成绩",
    "searchData": {
      "serviceData": [{ ... }],
      "serviceItemData": [{ ... }],
      "newsData": [{ ... }],
      "serviceSize": 3,
      "serviceItemSize": 16,
      "newsSize": 1482,
      "groupFieldInfo": [
        {
          "groupType": 2, "groupEnabled": 1,
          "fieldConfig": [
            {"fieldName": "serviceName", "searchType": 1},
            {"fieldName": "serviceClassify", "searchType": 1},
            {"fieldName": "serviceDesc", "searchType": 1}
          ]
        },
        {
          "groupType": 3, "groupEnabled": 1,
          "fieldConfig": [{"fieldName": "ITEM_NAME", "searchType": 1}]
        },
        {
          "groupType": 4, "groupEnabled": 1,
          "fieldConfig": [
            {"fieldName": "title", "searchType": 1},
            {"fieldName": "contents", "searchType": 1}
          ]
        }
      ]
    }
  }
}
```

## groupType 含义

| groupType | 含义 | 对应数据 |
|-----------|------|---------|
| 2 | 在线服务 | `serviceData[]` |
| 3 | 服务事项 | `serviceItemData[]` |
| 4 | 资讯 | `newsData[]` |
