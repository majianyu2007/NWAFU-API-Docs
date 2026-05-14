# 综合报修系统 API（repair.nwafu.edu.cn）

> 系统名：西北农林综合报修管理系统 V5.11.19
> 域：`repair.nwafu.edu.cn`
> 路径前缀：`/mgr/repaire/user/api/`

## 认证机制

报修系统通过 CAS bridge 模式登录。访问入口 URL 时会自动获取 `app_token` 并完成桥接认证。

### 入口 URL

```
https://repair.nwafu.edu.cn/mgr/repaire/public/cas/xinong/pc_user
→ 302 重定向到:
https://repair.nwafu.edu.cn/mgr/repaire/user/?app_token={token}&app_type=bridge
```

### bridgelogin.do — 桥接登录

| 属性 | 值 |
|------|-----|
| 方法 | `POST` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/bridgelogin.do` |

完成 CAS bridge 到本地 session 的转换。需要携带 CAS session cookie。

---

## 用户信息

### getuserinfo.do — 获取用户信息

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/getuserinfo.do` |

```json
{
  "usercode": "2024012001",
  "username": "2024012001",
  "mobile": "2024012001",
  "islocationmap": false,
  "iswritephoneno": false,
  "isshowaudit": false,
  "isgzhactive": false
}
```

---

## 维修场景（10 个分类）

### public/scenes/list.do — 维修场景列表

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/public/scenes/list.do` |

```json
[
  {"scid": 6, "scname": "暖气报修", "note": "南北校区及家属区 供暖方面的问题"},
  {"scid": 1, "scname": "宿舍报修", "note": "南校和北校宿舍水电、家具、公共区域水电等报修"},
  {"scid": 2, "scname": "办公教学楼报修", "note": "南校和北校的办公教学楼水电、教室设施设备等报修"},
  {"scid": 3, "scname": "中心区楼宇报修", "note": "中心区管辖范围内的水电、中央空调等报修"},
  {"scid": 4, "scname": "家属楼报修", "note": "南校和北校的家属楼内水电等报修"},
  {"scid": 5, "scname": "道路广场报修", "note": "路面道沿、雨篦子井盖、检查井化粪池等问题"},
  {"scid": 8, "scname": "浴室开水房报修", "note": "学生浴室、开水房的相关设施设备报修"},
  {"scid": 7, "scname": "基础设备报修", "note": "全校范围内室外水管网、电网、路灯..."},
  {"scid": 9, "scname": "水表报修", "note": "维修全校办公区、家属区的水表"},
  {"scid":10, "scname": "电表报修", "note": "维修全校办公区、南校青教公寓、牡丹园及西院住宅区的电表"}
]
```

---

## 区域与站点

### public/userareasitelist.do — 区域+站点全列表

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/public/userareasitelist.do` |

返回 `area[]`（20个区域）+ `site[]`（150+个具体楼栋/场所）。

每个 site 包含：`siteid`, `sitename`, `note`, `areaid`, `areaname`, `areanamepath`。

---

## 维修类型与项目

### public/usertypeitemlist.do — 类型+项目全列表

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/public/usertypeitemlist.do` |

返回 `type[]`（12个类型）+ `item[]`（70+个具体项目）。

type 列表：电、水、木泥、暖气、浴室、开水房、电梯、通信、紧急（慎选）、道路广场、室外设备、其它。

---

## 工单状态

### public/centerstatelist.do — 工单状态列表

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/public/centerstatelist.do` |

```json
[
  {"statetag": "s_dsl", "statename": "待受理"},
  {"statetag": "s_ypg", "statename": "已派单"},
  {"statetag": "s_clz", "statename": "处理中"},
  {"statetag": "s_dsh", "statename": "待审核"},
  {"statetag": "s_ysh", "statename": "已审核"},
  {"statetag": "s_ddz", "statename": "调度中"},
  {"statetag": "s_ywg", "statename": "已完工"},
  {"statetag": "s_ypj", "statename": "已评价"},
  {"statetag": "H_Ping", "statename": "已评价(好)"},
  {"statetag": "Z_Ping", "statename": "已评价(中)"},
  {"statetag": "C_Ping", "statename": "已评价(差)"},
  {"statetag": "s_ycx", "statename": "已撤销"},
  {"statetag": "s_yzz", "statename": "已终止"}
]
```

---

## 维修人员

### public/maintenancepersonnel/list.do — 维修人员列表

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/public/maintenancepersonnel/list.do` |

返回 80+ 名维修人员（姓名、电话、工号、是否启用自动刷新）。

---

## 我的工单

### dispose/mybill.do — 我的报修工单（分页）

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/dispose/mybill.do` |

### 参数

| 参数 | 说明 | 示例 |
|------|------|------|
| `sorttag` | 排序标签 | `1` |
| `pageindex` | 页码 | `1` |
| `pagesize` | 每页条数 | `30` |
| `begindate` | 开始日期 | `2025-05-14` |
| `enddate` | 结束日期 | `2026-05-14` |
| `statetag` | 状态筛选(可选) | `s_ypj` |
| `scid` | 场景筛选(可选) | `1` |

### 响应

```json
{
  "page": {
    "recordcount": 1,
    "pagecount": 1,
    "pagesize": 30,
    "pageindex": 1
  },
  "list": [
    {
      "billid": 167776,
      "formatbillid": "GD2605060001",
      "statetag": "s_ypj",
      "statename": "已评价(好)",
      "crtbilldatetime": "2026-05-06 00:44:25",
      "scid": 1,
      "scname": "宿舍报修",
      "typeid": 16,
      "typename": "电",
      "itemid": 86,
      "itemname": "其它",
      "areaid": 4,
      "siteid": 46,
      "sitename": "西区10#学生公寓",
      "sitenote": "428",
      "repairenote": "1.宿舍电风扇无法开启\n2.宿舍 23:30 不会断电...",
      "username": "张三",
      "usermobile": "13800008888",
      "mpcode": "2025140100",
      "mpname": "王凯国",
      "pic_1": "", "pic_2": "", "pic_3": "", "pic_4": ""
    }
  ]
}
```

---

## 提交报修（推断）

基于标准 REST 模式，提交报修可能的端点：

```
POST /mgr/repaire/user/api/dispose/savebill.do
```

参数（推断）：
- `scid` — 维修场景 ID
- `typeid` — 类型 ID
- `itemid` — 项目 ID
- `siteid` — 站点 ID
- `sitenote` — 详细位置（如"428"）
- `repairenote` — 故障描述
- `usermobile` — 联系电话
- 图片上传（pic_1~pic_4）

---

## 系统信息

### cr.do — 系统版权/配置

| 属性 | 值 |
|------|-----|
| 方法 | `GET` |
| URL | `https://repair.nwafu.edu.cn/mgr/repaire/user/api/cr.do` |

```json
{
  "name": "西北农林综合报修管理系统",
  "pfshortname": "综合报修",
  "ver": "V5.11.19",
  "cr": "江苏欣动 技术支持"
}
```
