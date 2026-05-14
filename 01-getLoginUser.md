# getLoginUser

获取当前登录用户的基本信息。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://ehall.nwafu.edu.cn/getLoginUser?_t={timestamp}` |
| 鉴权 | Cookie（`__Secure-Login-State-cas`） |
| 响应格式 | `errcode`/`errmsg`/`data` |

## 响应字段

| 字段 | 类型 | 说明 |
|------|------|------|
| `wid` | string | 用户全局唯一 ID |
| `personWid` | string | 人员 WID |
| `userAccount` | string | 学号/工号 |
| `userName` | string | 中文姓名 |
| `categoryWid` | string | 身份分类 ID |
| `categoryName` | string | 身份分类（学生/本科生） |
| `deptName` | string | 院系全路径 |
| `enterSchoolDate` | string | 入学年份 |
| `sexCode` | string | 性别（0=未设置） |
| `phone` | string | 手机号（脱敏） |
| `email` | string\|null | 邮箱 |
| `orgs[]` | array | 所属组织列表 |
| `groups[]` | array | 用户组列表 |
| `onlineUserCount` | int | 当前在线人数 |
| `allParentOrgIncludeSelf` | array | 组织层级链 |

## 示例响应

```json
{
  "errcode": "0",
  "errmsg": "请求成功",
  "data": {
    "wid": "1403876744639791104",
    "userAccount": "2024012001",
    "userName": "张三",
    "categoryName": "学生/本科生",
    "deptName": "学生/信息工程学院/2025",
    "enterSchoolDate": "2025",
    "sexCode": "0",
    "onlineUserCount": 3504
  }
}
```
