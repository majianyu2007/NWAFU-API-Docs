# SYS_CARD_RECOMMENDSERVICEITEMS — 推荐服务事项

办事大厅页面的推荐服务列表。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/8895351584007501/SYS_CARD_RECOMMENDSERVICEITEMS` |
| 鉴权 | Cookie |

## 响应 serviceItemsInfo[] 字段

| 字段 | 说明 |
|------|------|
| `itemWid` | 事项 UUID |
| `itemNumber` | 事项编号 |
| `itemName` | 事项名称 |
| `itemPinYin` | 拼音 |
| `visitCount` | 访问量 |
| `itemCategory` | 分类名称 |
| `itemDept` | 责任部门 |
| `score` | 评分 |
| `workGuide` | 是否有办事指南 |
| `onlineServiceType` | 在线服务类型（0=无, 1=仅线上, 2=可在线办理） |
| `serviceRecommendRating` | 推荐评分（算法排序依据） |
| `serviceList[]` | 关联的在线服务 wid |
| `roleName` | 适用角色 |
