# NWAFU 本科生 App API 参考手册

> 西北农林科技大学全信息系统 API 逆向 | 2026-05-14
> 账号：张三 2024012001 信息工程学院 2025级

---

## 系统全景

```
                    ┌──────────────────────┐
                    │   CAS AuthServer     │
                    │   (一个TGC通全部)     │
                    └──────┬───────────────┘
           ┌───────────────┼───────────────────────┐
           ▼               ▼                       ▼
    ┌──────────┐   ┌──────────────┐    ┌──────────────────┐
    │  ehall   │   │   newehall   │    │  独立业务系统     │
    │  新版门户 │   │   旧版门户    │    │  (15+ 个)        │
    │ execCard  │   │ jsonp/*      │    │ spark,deepseek,  │
    │ Method    │   │ taskcenter   │    │ pan,repair,mail  │
    └──────────┘   └──────────────┘    │ software,libopac │
           │               │           │ minos,cdsp...    │
           └───────┬───────┘           └──────────────────┘
                   ▼
    ┌──────────────────────────────┐
    │    Minos 子应用平台           │
    │    jwapp / gsapp / apps      │
    │    (getAppConfig 可通)       │
    └──────────────────────────────┘
```

---

## 本科生常用功能速查

### 日程课表

- **课表订阅列表** — ehall CUS_CARD_NWSUAF_CALENDAR `getPermissionCal` ✅
- **课表数据** — ehall 日历卡（页面渲染）⚠️ data=null
- **Minos 查询日程** — `assistant/getAssistantBusiness?businessType=schedule` ✅
- **Minos 创建日程** — AI 工具 "创建个人日程" ✅

📄 [91-newehall-taskcenter-apis.md](91-newehall-taskcenter-apis.md) | [110-minos-ai-assistant.md](110-minos-ai-assistant.md)

### 待办事项

- **待办/已办计数** — newehall `getTaskTodoAndDoneCount.do` ✅
- **待办列表(分页)** — newehall `getTaskRestful.do` POST ✅
- **流程统计** — newehall `getMyProcessCount.do` ✅
- **Minos AI查待办** — AI 工具 "查询待办任务" ✅

📄 [91-newehall-taskcenter-apis.md](91-newehall-taskcenter-apis.md)

### 图书馆

- **图书检索** — `libopac.nwafu.edu.cn/meta-local/opac/search/extend3` POST ✅
- **新书列表** — `/meta-local/opac/new/books?page=1&pageSize=24` ✅
- **热门图书** — `/meta-local/opac/commend/hot1?count=20` ✅
- **当前借阅** — `/meta-local/opac/users/loan_info` GET ✅
- **续借** — `/meta-local/opac/users/renew` POST ✅
- **借阅历史** — `/space/reader/histList` ✅
- **滞纳金/违章** — `/space/reader/violation` ✅
- **馆藏推荐** — 12 学科分类（哲学～艺术学）✅

📄 [107-library-opac.md](107-library-opac.md)

### 报修

- **维修分类** — `repair/.../public/scenes/list.do` (10 类) ✅
- **楼栋列表** — `.../public/userareasitelist.do` (150+ 楼栋) ✅
- **维修项目** — `.../public/usertypeitemlist.do` (70+ 项) ✅
- **我的工单** — `.../dispose/mybill.do` (分页) ✅

📄 [102-repair-system-apis.md](102-repair-system-apis.md)

### AI 助手

- **DeepSeek 对话** — `deepseek.nwafu.edu.cn/api/chat/completions` (OpenAI 兼容) ✅
- **可用模型** — Qwen3-235B, Qwen3-32B, Kimi-K2.6, Qwen3.6-27B ✅
- **AI 辅导员** — `minos.nwafu.edu.cn/assistant/completions` SSE 流式 ✅
- **10 个 AI 工具** — 查待办/日程/离校/证明/天气等 ✅
- **智能体平台** — `spark.nwafu.edu.cn/agent/proxyApi/` ✅

📄 [104-deepseek-openwebui.md](104-deepseek-openwebui.md) | [110-minos-ai-assistant.md](110-minos-ai-assistant.md) | [103-spark-agent-platform.md](103-spark-agent-platform.md)

### 云盘

- **主页数据** — `pan.nwafu.edu.cn/poseidon/main_page/data` ✅
- **未读消息** — 7 条 ✅
- **知识库** — `aiapi/zsh/knowledgeGpt/list_square` ✅

📄 [105-yunpan-360fangcloud.md](105-yunpan-360fangcloud.md)

### 正版软件

- **软件列表** — `software.nwafu.edu.cn/prod-api/index/recommendSoftwares` ✅
- **软件下载** — `prod-api/download/{id}/{uid}/{type}` ✅
- Office 2024/2021/2019/2016, Windows 11/10, Visio, MATLAB, WPS, 中望CAD

📄 [106-software-platform.md](106-software-platform.md)

### 个人画像

- **本科画像** — `cdsp.nwafu.edu.cn/cdsp/portalEngine/pageelement/list` ✅
- **用户信息** — `cdsp.nwafu.edu.cn/cdsp/portalEngine/getLoginUser` ✅

📄 [109-cdsp-student-data.md](109-cdsp-student-data.md)

### 消息通知

- **消息分类** — `newehall/jsonp/getUserTags` ✅
- **消息列表** — `newehall/jsonp/getTagsMessages` (分页) ✅

📄 [111-message-center.md](111-message-center.md)

### 用户中心

- **个人信息** — ehall `getLoginUserAndGuest` ✅
- **账号安全** — authserver `accountSecurity/accountSetting` ✅
- **登录历史** — authserver `UserOnline/user/queryUserOnline` ✅
- **设备管理** — authserver `common/unTrustDeviceNotify` ✅
- **OTP 令牌** — authserver `otpToken/isBind` ✅

### 办事大厅服务目录

| 视图 | 分类数 | 事项数 |
|------|--------|--------|
| 学生办事 | 7 | 118 |
| 教师办事 | 7 | 89 |
| 游客办事 | 1 | 4 |
| 按部门 | 7 | 41 |

📄 [108-service-catalog-complete.md](108-service-catalog-complete.md)

### 受限功能（需特定权限开放）

| 功能 | 应用 | 原因 |
|------|------|------|
| 成绩查询 | jwapp/cjcx | 403 |
| 成绩认定 | jwapp/cjrd | 403 |
| 中英文成绩单 | jwapp/zywcjd | 403 |
| 学籍异动 | jwapp/xjydyy | 403 |
| 大类专业分流 | jwapp/dlzyfl | 403 |
| 本研互选 | jwapp/byhx | 403 |
| 网上评教 | jwapp/jwwspj | 403 |
| 大模型训练平台 | huoshi | 讯飞 UAP SSO |

---

## 登录方式

- **FIDO2 Passkey** — `wisedu_cas` auth_method="fido2" ✅ 推荐
- **密码 + TOTP** — `wisedu_cas` ✅
- **微信联合登录** — authserver `combinedLoginSettingList` ✅

---

## 文档索引

### ehall 门户层：01–15 认证与配置 · 20–36 卡片系统

| 编号 | 文档 |
|------|------|
| 01 | [getLoginUser](01-getLoginUser.md) |
| 02 | [getLoginUserAndGuest](02-getLoginUserAndGuest.md) |
| 03 | [getUserPermissionRouters](03-getUserPermissionRouters.md) |
| 04 | [queryUserSiteWitching](04-queryUserSiteWitching.md) |
| 05 | [getPageView](05-getPageView.md) |
| 06 | [queryI18nList](06-queryI18nList.md) |
| 07 | [language/getStaticData](07-language-getStaticData.md) |
| 08 | [common/getProgrammeLocalStyle](08-common-getProgrammeLocalStyle.md) |
| 09 | [base/getPortalConfig](09-base-getPortalConfig.md) |
| 10 | [programme/queryPopupWindowDisplay](10-programme-queryPopupWindowDisplay.md) |
| 11 | [common/clientIp](11-common-clientIp.md) |
| 12 | [minos-stata/collectData](12-minos-stata-collectData.md) |
| 13 | [getSearchHisVal](13-getSearchHisVal.md) |
| 14 | [getPlaceholderVal](14-getPlaceholderVal.md) |
| 15 | [getSidebarCount](15-getSidebarCount.md) |
| 20 | [SYS_CARD_TODOTASK](20-card-SYS_CARD_TODOTASK.md) |
| 21 | [SYS_CARD_DONETASK](21-card-SYS_CARD_DONETASK.md) |
| 22 | [SYS_CARD_MYTASK](22-card-SYS_CARD_MYTASK.md) |
| 23 | [SYS_CARD_TODOTASKLIST](23-card-SYS_CARD_TODOTASKLIST.md) |
| 24 | [SYS_CARD_RECUSEAPP](24-card-SYS_CARD_RECUSEAPP.md) |
| 25 | [SYS_CARD_NEWSANNOUNCEMENT](25-card-SYS_CARD_NEWSANNOUNCEMENT.md) |
| 26 | [SYS_CARD_SEARCHRESULTS](26-card-SYS_CARD_SEARCHRESULTS.md) |
| 27 | [SYS_CARD_RECOMMENDSERVICEITEMS](27-card-SYS_CARD_RECOMMENDSERVICEITEMS.md) |
| 28 | [SYS_CARD_SERVICEITEMCOUNT](28-card-SYS_CARD_SERVICEITEMCOUNT.md) |
| 29 | [SYS_CARD_RECOMMENDAPP](29-card-SYS_CARD_RECOMMENDAPP.md) |
| 30 | [SYS_CARD_SERVICEBUS](30-card-SYS_CARD_SERVICEBUS.md) |
| 31 | [CUS_CARD_NWSUAF_CALENDAR](31-card-CUS_CARD_NWSUAF_CALENDAR.md) |
| 32 | [CUS_CARD_NWSUAF_PERSONALDATA](32-card-CUS_CARD_NWSUAF_PERSONALDATA.md) |
| 33 | [CUS_CARD_TXL](33-card-CUS_CARD_TXL.md) |
| 34 | [CUS_CARD_NWSUAF_SERVICEITEMCATEGORY](34-card-CUS_CARD_NWSUAF_SERVICEITEMCATEGORY.md) |
| 35 | [CUS_CARD_NWSUAF_SERVICEITEMCATEGORYDETAIL](35-card-CUS_CARD_NWSUAF_SERVICEITEMCATEGORYDETAIL.md) |
| 36 | [CUS_CARD_NWSUAF_SERVICEBUS](36-card-CUS_CARD_NWSUAF_SERVICEBUS.md) |

### CAS 认证：40–48

| 编号 | 文档 |
|------|------|
| 40 | [GET /authserver/login](40-cas-get-login-page.md) |
| 41 | [POST 密码登录](41-cas-post-login-password.md) |
| 42 | [POST FIDO2 登录](42-cas-post-login-fido2.md) |
| 43 | [startAssertion](43-cas-startAssertion.md) |
| 44 | [二次验证页](44-cas-reAuthLoginView.md) |
| 45 | [切换验证类型](45-cas-changeReAuthType.md) |
| 46 | [提交二次验证](46-cas-reAuthSubmit.md) |
| 47 | [登出](47-cas-logout.md) |
| 48 | [切换身份](48-cas-switchByCode.md) |

### 个人中心：60–78

| 编号 | 文档 |
|------|------|
| 60 | [getUserConf](60-pi-getUserConf.md) |
| 61 | [getLanguageTypes](61-pi-getLanguageTypes.md) |
| 62 | [getStaticLanguageData](62-pi-getStaticLanguageData.md) |
| 63 | [getCopyright](63-pi-getCopyright.md) |
| 64 | [tenant/info](64-pi-tenant-info.md) |
| 65 | [getMenuRole](65-pi-getMenuRole.md) |
| 66 | [MFA 设备](66-pi-showMultiFactorUntrustedDevice.md) |
| 67 | [设备通知](67-pi-unTrustDeviceNotify.md) |
| 68 | [账号设置](68-pi-accountSetting.md) |
| 69 | [关联账号](69-pi-bindingUserList.md) |
| 70 | [联合登录](70-pi-combinedLoginSettingList.md) |
| 71 | [三方邀请](71-pi-thirdPartyInvitation.md) |
| 72 | [设置详情](72-pi-userSettingDetail.md) |
| 73 | [在线应用](73-pi-onlineApp-enabled.md) |
| 74 | [OTP 绑定](74-pi-otpToken-isBind.md) |
| 75 | [用户数据](75-pi-queryUserData.md) |
| 76 | [在线用户/登录历史](76-pi-queryUserOnline.md) |
| 77 | [应用名称](77-pi-querySelectAppName.md) |
| 78 | [账号安全 Tab](78-pi-accountSecurity.md) |

### newehall 旧版门户：80–92

| 编号 | 文档 |
|------|------|
| 80 | [getPortalPage](80-newehall-getPortalPage.md) |
| 81 | [getPortalInfoNew](81-newehall-getPortalInfoNew.md) |
| 82 | [getUserInfoAndSchoolInfo](82-newehall-getUserInfoAndSchoolInfo.md) |
| 83 | [recUseServiceList](83-newehall-recUseServiceList.md) |
| 84 | [queryServiceCountGroupByType](84-newehall-queryServiceCountGroupByType.md) |
| 85 | [searchServiceItem](85-newehall-searchServiceItem.md) |
| 86 | [getNewsTypeByCode](86-newehall-getNewsTypeByCode.md) |
| 87 | [getMailAccountInfo](87-newehall-getMailAccountInfo.md) |
| 88 | [getView/getViewDataDetail](88-newehall-getView-getViewDataDetail.md) |
| 89 | [getUnreadMessageCount](89-newehall-getUnreadMessageCount.md) |
| 90 | [readUserServiceCount/readSearchHis](90-newehall-readUserServiceCount-readSearchHis.md) |
| 91 | [任务中心 APIs](91-newehall-taskcenter-apis.md) |
| 92 | [其他服务 API](92-newehall-serviceBus-recommend-random.md) |

### Minos 平台 & 独立业务系统：100–112

| 编号 | 文档 |
|------|------|
| 100 | [Minos 平台通用 API](100-minos-platform-apis.md) |
| 101 | [Minos 子应用模块目录](101-minos-app-catalog.md) |
| 102 | [综合报修系统](102-repair-system-apis.md) |
| 103 | [智能体平台](103-spark-agent-platform.md) |
| 104 | [DeepSeek/Open WebUI](104-deepseek-openwebui.md) |
| 105 | [云盘 360 亿方云](105-yunpan-360fangcloud.md) |
| 106 | [正版软件平台](106-software-platform.md) |
| 107 | [图书馆 OPAC](107-library-opac.md) |
| 108 | [办事大厅服务目录](108-service-catalog-complete.md) |
| 109 | [学生画像 CDSP](109-cdsp-student-data.md) |
| 110 | [Minos AI 辅导员](110-minos-ai-assistant.md) |
| 111 | [消息中心](111-message-center.md) |
| 112 | [图书馆座位/空间预约](112-library-seat-booking.md) |
