# getLoginUserAndGuest

获取登录用户及访客完整信息。比 `getLoginUser` 多包含 `interKey`、`stataAddress`、`bindUserList` 等字段。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://ehall.nwafu.edu.cn/getLoginUserAndGuest?_t={timestamp}` |
| 鉴权 | Cookie |

## 相比 getLoginUser 的额外字段

| 字段 | 说明 |
|------|------|
| `interKey` | 内部密钥（用于统计上报） |
| `stataAddress` | 统计上报地址 |
| `bindUserList` | 绑定的用户列表 |
| `switchAccountPage` | 是否可切换账号 |
| `portalDefaultLang` | 门户默认语言 |
| `isUserSwitchLang` | 用户是否可切换语言 |
| `idsUserType` | IDS 用户类型 |
| `headImageIcon` | 头像图标 |
| `defaultUserAvatar` | 默认头像 |

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
    "onlineUserCount": 3504,
    "interKey": "b79f5b4f0b18aeb963ab2e8931b6056f",
    "stataAddress": "https://ehall.nwafu.edu.cn/minos-stata",
    "portalDomain": "https://ehall.nwafu.edu.cn",
    "isParticipateInRecommend": 1,
    "isProvideDataAnalysis": 1,
    "allParentOrgIncludeSelf": ["category_20000", "737368636162834432", "1503070508679041024"]
  }
}
```

## 建议

这是获取用户信息最完整的接口，推荐优先使用。
