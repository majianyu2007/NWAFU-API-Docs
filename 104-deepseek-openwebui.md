# DeepSeek NWAFU API（deepseek.nwafu.edu.cn）

> 系统：Open WebUI v0.9.2
> 后端模型：Xinference + 外部 API
> 认证：JWT (signin 后获得 token)

## 认证

### POST /api/v1/auths/signin — CAS 自动登录

| 方法 | `POST` |
| URL | `https://deepseek.nwafu.edu.cn/api/v1/auths/signin` |

CAS SSO 后自动完成，返回 JWT token。

```json
{
  "id": "8b92753d-...", "name": "2024012001", "role": "user",
  "email": "2024012001@nwafu.edu.cn",
  "token": "eyJ...REDACTED_JWT_TOKEN",
  "token_type": "Bearer", "expires_at": 1782378545
}
```

## 可用模型

### GET /api/models

| 模型 | 类型 | 能力 |
|------|------|------|
| Qwen3-235B-A22B | 大语言模型 | vision, code_interpreter |
| Qwen3-32B | 大语言模型 | vision, web_search, code_interpreter |
| Kimi-K2.6 | 大语言模型 | vision, web_search, image_generation, code_interpreter |
| Qwen3.6-27B | 大语言模型 | vision, web_search, image_generation, code_interpreter |
| bge-m3 | 嵌入模型 | 1024维, 中英文 |
| bge-reranker-large | 重排序 | 中英文 |

## 主要 API

| 端点 | 方法 | 说明 |
|------|------|------|
| `/api/config` | GET | 系统配置 |
| `/api/version` | GET | 版本信息 |
| `/api/v1/auths/signin` | POST | 登录 |
| `/api/v1/users/user/settings` | GET | 用户设置 |
| `/api/v1/auths/update/timezone` | POST | 更新时区 |
| `/api/v1/configs/banners` | GET | 横幅配置 |
| `/api/v1/tools/` | GET | 工具列表 |
| `/api/v1/functions/` | GET | 函数列表 |
| `/api/v1/terminals/` | GET | 终端列表 |
| `/api/models` | GET | 模型列表 |

## 聊天

OpenAI 兼容端点：
```
POST /api/chat/completions
Authorization: Bearer {jwt_token}
```

请求体：
```json
{
  "model": "Qwen3-32B",
  "messages": [{"role": "user", "content": "..."}],
  "stream": true
}
```

## 权限

用户拥有：models, knowledge, prompts, chat (full), api_keys, notes, folders, memories, calendar 权限。
