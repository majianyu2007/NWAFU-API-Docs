# newehall: jsonp/ywtb/card/getView + getViewDataDetail — 卡片视图

门户卡片视图配置和数据获取。

## getView — 获取卡片视图配置

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/card/getView?_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

返回页面所有卡片区域的 wid 列表。

## getViewDataDetail — 获取卡片数据

| 属性 | 值 |
|------|-----|
| 方法 | `GET` (JSONP) |
| URL | `https://newehall.nwafu.edu.cn/jsonp/ywtb/card/getViewDataDetail?wid={cardWid}&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

根据 `getView` 返回的 wid 获取每个卡片的具体数据内容。
