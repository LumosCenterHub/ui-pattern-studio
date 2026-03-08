# LUMOS V2.0 — 前端 AI 组装协议（完整版）

> 本文件供项目 Arch Agent 分配任务时引用，供前端 AI 组装页面时遵循。  
> 包含：设计规范 · Token 体系 · 技术约束 · 布局契约 · 组件注册表 · 组装协议 · 一致性锁定 · 交付标准  
> 组件 showcase HTML 由 Stitch 生成（见 LUMOS-Global-Constraints.md + LUMOS-Step-Prompts.md）

---

# 第一章：设计基础规范

---

## 1.1 风格定义：Professional SaaS Admin — Classic Blue Business

```
【视觉基调】专业、干净、信任感、高效、留白充足
【主色】#2563EB（Blue 600）— 唯一主色
【风格】经典 SaaS 后台商务风 — 实色填充 + 清晰边框 + 轻量阴影

色彩体系：
  主色阶：#EFF6FF(50) → #2563EB(600) → #1E3A8A(900) 共 10 档
  灰色系：Slate 冷灰 #F8FAFC(50) → #0F172A(900)
  语义色：Success #10B981 / Warning #F59E0B / Error #EF4444
  ⚠ 禁止橙色/紫色装饰色。红色仅限 error 语义。

  背景：#FFFFFF 纯白为主，#F8FAFC 浅灰为辅
  文字：#0F172A(主) / #475569(次) / #94A3B8(弱)
  边框：#E2E8F0(默认) / #CBD5E1(强调)

容器：
  背景 #FFFFFF / 边框 1px solid #E2E8F0 / 阴影轻量 / 圆角 按钮6px 卡片8px 弹窗12px

交互：
  Hover #F8FAFC 或 #EFF6FF + transition / Active #1D4ED8 / Focus ring / Disabled opacity 0.5

禁止：
  ❌ 渐变/毛玻璃/模糊/暗色背景/橙色紫色装饰
  ❌ Tailwind CSS / 外部字体库 / 图标字体
```

> **⚠** 风格定义中的颜色值仅用于描述意图。代码只允许引用 Token 变量。

---

## 1.2 完整 Design Tokens

```css
:root {
  --color-primary-50:#EFF6FF; --color-primary-100:#DBEAFE; --color-primary-200:#BFDBFE;
  --color-primary-300:#93C5FD; --color-primary-400:#60A5FA; --color-primary-500:#3B82F6;
  --color-primary-600:#2563EB; --color-primary-700:#1D4ED8; --color-primary-800:#1E40AF;
  --color-primary-900:#1E3A8A;

  --color-slate-50:#F8FAFC; --color-slate-100:#F1F5F9; --color-slate-200:#E2E8F0;
  --color-slate-300:#CBD5E1; --color-slate-400:#94A3B8; --color-slate-500:#64748B;
  --color-slate-600:#475569; --color-slate-700:#334155; --color-slate-800:#1E293B;
  --color-slate-900:#0F172A;

  --color-text-primary:#0F172A; --color-text-secondary:#475569; --color-text-muted:#94A3B8;
  --color-text-inverse:#FFFFFF; --color-text-link:#2563EB;

  --color-success:#10B981; --color-success-bg:#ECFDF5;
  --color-warning:#F59E0B; --color-warning-bg:#FFFBEB;
  --color-error:#EF4444; --color-error-bg:#FEF2F2;

  --color-bg-primary:#FFFFFF; --color-bg-secondary:#F8FAFC; --color-bg-tertiary:#F1F5F9;
  --color-bg-hover:#F8FAFC; --color-bg-active:#EFF6FF; --color-bg-overlay:rgba(0,0,0,0.4);
  --color-surface-soft:#F1F5F9; --color-surface-mixed:rgba(241,245,249,0.5);

  --color-border-default:#E2E8F0; --color-border-strong:#CBD5E1; --color-border-focus:#2563EB;

  --shadow-sm:0 1px 2px rgba(0,0,0,0.05);
  --shadow-md:0 1px 3px rgba(0,0,0,0.06),0 1px 2px rgba(0,0,0,0.04);
  --shadow-lg:0 4px 12px rgba(0,0,0,0.08);
  --shadow-xl:0 8px 24px rgba(0,0,0,0.10);

  --radius-sm:4px; --radius-md:6px; --radius-lg:8px; --radius-xl:12px; --radius-full:9999px;

  --space-1:4px; --space-2:8px; --space-3:12px; --space-4:16px; --space-5:20px;
  --space-6:24px; --space-8:32px; --space-10:40px; --space-12:48px; --space-16:64px;

  --size-control-sm:32px; --size-control-md:36px; --size-control-lg:44px;
  --size-header-height:56px; --size-sidebar-width:220px; --size-sidebar-collapsed:56px;
  --size-sidebar-secondary-width:200px; --size-toolbar-height:48px; --size-footer-height:48px;
  --size-right-panel-width:320px; --size-content-max-width:1200px; --size-content-max-width-wide:1400px;
  --size-modal-sm:400px; --size-modal-md:520px; --size-modal-lg:640px;
  --size-stepper-connector:4px; --size-icon-stroke:1.5px; --size-indicator-bar:3px;
  --size-icon-sm:16px; --size-icon-md:20px; --size-icon-lg:24px;
  --size-avatar-sm:32px; --size-avatar-md:40px; --size-avatar-lg:64px;

  --font-family:"Inter","Segoe UI","PingFang SC","Microsoft YaHei",sans-serif;
  --font-size-xs:12px; --font-size-sm:13px; --font-size-base:14px; --font-size-md:16px;
  --font-size-lg:18px; --font-size-xl:20px; --font-size-2xl:24px;
  --font-weight-normal:400; --font-weight-medium:500; --font-weight-semibold:600; --font-weight-bold:700;

  --transition-fast:all 0.15s ease;
  --focus-ring:0 0 0 3px rgba(37,99,235,0.15);
}
```

Token 硬性约束：代码中所有视觉属性值只允许引用 token 变量名。

---

## 1.3 技术约束（三不准红线）

| 红线 | 规则 |
|------|------|
| 🚫 禁止 Tailwind | 禁止 CDN 引用和 utility 类名，只允许原生 CSS + :root 变量 |
| 🚫 禁止外部资源 | 禁止 Google Fonts / 图标字体。图标必须内联 SVG stroke="currentColor"。文件必须离线可用 |
| 🚫 禁止非蓝色强调 | 唯一主色 #2563EB。禁止橙/紫装饰。红仅限 error。禁止渐变/暗色背景 |

---

## 1.4 交互协议

- Select/DatePicker 必须 Div 模拟，禁止原生 `<select>` / `<input type="date">`
- Toggle 用 Div+CSS，禁止原生 checkbox
- JS 统一 `toggleActive(el)` 函数 + `document.addEventListener('click')` 关闭监听
- 所有 Hover 必须有 transition
- 按钮尺寸锁死：sm=32px / md=36px / lg=44px

---

## 1.5 图标规范

内联 SVG：`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">`
禁止：外部图片 / Unicode 符号 / CSS border 三角形 / 硬编码颜色

---

## 1.6 组件内容语言

组件内所有用户可见文字使用英文：
- 按钮 "Create" "Confirm" "Cancel" "Delete" "Export" "Search"
- 输入框 "Enter content..." "Select department..."
- 统计 "Total Revenue" "Active Users" "$128,430"
- 告警 "System Update" "Connection Failed"
- 导航 "Dashboard" "Settings" "Overview"
- 日期 "January 2025" "Mon Tue Wed Thu Fri Sat Sun"
- 分页 "Previous" "Next" "Page 1 of 10"

---

## 1.7 命名规范

组件名：小写连字符英文（button / input / date-picker）
变体名：英文（primary / secondary / ghost）
状态名：default / hover / active / focus / disabled / loading / selected / expanded / error / success

---

## 1.8 组件入库机制

检查组合覆盖 → 不能则提交申请 → 审核通过 → 加入注册表 → 页面层才可用

---
---

# 第二章：布局与组合规则

---

## 2.1 Layout 插槽契约

| 插槽 | 可变性 |
|------|--------|
| header-slot | 固定结构，仅内容可配 |
| sidebar-slot | 固定结构，仅菜单项可配 |
| page-header-slot | 结构固定（breadcrumb+title+actions），仅内容可配 |
| content-slot | **唯一自由组合区域** |
| 其他（right-panel/tab-bar/toolbar/footer） | 可选 |

---

## 2.2 五种 Layout

### Layout 1: Classic Admin

| 插槽 | position | width | scroll-owner |
|------|----------|-------|-------------|
| header | fixed | 100% | — |
| sidebar | fixed | --size-sidebar-width / --size-sidebar-collapsed | self |
| page-header | static | auto | — |
| content-slot | static | max --size-content-max-width | page |

### Layout 2: Top Navigation
header(fixed) + content(centered 1200px) + footer(static)

### Layout 3: Dual Panel
header + sidebar(--size-sidebar-secondary-width) + content + right-panel(--size-right-panel-width)

### Layout 4: Tab Layout
header + tab-bar(sticky) + content(centered 1400px)

### Layout 5: Full Canvas
toolbar(fixed --size-toolbar-height) + content(full)

### Layout 5: Full-Height Sidebar
Sidebar 240px (To top) + Header 56px (Right-aligned) + Content Area
Full-height sidebar with integrated logo, right-aligned header with centered search bar and status pills.

---

## 2.3 间距 / 嵌套

| 场景 | Token |
|------|-------|
| 组件内部 | --space-2 ~ --space-3 |
| 同类组件间 | --space-3 ~ --space-4 |
| 区块间 | --space-6 ~ --space-8 |
| 大模块间 | --space-10 ~ --space-16 |

嵌套 ≤ 3 层。内层用 --color-bg-secondary，外层用 --color-bg-primary。不重复阴影。

---
---

# 第三章：组件注册表

---

## 3.1 Atoms

| 组件 | variants | size-policy |
|------|----------|-------------|
| button | primary/secondary/ghost/danger/text/icon-only/icon-text/group | token-derived |
| input | text/password/search/number + decorations | token-derived |
| select | single/multi/searchable/grouped (Div 模拟) | token-derived |
| checkbox | default/card/with-description/indeterminate | intrinsic |
| radio | default/card/with-description/horizontal | intrinsic |
| toggle | default/with-text/with-icon/small (Div+CSS) | token-derived |
| badge | solid/soft/outline/dot/count/closable | intrinsic |
| avatar | image/text/icon/status/group | token-derived |
| tooltip | dark/light/with-arrow/multiline | intrinsic |
| divider | solid/dashed/with-text/with-icon/vertical | flow |

## 3.2 Molecules

| 组件 | variants | size-policy |
|------|----------|-------------|
| card | basic/media/horizontal/stat/action/profile/pricing/selectable | intrinsic |
| nav-item | text/icon-text/badge/expandable/grouped/collapsed | intrinsic |
| breadcrumb | slash/icon/dropdown | flow |
| tab | underline/capsule/icon-box/vertical | flow |
| pagination | full/simple/with-page-size | intrinsic |
| list-item | arrow/avatar/actions/description/badge | flow |
| alert | info/success/warning/error/with-action | flow |
| stat-block | basic/trend/icon/chart/progress | intrinsic |
| search-bar | basic/filterable/with-tabs | token-derived |
| upload | dropzone/button/image-grid/file-list/avatar/multi-state | intrinsic |
| stepper | basic/description/toolbar/icon/dot/form-linked/vertical/dashboard | flow |
| date-picker | single/range/quick-range/year-month/datetime/week (Div 模拟) | intrinsic |
| attachment-card | inline/card/media-preview/list/grid | intrinsic |
| media-embed | map/link/video/gallery/code/quote | intrinsic |
| audio-waveform | standard/mini/bubble/spectrum | intrinsic |

## 3.3 Organisms

| 组件 | variants | size-policy |
|------|----------|-------------|
| header | basic/search/notification/breadcrumb/language/action-button | token-derived |
| sidebar | basic-expanded/with-submenu/with-badge/collapsed/with-search/with-user-zone/multi-level/dark-theme | token-derived |
| footer | minimal/links/multi-column/logo/admin | token-derived |
| form-section | vertical/horizontal/inline/grouped/card/stepper | flow |
| modal | confirm/danger/form/result/fullscreen/stepper | token-derived |
| empty-state | no-data/no-results/error/no-permission/welcome | intrinsic |
| loading | skeleton/spinner/progress-bar/button/inline | intrinsic |
| floating-dock | vertical/horizontal/top/labeled/collapsible | intrinsic |
| rich-editor | basic-reply/formatted/minimal/mention/with-preview | flow |
| contact-profile | panel/hover-card/list-item/grid-card/compact | token-derived |

## 3.4 Layout Primitives

page-header：归属 page-header-slot，结构固定（breadcrumb+title+actions）

## 3.5 Patterns（逐层声明，禁止当单一组件用）

| 模式 | 组成 |
|------|------|
| table-base | classic/striped/card/compact (.lumos-table) |
| table-toolbar | tab-filter+search+date-range+sort+batch+view-switch |
| table-cell-patterns | meta-lines/rich-notes/badge-group/status-dot/action-links/voided |
| table-views | expandable-row/card-grid/view-toggle (icon-only) |

---
---

# 第四章：前端 AI 组装协议

---

## 4.1 三方职责

| 角色 | 负责 | 不负责 |
|------|------|--------|
| Arch Agent/人 | 选 Layout·审核·填写锁定配置 | 不写代码 |
| Stitch | 生成 tokens·showcase·骨架 | 不做业务页面 |
| 前端 AI | 选组件·组装 content-slot | 不改 tokens·不创组件·不改 Layout |

## 4.2 组装流程

```
Step 1: 使用项目锁定的 Layout + Header + Sidebar + Footer（🔴 LOCKED）
Step 2: 评估 content-slot 需要哪些组件
Step 3: 对 🟡 CONTROLLED 决策按规则选择，声明理由
Step 4: 检查同类页面一致性
Step 5: 自由组合 content-slot + 填写交付说明
```

## 4.3 交付模板

```html
<!--
=== Page Delivery Note ===
【Layout】Layout 1 Classic Admin (🔴 LOCKED)
【Fixed Slots】header: variant=___ / sidebar: active="___" / page-header: breadcrumb+title
【CONTROLLED】table-base: ___ (reason) / table-toolbar: ___ (reason)
【Consistency】Same config as "___" page
【Content-slot】component list...
【Notes】None
-->
```

## 4.4 检查清单

```
□ 🔴 Layout/Header/Sidebar/Footer 使用锁定配置
□ 🔴 Tab/Pagination/DatePicker/SearchBar/Alert 使用锁定变体
□ 🔴 Token 合规，无硬编码，无 Tailwind，无外部资源，图标为 SVG
□ 🟡 CONTROLLED 决策声明理由 + 同类一致
□ 🟢 组件来自注册表，嵌套 ≤ 3，间距用 --space-*
□ ✅ page-header 完整 + 交付说明完整
```

## 4.5 验收评分（满分 100，≥85 通过）

🔴 Layout 15 | 🔴 LOCKED 组件 15 | 🔴 Token+技术 15 | 🟡 CONTROLLED 15 | 🟡 一致性 10 | 🟢 组装 10 | ✅ page-header 8 | ✅ 交付说明 7 | ⛔ 无违规 5

---
---

# 第五章：文件说明

---

| 文件 | 用途 | 使用者 |
|------|------|--------|
| 01-前端AI组装协议.md（本文件） | 全部规范+规则 | Arch Agent · 前端 AI |
| LUMOS-Global-Constraints.md | Stitch 全局约束（上传到工作面板） | Stitch |
| LUMOS-Step-Prompts.md | 17 条分步提示词 | Stitch |
| design-tokens.css + 20 个 showcase HTML | Stitch 生成的组件文件 | 前端 AI |

Stitch 生成的 20 个文件：design-tokens.css / buttons / form-controls / badges-avatars / cards / navigation / lists-alerts-stats / upload / steps / date-picker / table-base~showcase(5个) / sidebar-menu / header-footer / forms-modals-states / rich-components / layout-showcase / template-demo

目录结构由 Arch Agent 和人工确定，本系统不规定。

---
---

# 第六章：一致性锁定规则

---

## 6.1 锁定分级

| 级别 | 含义 | AI 权限 |
|------|------|---------|
| 🔴 LOCKED | 全项目一致 | 不得修改 |
| 🟡 CONTROLLED | 预定义选项按业务选，同类一致 | 可选，须声明理由 |
| 🟢 FREE | content-slot 自由组合 | 自主决定 |

## 6.2 🔴 LOCKED

- 骨架：Layout / Header / Sidebar / Footer / page-header 结构
- Token：全部 token 值
- 原子组件样式：Button/Input/Select/Badge/Alert/Avatar 等
- 交互模式：Tab/Pagination/DatePicker/SearchBar/Alert/View Toggle/表头/行 hover/Empty State/Loading

## 6.3 🟡 CONTROLLED

**表格**：base 形态 / cell 模式 / toolbar 控件 / Tab 筛选 / 行选择 — AI 按数据复杂度判断，同类页面配置一致
**表单**：layout 选择 — 按字段数量判断
**卡片/步骤**：按业务丰富度选，同页统计卡同一变体

## 6.4 🟢 FREE

content-slot 内组件选择/排列/数量/业务文案 — 仍受间距/嵌套/token 约束

## 6.5 AI 执行流程

使用锁定配置 → 评估 CONTROLLED → 检查同类一致 → 组合 content → 填写交付说明

## 6.6 项目锁定配置表（Arch Agent 填写）

```
==================== 🔴 PROJECT LOCK ====================
【Layout】________________
【Header】________________
【Sidebar】________________
【Footer】________________
【Tab】________________
【Pagination】________________
【Date Picker】________________
【Search Bar】________________
【Alert】________________
【Table View Toggle】icon-only（已锁死）
【Empty State】________________
【Loading】________________
==================== 填写后生效 ====================
```
