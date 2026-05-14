# newehall: jsonp/ywtb/card/recUseServiceList — 最近使用服务（全应用目录）

获取用户最近使用/收藏的服务列表。这是**最重要的应用目录 API**，包含所有应用的完整元数据。

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/card/recUseServiceList?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

## 响应 appList 字段（每个应用）

| 字段 | 说明 |
|------|------|
| `appId` | 应用 ID |
| `appName` | 应用名称 |
| `appKey` | `{appId}-{version}` |
| `deployPrefix` | 部署前缀（如 `https://newehall.nwafu.edu.cn/jwapp`） |
| `appPc.entranceUrl` | PC 入口 URL |
| `appMobile.entranceUrl` | 移动端入口 URL |
| `middleIcon` | 图标 URL |
| `pcOpenUrl` | 最终 PC 打开 URL |
| `mobileAppOpenUrl` | 最终移动端 URL |
| `pcApp` / `mobileApp` | 是否有 PC/移动版 |
| `accessAuth` | 访问权限（1=可访问, 2=受限） |
| `viewAuth` | 查看权限 |
| `hasPermission` | 是否有权限 |
| `favorite` | 是否收藏 |
| `favoriteCount` | 收藏数 |
| `useCount` | 使用次数 |
| `appPV` | 页面访问量 |
| `categoryList` | 分类列表 |
| `authUrl` | 鉴权 URL（受限应用需要走此 URL 鉴权） |
| `appShortName` | 应用短名（用于 sys 路径） |
| `version` | 版本号 |
| `opening` / `maintaining` | 是否开放/维护中 |

## 关键发现

- 返回 **所有有权限的应用**（不限最近使用）
- `pcOpenUrl` 是实际可访问的 URL
- `authUrl` 用于需要额外鉴权的应用（如网上评教、学籍异动等）
