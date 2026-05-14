# 正版软件平台 API（software.nwafu.edu.cn）

> 系统：慧云正版软件管理平台
> 路径前缀：`/prod-api/`

## 认证

通过 CAS ST ticket 登录（URL 中带 `ticket=ST-...`）。

## API 列表

| 端点 | 方法 | 说明 |
|------|------|------|
| `/prod-api/sso/getUserInfo` | POST | 用户信息（CAS登录后） |
| `/prod-api/index/info` | GET | 首页信息 |
| `/prod-api/index/logo` | GET | Logo 配置 |
| `/prod-api/index/recommendSoftwares` | GET | 推荐软件列表 |
| `/prod-api/index/indexModels` | GET | 首页模块 |
| `/prod-api/index/double/softwareTypes` | GET | 软件分类 |
| `/prod-api/index/banners` | GET | 横幅 |

## 下载 API

```
GET /prod-api/download/{softwareId}/{userId}/{downloadType}
```

示例：`/prod-api/download/348/39196/0`

## 已知软件

| 软件 | 下载量 |
|------|--------|
| Office 2021 64位 | 34,724 |
| Windows 11 64位 | 15,414 |
| Office 2019 | 12,601 |
| Office 2024 | 12,426 |
| Windows 10 | 9,454 |
| Visio 2021 | 8,165 |
| Office 2016 | 5,143 |
| Office修复工具 | 4,517 |
| Office 2021 32位 | 4,383 |
| Office卸载工具 | 3,615 |
