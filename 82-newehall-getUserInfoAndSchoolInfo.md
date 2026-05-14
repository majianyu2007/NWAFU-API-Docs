# newehall: jsonp/ywtb/info/getUserInfoAndSchoolInfo.json — 用户+学校信息

获取当前用户详细信息及学校信息。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/info/getUserInfoAndSchoolInfo.json?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 响应

```json
{
  "result": "success",
  "data": {
    "userId": "2024012001",
    "userName": "张三",
    "userType": "1",
    "userTypeName": "学生",
    "userDepartment": "2025",
    "userSex": "男",
    "hasYwtbManagePermission": false,
    "hasAppManagePermission": false,
    "hasLogin": true,
    "userPlanList": [
      {
        "wid": "a5c9784e-6e5d-40ba-9ba8-e3ff4d696c88",
        "userId": "2024012001",
        "planId": "39baa7f3-bd33-47be-925d-9b6f0d794555",
        "pageCode": "Lite_home"
      }
    ]
  }
}
```

| 字段 | 说明 |
|------|------|
| `userType` | 用户类型（1=学生） |
| `userTypeName` | 类型名称 |
| `userDepartment` | 年级 |
| `userSex` | 性别 |
| `userPlanList` | 用户自定义页面方案列表 |
