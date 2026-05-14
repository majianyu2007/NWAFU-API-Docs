# 图书馆书目检索系统 API（libopac.nwafu.edu.cn）

> 系统：汇文文献信息服务系统 (Libsys) V4.2.34
> CAS 登录 → `/space/login` → 选"统一身份认证登录" → `/space/reader/readerHome`

## 一、公开 API（无需登录）

### 搜索

| 端点 | 方法 | 说明 |
|------|------|------|
| `/meta-local/opac/search/extend3` | POST | 通过 ISBN/bibId 批量获取图书详情 |
| `/meta-local/opac/search/extend3?coversOnly=true` | POST | 仅获取封面 |

**请求体**：`{"isbns":["978-7-..."], "bibIds":["m..."]}`

**响应**：按 ID 分组返回每本书完整信息：
```json
{
  "m355d3541...": [{
    "_id": "7-307-03813-7",
    "title": "图书馆学基础教程",
    "authorIntroduction": "...",
    "catalog": "完整目录...",
    "content": "内容简介...",
    "imageUrl": "//img3m8.ddimg.cn/..."
  }]
}
```

### 热门

| 端点 | 方法 | 说明 |
|------|------|------|
| `/meta-local/opac/commend/hot1?count=20` | GET | 热门图书排行 |
| `/meta-local/opac/commend/dcp_hot_book?dcps=01&size=80` | GET | 按中图分类号热门 |
| `/meta-local/opac/commend/top_search_trend?count=10` | GET | 搜索趋势 |

热门图书返回字段：`bibId, title, author, publisher, pub_year, isbn, callno, rank, hotValue`

### 新书

| 端点 | 方法 | 说明 |
|------|------|------|
| `/meta-local/opac/new/books?page=1&pageSize=24` | GET | 新书通报（分页） |

### 配置

| 端点 | 方法 | 说明 |
|------|------|------|
| `/meta-local/opac/search/search_confs` | GET | 搜索配置 |
| `/meta-local/opac/sys/menu` | GET | 系统菜单 |
| `/meta-local/opac/classes/GBT13745/disciplines` | GET | 学科分类 |

---

## 二、读者 API（CAS 登录后）

### 读者主页 `/space/reader/readerHome`

| 端点 | 方法 | 说明 |
|------|------|------|
| `/meta-local/opac/users/loan_info` | GET | 借阅概况 "1 / 60" (当前/最大) |
| `/meta-local/opac/users/loan_dcp_dist` | GET | 借阅分类分布 |
| `/meta-local/opac/users/loan_range_dist` | GET | 借阅时间分布（按月） |
| `/meta-local/opac/users/export/loans` | POST | 导出当前借阅 |

### 侧边栏页面（前端路由，对应独立 API）

| 前端路由 | 功能 | 对应 API（推断） |
|---------|------|----------------|
| `/space/reader/lendList` | 当前借阅 | `users/current_loans` |
| `/space/reader/expiring` | 即将到期 | `users/expiring_loans` |
| `/space/reader/histList` | 借阅历史 | `users/loan_history` |
| `/space/reader/violation` | 滞纳金/违章 | `users/fines` |
| `/space/reader/request` | 我的请求 | `users/requests` |
| `/space/reader/shelf` | 我的书单 | `users/shelf` |
| `/space/reader/purchase` | 我的荐购 | `users/purchase` |
| `/space/reader/feedback` | 我的反馈 | `users/feedback` |
| `/space/reader/loanLoss` | 书刊遗失 | `users/lost_books` |
| `/space/reader/certificateInfo` | 证件信息 | `users/profile` |
| `/space/reader/searchHist` | 检索历史 | `users/search_history` |

### 续借

页面显示"续借"按钮，对应 API（推断）：

| 端点 | 方法 | 说明 |
|------|------|------|
| `/meta-local/opac/users/renew` | POST | 续借（参数：barcode） |

### 图书详情页

| 前端路由 | 示例 |
|---------|------|
| `/space/searchDetailLocal/{bibId}` | `/space/searchDetailLocal/me3f0b5c1ddda5d1bcf9e7d9559265d09` |

### 阅读功能

| 前端路由 | 功能 |
|---------|------|
| `/space/reading/readingList` | 阅读清单 |
| `/space/reading/readingCertificates` | 阅读证书 |

---

## 三、当前读者实测数据

| 字段 | 值 |
|------|-----|
| 姓名 | 张** |
| 院系 | 信息工程学院 |
| 证件状态 | 有效 |
| 当前借阅 | 1 本 (最大60) |
| 即将到期 | 0 |
| 滞纳金/违章 | 0 |
| 在借图书 | 《昨日世界:一个欧洲人的回忆》茨威格，应还 2026-06-26 |
| 馆藏地 | 总馆-北馆三层历史地理图书借阅区 |
| 借阅分类 | 历史、地理 (1本) |
| 借阅时间 | 2026年4月 |

---

## 四、学科分类（馆藏推荐）

哲学, 经济学, 法学, 教育学, 文学, 历史学, 理学, 工学, 农学, 医学, 管理学, 艺术学

每个分类的推荐图书通过 `dcp_hot_book?dcps={code}` 获取。
