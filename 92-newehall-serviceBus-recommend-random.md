# newehall: 其他服务 API

## getServiceBusAppList — 服务总线应用列表

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/card/getServiceBusAppList?cardId=6088657540236238&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

返回指定卡片下关联的应用列表。

---

## getRecommendService — 推荐服务

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/card/getRecommendService?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

---

## getRandomServiceName — 随机服务名称

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/getRandomServiceName` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

返回一个随机服务名称（用于首页展示）。

---

## rightSideDatas — 右侧栏数据

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/rightSideDatas?flag=1&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

---

## serviceAnalysis — 服务分析数据

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/serviceAnalysis?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |
