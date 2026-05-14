# SYS_CARD_RECUSEAPP — 最近使用服务

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/execCardMethod/{cardWid}/SYS_CARD_RECUSEAPP` |
| 鉴权 | Cookie |

## cardWid

| 页面 | cardWid |
|------|---------|
| 首页 | `680345040648209` |
| 工作台 | `10099085702774024` |

## 响应 data.appList[] 字段

| 字段 | 说明 |
|------|------|
| `serviceId` | 服务 ID |
| `serviceWid` | 服务 WID |
| `serviceName` | 服务名称 |
| `iconLink` | 图标 URL（带 OSS sign） |
| `pcAccessUrl` | PC 访问 URL |
| `mobileAccessUrl` | 移动端 URL |
| `useTime` | 最近使用时间 |
| `favorite` | 是否收藏 |
| `permission` | 是否有权限 |
| `classifyInfos[]` | 分类信息（`classifyName`、`sortNum`） |
