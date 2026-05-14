# SYS_CARD_TODOTASKLIST — 待办任务列表

待办中心页面的完整任务列表。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/39995600956331534/SYS_CARD_TODOTASKLIST` |
| 鉴权 | Cookie |

## 响应

```json
{
  "errcode": "0",
  "errmsg": "请求成功",
  "data": {
    "bizScene": [],
    "config": {
      "showFilterOption": ["3", "1", "2", "4", "5"],
      "showSetTopButton": 0,
      "showIgnoreButton": 0,
      "showDelayButton": 0,
      "showSceneName": 1,
      "showAppName": 0,
      "showFavorite": "0",
      "sourceList": 1,
      "showDraftData": 0,
      "showTaskType": ["3", "1", "2", "4", "5"]
    }
  }
}
```
