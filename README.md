# NWAFU 本科生 App API 参考手册

> 西北农林科技大学全信息系统 API 逆向 | 2026-05-14
> 账号：张三 2024012001 信息工程学院 2025级

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

## 本科生常用功能速查

### 📅 日程课表
| 功能 | API | 状态 |
|------|-----|------|
| 课表订阅列表 | ehall `execCardMethod` CUS_CARD_NWSUAF_CALENDAR `getPermissionCal` | ✅ |
| 课表数据 | ehall 日历卡（页面渲染） | ⚠️ data=null via API |
| Minos 查询日程 | `minos.nwafu.edu.cn/assistant/getAssistantBusiness?businessType=schedule` | ✅ |
| Minos 创建日程 | Minos AI 工具 "创建个人日程" | ✅ |
| [91-newehall-taskcenter-apis.md](91-newehall-taskcenter-apis.md) | | |
| [110-minos-ai-assistant.md](110-minos-ai-assistant.md) | | |

### 📝 待办事项
| 功能 | API | 状态 |
|------|-----|------|
| 待办/已办计数 | newehall `taskcenterapp/.../getTaskTodoAndDoneCount.do` | ✅ |
| 待办列表(分页) | newehall `taskcenterapp/.../getTaskRestful.do` POST | ✅ |
| 流程统计 | newehall `taskcenterapp/.../getMyProcessCount.do` | ✅ |
| Minos AI查待办 | Minos 工具 "查询待办任务" | ✅ |
| [91-newehall-taskcenter-apis.md](91-newehall-taskcenter-apis.md) | | |

### 📚 图书馆
| 功能 | API | 状态 |
|------|-----|------|
| 搜索图书 | `libopac.nwafu.edu.cn/meta-local/opac/search/extend3` POST | ✅ |
| 新书列表 | `/meta-local/opac/new/books?page=1&pageSize=24` | ✅ |
| 热门图书 | `/meta-local/opac/commend/hot1?count=20` | ✅ |
| [107-library-opac.md](107-library-opac.md) | | |

### 🔧 报修
| 功能 | API | 状态 |
|------|-----|------|
| 维修分类 | `repair.nwafu.edu.cn/.../api/public/scenes/list.do` (10类) | ✅ |
| 楼栋列表 | `.../api/public/userareasitelist.do` (150+楼栋) | ✅ |
| 维修项目 | `.../api/public/usertypeitemlist.do` (70+项) | ✅ |
| 我的工单 | `.../api/dispose/mybill.do` (分页) | ✅ |
| [102-repair-system-apis.md](102-repair-system-apis.md) | | |

### 🤖 AI 助手
| 功能 | API | 状态 |
|------|-----|------|
| DeepSeek 对话 | `deepseek.nwafu.edu.cn/api/chat/completions` (OpenAI兼容) | ✅ |
| DeepSeek 可用模型 | Qwen3-235B, Qwen3-32B, Kimi-K2.6, Qwen3.6-27B | ✅ |
| AI辅导员 | `minos.nwafu.edu.cn/assistant/` (10个AI工具) | ✅ |
| 智能体平台 | `spark.nwafu.edu.cn/agent/proxyApi/` | ✅ |
| [104-deepseek-openwebui.md](104-deepseek-openwebui.md) | | |
| [110-minos-ai-assistant.md](110-minos-ai-assistant.md) | | |
| [103-spark-agent-platform.md](103-spark-agent-platform.md) | | |

### 📁 云盘
| 功能 | API | 状态 |
|------|-----|------|
| 主页数据 | `pan.nwafu.edu.cn/poseidon/main_page/data` POST | ✅ |
| 未读消息 | `pan.nwafu.edu.cn/trumpet/messages/get_unread_message_count_for_user` | ✅ 7条 |
| 知识库 | `pan.nwafu.edu.cn/aiapi/zsh/knowledgeGpt/list_square` | ✅ |
| [105-yunpan-360fangcloud.md](105-yunpan-360fangcloud.md) | | |

### 💻 正版软件
| 功能 | API | 状态 |
|------|-----|------|
| 软件列表 | `software.nwafu.edu.cn/prod-api/index/recommendSoftwares` | ✅ |
| 软件下载 | `software.nwafu.edu.cn/prod-api/download/{id}/{uid}/{type}` | ✅ |
| Office 2024/2021/2019/2016, Windows 11/10, Visio, MATLAB, WPS, 中望CAD | | |
| [106-software-platform.md](106-software-platform.md) | | |

### 📊 个人画像
| 功能 | API | 状态 |
|------|-----|------|
| 本科画像 | `cdsp.nwafu.edu.cn/cdsp/portalEngine/pageelement/list` | ✅ |
| 用户信息 | `cdsp.nwafu.edu.cn/cdsp/portalEngine/getLoginUser` | ✅ |
| [109-cdsp-student-data.md](109-cdsp-student-data.md) | | |

### 📬 消息通知
| 功能 | API | 状态 |
|------|-----|------|
| 消息分类 | `newehall/jsonp/getUserTags` | ✅ 0条 |
| 消息列表 | `newehall/jsonp/getTagsMessages` (分页) | ✅ |
| [111-message-center.md](111-message-center.md) | | |

### 👤 用户中心
| 功能 | API | 状态 |
|------|-----|------|
| 个人信息 | ehall `getLoginUserAndGuest` | ✅ |
| 账号安全 | authserver `personalInfo/accountSecurity/accountSetting` | ✅ |
| 登录历史 | authserver `personalInfo/UserOnline/user/queryUserOnline` | ✅ |
| 设备管理 | authserver `personalInfo/common/unTrustDeviceNotify` | ✅ |
| OTP 令牌 | authserver `personalInfo/otpToken/isBind` | ✅ true |

### 🏫 办事大厅服务目录
| 视图 | 分类 | 事项 |
|------|------|------|
| 学生办事 | 迎新/本科/研究生/证明/自助/网络/师生 7类 | 118项 |
| 按部门 | 党校/组织部/教务处/档案馆/图书馆/医院/统战部 7部门 | 41项 |
| [108-service-catalog-complete.md](108-service-catalog-complete.md) | | |

### ⚠️ 受限功能（需特定权限）
| 功能 | 应用 | 状态 |
|------|------|------|
| 成绩查询 | jwapp/cjcx | 403 |
| 成绩认定 | jwapp/cjrd | 403 |
| 中英文成绩单 | jwapp/zywcjd | 403 |
| 学籍异动 | jwapp/xjydyy | 403 |
| 大类专业分流 | jwapp/dlzyfl | 403 |
| 本研互选 | jwapp/byhx | 403 |
| 网上评教 | jwapp/jwwspj | 403 |
| 大模型训练平台 | huoshi | UAP SSO 不兼容 |

> 注：`getAppConfig` 对所有受限应用可通，可获取模块路由。

## 登录方式

| 方式 | 库 | 状态 |
|------|-----|------|
| FIDO2 Passkey | `wisedu_cas` auth_method="fido2" | ✅ 推荐 |
| 密码+TOTP | `wisedu_cas` | ✅ |
| 微信联合登录 | authserver accountRelation/combinedLoginSettingList | ✅ |
