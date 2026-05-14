# CUS_CARD_NWSUAF_PERSONALDATA — 个人数据卡片

用户个人信息卡片。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/7411305194072212/CUS_CARD_NWSUAF_PERSONALDATA` |
| 鉴权 | Cookie |

## 响应

```json
{
  "data": {
    "serviceCarHeight": {"type": 0, "value": 500},
    "personalInfo": {
      "infoList": [0, 1, 2],
      "dataSource": "",
      "isDisplay": 0
    },
    "isHiddenPrivacy": 0,
    "showBindMail": 1,
    "columns": "1",
    "personalDatas": ["1364146375118934016"],
    "showSubscribe": 0
  }
}
```
