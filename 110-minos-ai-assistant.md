# Minos AI辅导员/AI助手 API（minos.nwafu.edu.cn）

> 系统：Minos Campus AI Assistant
> 路径前缀：`/assistant/`

## 认证

通过 CAS SSO 自动登录。

---

## 一、基础 API

| 端点 | 方法 | 说明 |
|------|------|------|
| `/currentUserInfo` | GET | 当前用户信息 |
| `/assistant/getAssistantConfig?assistantCode=assistant_default` | GET | 助手配置 |
| `/assistant/getDisclaimerFlag` | GET | 免责声明标志 |

## 二、智能体与工具

### getAgentAndTools — 智能体+工具列表

| 方法 | `GET` |
| URL | `https://minos.nwafu.edu.cn/assistant/getAgentAndTools?isUserChatOrder=1&platformType=0` |

返回可用 AI 工具列表（见下方工具清单）。

## 三、会话管理

### saveUserSession — 创建/更新会话

| 方法 | `POST` |
| URL | `https://minos.nwafu.edu.cn/assistant/saveUserSession` |

返回：`sessionId` (如 `1504539901833809920`)

### getUserSession — 获取会话历史（分页）

| 方法 | `GET` |
| URL | `https://minos.nwafu.edu.cn/assistant/getUserSession?pageNumber=1&pageSize=31` |

## 四、AI 对话（核心）

### assistant/completions — 发送消息并获取回复（SSE 流式）

| 方法 | `GET` (SSE) |
| URL | `https://minos.nwafu.edu.cn/assistant/completions` |

#### 参数

| 参数 | 说明 | 示例 |
|------|------|------|
| `sessionId` | 会话 ID | `1504539901833809920` |
| `question` | URL编码的问题 | `%E6%9F%A5%E8%AF%A2%E6%88%91%E7%9A%84%E8%AF%BE%E8%A1%A8` |
| `agentWid` | 智能体 WID（空=默认） | |
| `fileIds` | 文件 ID（空=无附件） | |
| `useReasoner` | 是否使用深度思考 | `1`=是, `0`=否 |

#### 响应

SSE (Server-Sent Events) 流式返回，类型为 `text/event-stream`。

### getRecommendQuestion — 推荐追问

| 方法 | `POST` |
| URL | `https://minos.nwafu.edu.cn/assistant/getRecommendQuestion` |

## 五、业务数据

### getAssistantBusiness — 获取业务数据

| 方法 | `GET` |
| URL | `https://minos.nwafu.edu.cn/assistant/getAssistantBusiness?businessType={type}` |

| businessType | 说明 | 状态 |
|-------------|------|------|
| `task` | 待办任务 | ✅ data=0 |
| `schedule` | 课表日程 | ⚠️ 应用未申请接口 |
| `message` | 消息 | ✅ |

## 六、反馈

### assistantFeedback/getFeedbackPhraseList — 反馈短语

| 方法 | `GET` |
| URL | `https://minos.nwafu.edu.cn/assistantFeedback/getFeedbackPhraseList?phraseType=aiAnswer` |

---

## 七、可用 AI 工具

| 工具名 | 类型 | 引用次数 | 功能 |
|--------|------|---------|------|
| 服务办理助手 | agent | 6,401 | 综合服务办理Agent |
| 查询日程列表 | tools | 3,752 | 查询课表/日程 |
| 生成证明文件 | tools | 1,046 | 证明文件打印 |
| 研究生离校 | tools | 717 | 离校办理查询 |
| 创建个人日程 | tools | 212 | 创建日程/预约 |
| 查询待办任务 | tools | 193 | 获取待办(分页) |
| 研究生缓考申请 | tools | 169 | 缓考申请 |
| 查询天气 | tools | 35 | 天气查询 |
| 本科生离校 | tools | 19 | 离校办理查询 |
| 迎新查询[本科生] | tools | 0 | 迎新查询 |

## 八、Flutter 集成建议

```dart
// 1. 创建会话
final sessionId = await post('saveUserSession');

// 2. 发送消息（SSE流式）
final url = 'completions?sessionId=$sessionId&question=${Uri.encodeComponent(q)}&useReasoner=1';
// 使用 SSE client 接收流式响应

// 3. 获取推荐追问
final suggestions = await post('getRecommendQuestion');
```
