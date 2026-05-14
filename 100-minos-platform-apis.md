# Minos 子应用平台通用 API

> 域：`newehall.nwafu.edu.cn`
> 路径：`/{appType}/sys/`（appType = `jwapp`, `gsapp` 等）

所有 Minos 子应用共享一套平台级别中间件 API。

---

## 一、应用配置

### funauthapp/api/getAppConfig — 获取应用配置

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `/{appType}/sys/funauthapp/api/getAppConfig/{appName}-{serviceId}.do?v={random}` |

**示例**：`/gsapp/sys/funauthapp/api/getAppConfig/tmzgsqglappnwsuaf-7218862527423622.do`

#### 响应

```json
{
  "APP_ID": "7218862527423622",
  "MODULES": [
    {"route": "zxsq", "buttons": [], "range": "19", "title": "在线申请"}
  ],
  "schoolID": "107121",
  "routeTitle": {"zxsq": "在线申请"},
  "HEADER": {
    "userInfo": {
      "logoutHref": "http://newehall.nwafu.edu.cn/logout?service="
    },
    "dropMenu": [
      {"active": true, "id": "20150808183545465", "text": "学生组"}
    ]
  }
}
```

| 字段 | 说明 |
|------|------|
| `MODULES[].route` | 模块路由名（用于 URL #/module） |
| `MODULES[].title` | 模块显示名 |
| `routeTitle` | 所有路由的标题映射 |
| `HEADER.userInfo.logoutHref` | 登出 URL |
| `HEADER.dropMenu` | 菜单项（用户组） |

---

## 二、模块初始化（核心业务 API）

### modules/{module}/initPage.do — 模块页面初始化

每个应用的每个功能模块对应一个 `initPage.do`，这是获取业务数据的**核心 API**。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `/{appType}/sys/{appName}/modules/{module}/initPage.do` |

**示例**：`/gsapp/sys/tmzgsqglappnwsuaf/modules/zxsq/initPage.do`

模块 HTML 模板位于：
```
/{appType}/sys/{appName}/*default/modules/{module}/{module}.html
```

---

## 三、流程引擎

### gglglyy/ydlc/getYdlcByAppNameAndGnid.do — 获取业务流程

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `/{appType}/sys/gglglyy/ydlc/getYdlcByAppNameAndGnid.do` |

返回该应用关联的业务流程定义。

---

## 四、前端辅助

### gglglyy/qs/checkShow.do — 检查组件的显示状态

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `/{appType}/sys/gglglyy/qs/checkShow.do` |

### gglglyy/qs/checkShowItems.do — 检查组件的子项显示

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `/{appType}/sys/gglglyy/qs/checkShowItems.do` |

### gglglyy/qs/getUnReadMsgCount.do — 获取未读消息数（应用级）

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `/{appType}/sys/gglglyy/qs/getUnReadMsgCount.do?appid={serviceId}` |

---

## 五、页面日志

### emappagelog/config/{appName}.do — 页面日志配置

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `/{appType}/sys/emappagelog/config/{appName}.do` |

### emappagelog/push.do — 推送页面日志

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `/{appType}/sys/emappagelog/push.do` |

---

## 六、金手指（开发工具，管理员可见）

### jnbbapp/goldenfinger/queryEditPageDatas.do — 查询页面编辑数据

显示哪些模块/文本被管理员自定义修改过。

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `/{appType}/sys/jnbbapp/goldenfinger/queryEditPageDatas.do` |

#### 响应示例

```json
[
  {
    "WID": "fbd9bb2022ae49d4a931d186115e34b2",
    "APPNAME": "tmzgsqglappnwsuaf",
    "TYPE": "TITLE",
    "MODULE": "/tmkhzb",
    "VALUE": "{\"curValue\":\"推免考核部门指标\",\"srcValue\":\"推免考核指标\"}",
    "CZRQ": "2025-07-21 10:36:30",
    "CZZ": "01119136"
  }
]
```

这暴露了该应用的所有模块列表以及它们被自定义的文本。

---

## 已知模块路由列表

### 推免资格申请管理 (tmzgsqglappnwsuaf)

| 模块路由 | 标题 |
|---------|------|
| `zxsq` | 在线申请 |
| `tmkhzb` | 推免考核部门指标 |
| `tmkhzb2` | 推免考核项目指标 |
| `bmxmgl` | 报名批次管理 |
| `yzbshkh` | 推免资格名单审核 |

### 学术成果申请 (xsczsjcjglapp)

（模块路由在 `getAppConfig` 中返回）
