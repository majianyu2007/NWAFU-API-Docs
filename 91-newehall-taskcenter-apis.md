# newehall: 任务中心 APIs（taskcenterapp）

任务中心是处理待办、已办、流程的核心模块。

## getTaskTodoAndDoneCount — 待办/已办计数

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://newehall.nwafu.edu.cn/taskcenterapp/sys/taskCenter/taskNew/getTaskTodoAndDoneCount.do` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

### 响应

```json
{
  "code": 0,
  "datas": {
    "todoCount": 0,
    "doneCount": 0
  },
  "result": "success"
}
```

---

## getMyProcessCount — 我的流程计数

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://newehall.nwafu.edu.cn/taskcenterapp/sys/taskCenter/taskNew/getMyProcessCount.do` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

### 响应

```json
{
  "code": 0,
  "datas": {
    "runningCount": 8398,
    "completeCount": 131824
  },
  "result": "success"
}
```

---

## getTaskCountByBusinessSource — 按业务来源统计

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://newehall.nwafu.edu.cn/taskcenterapp/sys/taskCenter/taskNew/getTaskCountByBusinessSource.do?flag=1&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

### 响应

```json
{
  "code": 0,
  "datas": [
    {"WID": "", "COUNT": 0, "SOURCE_NAME": "全部"}
  ],
  "result": "success"
}
```

---

## getTaskRestful — 任务列表（分页）

这是获取具体任务列表的核心 API。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://newehall.nwafu.edu.cn/taskcenterapp/sys/taskCenter/taskNew/getTaskRestful.do` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

### 请求体

```json
{
  "flag": 1,
  "sourceWid": "",
  "pageNumber": 1,
  "pageSize": 7,
  "_": 1778748404185
}
```

| 字段 | 说明 |
|------|------|
| `flag` | 1=待办, 2=已办, 3=我发起的 |
| `sourceWid` | 业务来源 WID（空=全部） |
| `pageNumber` | 页码 |
| `pageSize` | 每页数量 |

### 响应

```json
{
  "code": 0,
  "datas": {
    "queryTodoTask": {
      "taskDataTotal": 0,
      "taskData": []
    }
  },
  "result": "success"
}
```

任务项包含业务流程详情、发起人、时间等字段。

---

## pubdzywtbjk/getData/getAll — 公共通知

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://newehall.nwafu.edu.cn/taskcenterapp/sys/pubdzywtbjk/getData/getAll.do?pageNum=1&pageSize=6&_={timestamp}` |
| 鉴权 | asessionid + MOD_AUTH_CAS |

### 响应

```json
{
  "COUNT": "8062",
  "XX": [
    {"URL": "https://fwoa.nwafu.edu.cn", "TITLE": "关于举办第116期...的通知", "TIME": "2023-12-19"}
  ],
  "code": 200
}
```

> 注意：此接口响应格式不同于其他 taskcenter API（使用 `code:200` 和大写字段名）。
