# 西农云盘 API（pan.nwafu.edu.cn）

> 系统：360亿方云 (FangCloud) 混合云版
> 用户数：80001 seats
> 公司：西北农林科技大学

## 认证

通过 CAS SSO 自动登录。

## API 列表

### 基础

| 端点 | 方法 | 说明 |
|------|------|------|
| `/token/` | GET | CSRF token |
| `/alive/link` | GET | 长连接保活 |
| `/poseidon/main_page/data` | POST | 主页数据（企业信息+用户信息+导航） |
| `/poseidon/main_page/data_secondary` | POST | 次级数据 |
| `/enterprises/get_promotion` | POST | 推广信息 |
| `/enterprises/important_message` | POST | 重要消息 |
| `/trumpet/messages/get_unread_message_count_for_user` | GET | 未读消息数 (7条) |

### 用户

| 端点 | 方法 | 说明 |
|------|------|------|
| `/apps/users/search_suggestion` | GET | 用户搜索建议 |

### 智能/AI

| 端点 | 方法 | 说明 |
|------|------|------|
| `/aiapi/zsh/knowledgeGpt/list_square?type=all` | GET | AI知识库广场 |
| `/ai_appointment/appointment_data?tracking_type=1` | GET | AI预约数据 |

### 工作流

| 端点 | 方法 | 说明 |
|------|------|------|
| `/ark/app/workflow/queryTemplates?isAll=true` | GET | 工作流模板 |

### LowCode 页面

| 端点 | 方法 | 说明 |
|------|------|------|
| `/lowCode_api/lowcode/page/ui/get_config` | GET | 页面配置 |
| `/lowCode_api/lowcode/page/view?pageKey=...` | POST | 页面数据 |
| `/lowCode_api/lowcode/config_item/get?name=0` | GET | 配置项 |

### 下载

| 端点 | URL |
|------|-----|
| Windows 客户端 | `/app/sync/nwafu/nwafuInstaller.exe` |
| Mac 客户端 | `/app/sync/nwafu/nwafuInstaller.dmg` |

## 导航菜单

工作台, AI, 门户, 文件, 同步, 消息, 知识, 任务
