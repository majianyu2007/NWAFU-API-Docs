# CUS_CARD_NWSUAF_SERVICEBUS — 服务总线（工作台带分类）

工作台页面的服务总线卡片，相比直通车的版本多了分类标签。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/10719428818576493/CUS_CARD_NWSUAF_SERVICEBUS` |
| 鉴权 | Cookie |

## 响应

```json
{
  "data": {
    "showAllTab": 1,
    "classifyData": [
      {"typeId": "1412872828024242177", "typeName": "招生管理", "show": true, "count": 2},
      {"typeId": "1412881721524518913", "typeName": "选课管理", "show": true, "count": 1},
      {"typeId": "1416726467495051265", "typeName": "学位申请", "show": true, "count": 1}
    ],
    "columns": 4,
    "hasChildClassify": true,
    "tabPosition": "1",
    "appData": [
      {
        "typeId": "1412872828024242177",
        "appId": "1414579286003134464",
        "appName": "推免资格申请管理",
        "pcAccessUrl": "https://newehall.nwafu.edu.cn/gsapp/sys/tmzgsqglappnwsuaf/*default/index.do"
      }
    ]
  }
}
```
