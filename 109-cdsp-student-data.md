# 学生数据平台 API（cdsp.nwafu.edu.cn）

> 系统：数据采集与分析平台 (CDSP)
> 路径前缀：`/cdsp/portalEngine/`
> 含：本科画像 + 硕博画像

## 认证

通过 CAS SSO，URL 加 `?isCasLogin=1`。

## API 列表

| 端点 | 方法 | 说明 |
|------|------|------|
| `/cdsp/cas/isLogin` | GET | CAS 登录状态检查 |
| `/cdsp/portalEngine/getLoginUser` | GET | 用户信息（deptId, deptName, userAccount） |
| `/cdsp/portalEngine/getUserPermissionRouters` | GET | 权限路由 |
| `/cdsp/portalEngine/base/getPortalConfig` | POST | 门户配置 |
| `/cdsp/portalEngine/pageelement/list` | POST | 页面元素数据（核心，含所有展示字段的 fieldKey/value） |
| `/cdsp/portalEngine/getPageView` | GET | 页面埋点 |

## 学生数据页

URL: `https://cdsp.nwafu.edu.cn/cdsp/site/studentdata/index.html#/Mydata?isCasLogin=1`

`pageelement/list` 返回所有展示字段的 key-value，包含：
- `collectProductName` - 数据采集系统
- `consoleProductName` - 学生画像平台
- `portalSchoolIcon` - 学校图标
- 各数据域 fieldKey/value

## 研究生数据页

URL: `https://cdsp.nwafu.edu.cn/cdsp/site/Graduatedata/index.html#/myData?isCasLogin=1`
