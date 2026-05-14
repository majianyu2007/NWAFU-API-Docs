# minos-stata/collect/collectData

数据埋点统计上报。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://ehall.nwafu.edu.cn/minos-stata/collect/collectData` |
| 鉴权 | Cookie |

## 说明

此接口用于上报用户行为数据到 Minos 统计分析平台。上报地址来自 `getLoginUserAndGuest` 响应中的 `stataAddress` 字段。
