# newehall: jsonp/ywtb/home/getPortalInfoNew — 页面布局

获取指定页面的卡片布局配置。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/home/getPortalInfoNew?pageCode=Lite_home&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 参数

| 参数 | 说明 |
|------|------|
| `pageCode` | 页面代码，如 `Lite_home`、`Lite_hall`、`Lite_ztc`、`Lite_zxzx` |

## 响应

```json
{
  "result": "success",
  "data": {
    "displayPlan": {
      "planId": "39baa7f3-bd33-47be-925d-9b6f0d794555",
      "planName": "任务中心",
      "imageUrl": "/ywtb-manage/img/header/banner_lite.png",
      "pageCode": "Lite_home"
    },
    "displayCards": [
      {
        "wid": "fb894d58-1976-4e21-b34c-78462e322bec",
        "width": 2,
        "height": 2,
        "xPlace": 0,
        "yPlace": 0,
        "cards": [
          {"cardId": "sys_dblyfl_pc_2_2_1", "displayName": "待办任务", "sort": 0},
          {"cardId": "sys_yblyfl_pc_2_2_1", "displayName": "已办任务", "sort": 1},
          {"cardId": "sys_wfqdlyfl_pc_2_2_1", "displayName": "我发起", "sort": 2}
        ]
      }
    ]
  }
}
```
