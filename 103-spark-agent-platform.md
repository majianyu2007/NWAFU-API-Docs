# 西农智能体平台 API（spark.nwafu.edu.cn）

> 系统：Skybox 智能体平台
> 后端：FireFlames Agent Manager
> 路径前缀：`/agent/proxyApi/`

## 认证

通过 CAS SSO 自动登录，使用 `CASTGC=REDACTED

## API 列表

### 1. skybox/api/v1/menus — 菜单

| 方法 | `GET` |
| URL | `https://spark.nwafu.edu.cn/agent/proxyApi/skybox/api/v1/menus` |

### 2. skybox/api/v1/currentUser — 当前用户

| 方法 | `GET` |
| URL | `https://spark.nwafu.edu.cn/agent/proxyApi/skybox/api/v1/currentUser` |

### 3. skybox/api/v1/getTenantByUserId — 租户信息

| 方法 | `GET` |
| URL | `https://spark.nwafu.edu.cn/agent/proxyApi/skybox/api/v1/getTenantByUserId?userId={uid}` |

```json
[{"id":"314948c3-...", "name":"西北农林科技大学", "tenantCode":"zh_1705891385753"}]
```

### 4. skybox/boxing.json — 平台配置

| 方法 | `GET` |
| URL | `https://spark.nwafu.edu.cn/agent/proxyApi/skybox/boxing.json` |

### 5. flames-api/v1/config/list — 配置列表

| 方法 | `GET` |
| URL | `https://spark.nwafu.edu.cn/agent/proxyApi/flames-agent-manager/flames/api/v1/config/list` |

### 6. flames-api/v1/taskRecords/unPage — 任务记录（聊天会话）

| 方法 | `GET` |
| URL | `https://spark.nwafu.edu.cn/agent/proxyApi/flames-agent-manager/flames/api/v1/taskRecords/unPage?sort=createdDate,desc&kindCode.equals=CHAT_SESSION` |

参数 `kindCode.equals` 可选值：`CHAT_SESSION`, `AGENT_SESSION` 等。

---

## 子应用

SPA 入口：`/agent/{appName}/` 如：
- `skybox-base/` — 基础框架
- `skybox-core/` — 核心
- `flames-agent/` — 智能体管理
- `micro-docqa/` — 文档问答
- `skybox-astrolink-ui/` — Astrolink UI
- `skybox-elite-app/` — Elite 应用
- `skybox-ppt-editor/` — PPT 编辑器
