# 消息中心 API（newehall.nwafu.edu.cn）

> 页面：`/new/portal/html/message/scenes_message_center.html`
> 路径前缀：`/jsonp/`

## API 列表

| 端点 | 方法 | 说明 |
|------|------|------|
| `/jsonp/userInfo.json` | GET | 消息中心用户信息 |
| `/jsonp/getUserTags` | GET | 用户标签分类（含 `allUnReadSum`, `typeList[]`） |
| `/jsonp/getTagsMessages?typeId=&size=20&start=0&typeName=` | GET | 分页获取消息列表 |

## getTagsMessages 参数

| 参数 | 说明 |
|------|------|
| `typeId` | 消息类型 ID（空=全部） |
| `size` | 每页条数 |
| `start` | 偏移量 |
| `typeName` | 类型名称 |

## 响应示例

```json
{
  "result": "success",
  "data": {
    "count": 0,
    "children": [],
    "type": "",
    "typeId": -1
  }
}
```
