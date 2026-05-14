# SYS_CARD_TODOTASK — 待办任务

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/{cardWid}/SYS_CARD_TODOTASK` |
| 鉴权 | Cookie |

## cardWid（按页面）

| 页面 | cardWid |
|------|---------|
| 首页 | `762026031326434` |
| 工作台 | `3636958789019812` |

## 请求体

```json
{"cardId":"SYS_CARD_TODOTASK","cardWid":"762026031326434","method":"renderData","param":{},"n":"随机数"}
```

## 响应

```json
{"errcode": "0", "errmsg": "请求成功", "data": 0}
```

`data` 为待办任务数量。
