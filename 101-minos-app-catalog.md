# Minos 子应用模块目录

> `getAppConfig` API 对所有子应用可通（即使应用本身返回 403）

## 获取配置

```
GET /{appType}/sys/funauthapp/api/getAppConfig/{appName}-{serviceId}.do
```

返回该应用的 `MODULES[]`（路由+标题）、`HEADER`（用户信息）、`routeTitle` 等。

## 已探测应用模块清单

### 成绩查询 (cjcx / jwapp)

| serviceId | 4768574631264620 |
|-----------|-----------------|

| 模块路由 | 标题 | 说明 |
|---------|------|------|
| `cjcx` | 成绩查询 | 查询个人成绩 |
| `cjfx` | 成绩分析 | 成绩统计分析 |

### 成绩认定 (cjrd / jwapp)

| serviceId | 4972513376771829 |
|-----------|-----------------|

| 模块路由 | 标题 |
|---------|------|
| `cjrd` | 成绩认定 |

### 中英文成绩单 (zywcjd / jwapp)

| serviceId | 4903218112351275 |
|-----------|-----------------|

| 模块路由 | 标题 |
|---------|------|
| `cjd` | 中英文成绩单(本) |

### 大类专业分流 (dlzyfl / jwapp)

| serviceId | 5500471297307451 |
|-----------|-----------------|

| 模块路由 | 标题 |
|---------|------|
| `xszyflsq` | 学生专业分流申请 |

### 学籍异动 (xjydyy / jwapp)

| serviceId | 5411553903799053 |
|-----------|-----------------|

| 模块路由 | 标题 |
|---------|------|
| `xjydsq` | 学籍异动申请 |

### 本研互选 (byhx / jwapp)

| serviceId | 5330873932937271 |
|-----------|-----------------|

| 模块路由 | 标题 | 按钮 |
|---------|------|------|
| `bksxk` | 本科生选课 | - |
| `xscjcx` | 学生成绩查询 | `xscjcx_export` |

### 推免资格申请管理 (tmzgsqglappnwsuaf / gsapp)

| serviceId | 7218862527423622 |
|-----------|-----------------|

| 模块路由 | 标题 | 范围 |
|---------|------|------|
| `zxsq` | 在线申请 | 19级 |
| `tmkhzb` | 推免考核部门指标 | admin |
| `tmkhzb2` | 推免考核项目指标 | admin |
| `bmxmgl` | 报名批次管理 | admin |
| `yzbshkh` | 推免资格名单审核 | admin |

## 模块 API 模式

每个模块的数据通过以下端点获取：

```
POST /{appType}/sys/{appName}/modules/{module}/initPage.do
```

示例：`POST /jwapp/sys/cjcx/modules/cjcx/initPage.do`

> 注意：`initPage.do` 需要对该应用有实际权限，否则返回 403。

## appType 清单

| appType | 目录 | 说明 |
|---------|------|------|
| `jwapp` | 教务应用 | 成绩查询、课表、学籍、评教等 |
| `gsapp` | 研究生应用 | 推免、学术成果、学位申请等 |
| `taskcenterapp` | 任务中心 | 待办/已办/流程 |

## URL 构造规则

```
# 应用首页
https://newehall.nwafu.edu.cn/{appType}/sys/{appName}/*default/index.do

# 应用配置
https://newehall.nwafu.edu.cn/{appType}/sys/funauthapp/api/getAppConfig/{appName}-{serviceId}.do

# 模块页面
https://newehall.nwafu.edu.cn/{appType}/sys/{appName}/modules/{module}/{module}.html

# 模块数据初始化
https://newehall.nwafu.edu.cn/{appType}/sys/{appName}/modules/{module}/initPage.do

# 业务流程
https://newehall.nwafu.edu.cn/{appType}/sys/gglglyy/ydlc/getYdlcByAppNameAndGnid.do
```
