# Design System: 思链科技 MindLink v2.0

> MindLink 新媒体内容系统 · AI 驱动的内容生产与分发 SaaS
> 品牌：思链科技（Sichain Tech）
> 架构参照：Material Design 3 / Ant Design 5 / Arco Design

---

## 1. Visual Theme & Atmosphere

MindLink 是一家专注于人工智能与系统研发的技术企业，深耕人工智能、大数据、云计算及物联网等前沿技术领域。AI数字系统，视觉语言建立在"冷静的生产力"之上——大面积留白与克制的浅色背景承载高密度数据与创作流程，让界面退居幕后，把注意力还给创新本身。

排版构建整体骨架。Noto Sans SC 承担中文显示，Inter 承担英文，JetBrains Mono 承担数字与代码。大标题 32-40px 字重 600、行高 1.25、负字距 -0.01em；正文 14px 字重 400、行高 1.6。

色彩由 MindLink 蓝 `#3662EC` 主线驱动，仅出现在交互元素上。背景三层：`#F7F9FD`（页面）/ `#FFFFFF`（卡片）/ `#F5F8FF`（品牌区）。语义色仅用于状态反馈。

**Key Characteristics:**
- Noto Sans SC + Inter + JetBrains Mono 三通道排版
- 浅色三层背景：`#F7F9FD` / `#FFFFFF` / `#F5F8FF`
- 单一品牌色：MindLink Blue `#3662EC`
- 内联 SVG 图标：2px 描边、16/20/24 三档、无填充、`stroke="currentColor"`
- 两栏布局：左侧 220px 导航 + 右侧弹性工作区 + 顶部 64px 信息条
- 动效三档：120 / 200 / 320ms，缓动 default / out / spring，禁止无意义闪烁
- 阴影微蓝克制：`rgba(15,27,60,...)` 统一色调

---

## 2. Global Tokens（全局变量）

### 2.1 Color — Brand

| Token | 值 | Press | Hover | Disable | Bg | 用途 |
|-------|-----|-------|-------|---------|-----|------|
| `--brand` | `#3662EC` | `#2753D9` | `#4A74F0` | `#ADBDED` | `#EAEFFD` | 主按钮、链接、焦点环、选中态 |
| `--brand-deep` | `#0A34AA` | `#04288A` | `#2450C9` | `#7D94D4` | `#E8EEFF` | 标题、强调文字 |

### 2.2 Color — Semantic

| Token | 值 | Press | Hover | Disable | Bg | 用途 |
|-------|-----|-------|-------|---------|-----|------|
| `--success` | `#2DAC0C` | `#259C08` | `#53C736` | `#BCDEB4` | `#EFFFEB` | 成功、已发布、正向趋势 |
| `--danger` | `#FF4245` | `#E3272A` | `#FF6B6E` | `#FCCACB` | `#FFF2F2` | 错误、删除、下跌趋势 |
| `--warning` | `#FF8F1F` | `#E37D17` | `#FFB061` | `#F7DCC1` | `#FFF7F0` | 注意、待处理 |
| `--warning-soft` | `#FAC814` | `#E6B400` | `#FCD442` | `#FCEFC0` | `#FFFBEB` | 轻提示、温和警告 |

### 2.3 Color — Neutral / Gray（辅助色）

| Token | 值 | 用途 |
|-------|-----|------|
| `--text-1` | `#0F1B3C` | 主文字——标题、正文、表格主信息 |
| `--text-2` | `#3A4868` | 次级文字——卡片描述、次要段落 |
| `--text-3` | `#6B7A9C` | 三级文字——辅助说明、placeholder |
| `--text-4` | `#9BA7C3` | 四级文字——时间戳、禁用文字、元信息 |
| `--text-5` | `#C8D0E0` | 五级——弱化图标、列表辅助图标 |

### 2.4 Color — Surface & Line

| Token | 值 | 用途 |
|-------|-----|------|
| `--page-bg` | `#F7F9FD` | 页面底色（微蓝冷灰） |
| `--card-bg` | `#FFFFFF` | 卡片、模态、输入框底色 |
| `--brand-tint` | `#F5F8FF` | 品牌区底——引导区、AI 提示区 |
| `--brand-bg` | `#EAEFFD` | 选中态底——活跃行、活跃 tab |
| `--line` | `#E5EBF5` | 标准分割线、卡片边框 |
| `--line-soft` | `#EEF2FA` | 柔性分割线——表格行、次要边界 |
| `--line-brand` | `#D5DFFA` | 品牌边框——AI 卡片、品牌提示条 |
| `--line-danger` | `#FCCACB` | 错误边框——表单验证失败 |

### 2.5 Color — Dark Mode 映射

| Token | Light | Dark | 说明 |
|-------|-------|------|------|
| `--page-bg` | `#F7F9FD` | `#0B0F1E` | 页面底色 |
| `--card-bg` | `#FFFFFF` | `#161B2E` | 卡片底色 |
| `--brand` | `#3662EC` | `#4A74F0` | 深色亮度+5% |
| `--brand-bg` | `#EAEFFD` | `#1A2548` | 品牌底色 |
| `--text-1` | `#0F1B3C` | `#E8ECF4` | 主文字 |
| `--text-2` | `#3A4868` | `#9BA7C3` | 次文字 |
| `--text-3` | `#6B7A9C` | `#5A6585` | 三级文字 |
| `--line` | `#E5EBF5` | `#1E2440` | 分割线 |
| `--success` | `#2DAC0C` | `#34C914` | 深色亮度+8% |
| `--danger` | `#FF4245` | `#FF5A5D` | 深色亮度+6% |
| `--shadow` | alpha 原值 | alpha ×0.6 | 避免"黑洞" |

### 2.6 Shadow

| Token | 值 | 用途 |
|-------|-----|------|
| `--sh-sm` | `0 1px 2px rgba(15,27,60,.04), 0 1px 3px rgba(15,27,60,.06)` | 按钮、小控件 |
| `--sh` | `0 4px 12px rgba(15,27,60,.06), 0 2px 4px rgba(15,27,60,.04)` | 标准卡片 |
| `--sh-lg` | `0 12px 32px rgba(15,27,60,.08), 0 4px 12px rgba(15,27,60,.04)` | 浮层、下拉 |
| `--sh-xl` | `0 24px 56px rgba(15,27,60,.14), 0 10px 24px rgba(15,27,60,.08)` | 模态框 |
| `--sh-focus` | `0 0 0 3px rgba(54,98,236,.15)` | 键盘焦点 |

### 2.7 Typography

**Font Stack**
- 中文：`"Noto Sans SC", "PingFang SC", "Microsoft YaHei", sans-serif`
- 英文：`"Inter", -apple-system, BlinkMacSystemFont, sans-serif`
- 数字/代码：`"JetBrains Mono", "SF Mono", ui-monospace, Menlo, monospace`

| Role | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|--------|-------------|----------------|-------|
| Display Hero | 40px | 600 | 1.20 | -0.01em | hero 首屏 |
| Page Title | 32px | 600 | 1.25 | -0.005em | 页面主标题 |
| Section Heading | 24px | 600 | 1.30 | normal | 模块标题 |
| Card Title | 18px | 600 | 1.40 | normal | 卡片标题 |
| Subtitle | 16px | 500 | 1.50 | normal | 小节标题 |
| Body | 14px | 400 | 1.60 | normal | 标准正文 |
| Body Emphasis | 14px | 500 | 1.60 | normal | 强调正文 |
| Caption | 12px | 400 | 1.50 | normal | 辅助说明 |
| Micro | 11px | 500 | 1.40 | 0.02em | tag、元信息 |
| Data Display | 20-32px | 600 | 1.10 | normal | KPI 大数字（Mono） |
| Data Inline | 13px | 500 | 1.50 | normal | 表格数字（Mono） |

### 2.8 Spacing

基础单位 4px。Scale: 4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80。

### 2.9 Border Radius

| Token | 值 | 用途 |
|-------|-----|------|
| `2px` | Tag | 极小标签 |
| `4px` | Micro | 状态标签、小徽章 |
| `6px` | Compact | 图标按钮、小控件 |
| `8px` | Standard | 按钮、输入框、下拉 |
| `12px` | Card | 卡片、容器 |
| `16px` | Panel | 大面板、模态框 |
| `999px` | Pill | 筛选按钮、Switch |
| `50%` | Circle | 头像、圆点 |

### 2.10 Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| 0 Flat | 无阴影 + `1px solid --line-soft` | 表格行、分割区 |
| 1 Surface | `--sh-sm` | 按钮、输入框 |
| 2 Card | `--sh` | 卡片、看板模块 |
| 3 Popover | `--sh-lg` | 下拉菜单、tooltip |
| 4 Modal | `--sh-xl` | 模态框、抽屉 |
| Focus | `--sh-focus` | 键盘焦点、输入聚焦 |

---

## 3. Motion Tokens（动效系统）

### 3.1 时长 Duration — 三档

| Token | 值 | 用途 |
|-------|-----|------|
| `--dur-fast` | **120ms** | 色彩过渡、hover、switch、tab 切换 |
| `--dur-normal` | **200ms** | 标准进入/离开、卡片悬浮、列表切换（默认档） |
| `--dur-slow` | **320ms** | 模态、抽屉、折叠面板 |

### 3.2 缓动 Easing — 三种

| Token | 值 | 用途 |
|-------|-----|------|
| `--ease-default` | `cubic-bezier(0.4, 0, 0.2, 1)` | 对称加减速——hover、tab、透明度 |
| `--ease-out` | `cubic-bezier(0.16, 1, 0.3, 1)` | 指数减速——入场首选（MindLink 节奏签名） |
| `--ease-spring` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | 弹簧回弹——成功、勾选、选中反馈 |

> **90% 走 200ms + ease-out**，这是 MindLink 的默认节奏。

### 3.3 Principles

1. **禁止无意义闪烁抖动**——每个动效必须回答"用户得到了什么反馈"
2. **进出对称、离场更快**——离场时长比进场快 40%
3. **只动 transform / opacity**——GPU 加速，禁止动 width/height/top/left
4. **层级错位**——多元素同时出现用 stagger（delay 40-80ms），禁止"一齐弹出"
5. **尊重用户偏好**——`@media (prefers-reduced-motion: reduce)` 下全局降级

### 3.4 组件→动效映射

| 场景 | 动效 | 时长 | 曲线 |
|------|------|------|------|
| 按钮 hover | color + shadow | 120ms | ease-default |
| 按钮 active | scale(0.98) + bg | 120ms | ease-default |
| 按钮 ripple | ripple-expand | 600ms | linear |
| Tab 切换 | slider translateX + width | 200ms | ease-default |
| 卡片 hover | translateY(-2px) + shadow | 200ms | ease-out |
| 模态进入 | fade + scale(0.85→1) | 320ms | ease-spring |
| 模态退出 | fade + scale(1→0.96) | 200ms | ease-default |
| Toast 进入 | translateX(120%→0) | 200ms | ease-out |
| Drawer 进入 | translateX(100%→0) | 320ms | ease-out |
| 列表新增项 | spring-up + stagger | 200ms | ease-spring |
| 数字变化 | count-up | 1200ms | ease-out |
| 图表绘制 | path-draw / bar-grow | 800-1200ms | ease-out |
| 骨架屏 | shimmer | 1.4s | ease (loop) |
| Switch 切换 | thumb translate | 120ms | ease-default |
| Checkbox 勾选 | check-draw | 200ms | ease-spring |
| 折叠面板 | max-height | 320ms | ease-out |
| 环形进度 | stroke-dashoffset + count-up | 1200ms | ease-out(带 4% 过冲) |
| 步骤条当前 | box-shadow 呼吸脉冲 | 2s | ease-in-out (loop) |
| 内容切换 | crossfade opacity swap | 200ms | ease-out |
| AI 生成中 | typing cursor + gradient-flow | loop | — |
| 发布成功 | spring-in + confetti | 600ms | ease-spring |

### 3.5 动效清单（26 种）

按用途分 7 类：
- **入场 Entrance（5）**：弹性上移 · 逐字模糊入场 · 弹性缩放 · 列表错位入场 · 左侧滑入
- **反馈 Feedback（5）**：按钮涟漪 · 勾选绘制 · 脉冲提醒 · Tab 回弹 · 彩带庆祝
- **加载 Loading（4）**：旋转 · 骨架屏 shimmer · 进度条条纹 · AI 打字机
- **数据 Data（4）**：数字逐位滚动 · 柱图生长 · 线图描边 · 品牌底流动
- **交互 Interaction（4）**：悬浮上升 · 磁吸按钮 · 3D 倾斜 · 折叠展开
- **转场 Transition（4）**：模态弹出 · Toast 滑入 · 抽屉滑入 · 内容交叉淡入
- **聚焦 Input（1）**：聚焦光晕

---

## 4. Components — Buttons

### Primary Brand（主按钮）
- Background: `--brand` (#3662EC)
- Text: `#FFFFFF`
- Padding: 0 20px; Height: 36px; Radius: 8px
- Hover: bg `--brand-hover`, shadow `0 6px 16px rgba(54,98,236,.28)`, translateY(-1px)
- Active: bg `--brand-press`, translateY(0)
- Disabled: bg `--brand-disable`, cursor not-allowed, opacity 0.7
- Focus: `--sh-focus`

### Secondary Ghost（次按钮）
- Background: `#FFFFFF`; Text: `--brand`; Border: `1px solid --brand`
- Hover: bg `--brand-bg`

### Tertiary Plain（三级按钮）
- Background: transparent; Text: `--text-2`
- Hover: bg `--brand-tint`, text `--brand`

### Danger Ghost（危险-轮廓）
- Background: `#FFFFFF`; Text: `--danger`; Border: `1px solid --line-danger`
- Hover: bg `--danger-bg`

### **Danger Fill（危险-实心）** ← v2.0 新增
- Background: `--danger`; Text: `#FFFFFF`
- Hover: bg `--danger-hover`, shadow `0 6px 16px rgba(255,66,69,.28)`, translateY(-1px)
- Active: bg `--danger-press`
- Use: 确认删除弹窗中的红色主按钮

### **Loading（加载态）** ← v2.0 新增
- 基于 Primary 样式 + cursor: wait
- 内容: 14px spinner(白色) + "处理中..." 文字
- spinner: 14×14, border 2px solid rgba(255,255,255,0.3), border-top-color #fff, spin 0.8s linear infinite

### Pill Control（药丸筛选）
- 未选: bg `#FFFFFF`, text `--text-3`, border `1px solid --line`, radius 999px
- 选中: bg `--brand-bg`, text `--brand`, border `1px solid --brand`
- Active press: scale(0.96), 120ms

### Icon Button
- Size: 32×32(standard) / 28×28(compact); Radius: 6px
- Icon: 16-20px, `--text-3`; Hover: bg `--brand-tint`, icon `--brand`

---

## 5. Components — Cards

### Standard Card
- bg `#FFFFFF`, radius 12px, shadow `--sh`, padding 20-32px
- Hover(如可点击): translateY(-2px), shadow `--sh-lg`, 200ms ease-out

### Data Card（KPI 卡片）
- Label: 12px `--text-3` + trend tag(Success/Danger Bg)
- Value: 28-32px JetBrains Mono weight 600 `--text-1`
- 入场: stagger slide-up, 数字 count-up 1200ms

### Brand Card（AI 引导卡）
- bg: `linear-gradient(135deg, --brand-bg 0%, --brand-tint 100%)`
- border: `1px solid --line-brand`

### **Radio Card（可选中卡片）** ← v2.0 新增
- 未选: border `1.5px solid --line`, bg `#FFFFFF`
- 选中: border `--brand`, bg `--brand-bg`, shadow `0 0 0 3px rgba(54,98,236,0.1)`
- 内含 radio dot: 18×18 圆形，选中后内填 8px 品牌蓝实心圆

### Status Tags

| 类型 | Text | Background |
|------|------|-----------|
| Brand | `--brand` | `--brand-bg` |
| Success | `--success` | `--success-bg` |
| Danger | `--danger` | `--danger-bg` |
| Warning | `--warning` | `--warning-bg` |
| Warning Soft | `--warning-soft-press` | `--warning-soft-bg` |
| Neutral | `--text-3` | `--page-bg` |

Tags: height 22px, padding 0 8px, radius 4px, font 11-12px weight 500。

---

## 6. Components — Forms

### Text Input
- Height 36px, bg `#FFFFFF`, border `1px solid --line`, radius 8px
- Placeholder: `--text-4`
- Focus: border `--brand`, shadow `--sh-focus`
- Error: border `--danger`, shadow `0 0 0 3px rgba(255,66,69,.12)`

### **Select（下拉选择）** ← v2.0 细化
- 同 Text Input + 右侧 chevron SVG (10px, `--text-4`)
- 自定义 `appearance: none` + background-image SVG 箭头
- Focus: border `--brand`, shadow `--sh-focus`

### Textarea
- 同 Text Input，min-height 96px，padding 10px 12px

### Checkbox / Radio
- Size 16×16; Unchecked: `1px solid --line`, bg `#FFFFFF`
- Checked: bg `--brand`, white glyph; Checkbox radius 4px, Radio radius 50%

### **Radio Group** ← v2.0 新增
- 垂直排列，每项 gap 10px
- 每项: radio circle 16×16 + 13px label

### Switch / Toggle
- Track: 36×20px, bg `--line`(off) / `--brand`(on), radius 999px
- Thumb: 16×16 white circle, shadow-sm
- Transition: **120ms** ease-default ← v2.0 修正（原 180ms）

### Date Input
- 同 Text Input + `type="date"`, `color-scheme: light`

---

## 7. Components — Tabs ← 整章新增

### Pill Tabs（个人中心视图切换）
- 独立圆角药丸，每个可带数量 badge
- 未选: bg `#FFFFFF`, text `--text-2`, border `1px solid --line`
- 选中: bg `--brand`, text `#FFFFFF`, shadow `0 3px 10px rgba(54,98,236,0.25)`
- Active press: scale(0.96), 120ms
- Badge: 未选 bg `--page-bg` text `--text-3` / 选中 bg `rgba(255,255,255,0.25)` text `#FFFFFF`

### Segmented Pill（iOS 分段切换）
- 容器: bg `--page-bg`, padding 3px, radius 10px
- 选中项: bg `#FFFFFF`, text `--brand`, shadow `--sh-sm`
- **滑动指示器**: 白色 slider div，`transform: translateX()` + `width`, 200ms ease-default

### Underline Tabs（主工作区切换）
- gap 28px, border-bottom `1px solid --line`
- 未选: text `--text-3`, 14px weight 400
- 选中: text `--brand`, 14px weight 600
- **滑动指示器**: 2px 高品牌蓝 slider，`translateX` + `width`, 200ms ease-default
- 可带数字 badge: bg `--brand-bg`, text `--brand`, mono 10px

---

## 8. Components — Progress ← 整章新增

### Linear（线性进度）
- Track: height 8px(standard) / 4px(thin) / 12px(thick), bg `--line-soft`, radius 4px
- Fill: `linear-gradient(90deg, --brand 0%, --brand-hover 100%)`, radius 4px
- 语义变体: success / warning / danger 各自渐变
- **条纹动画**: `background-image: repeating-linear-gradient(135deg, ...)`, animation 1s linear infinite
- **不定态**: 40% 宽 fill 块，translateX(-40%→100%), 1.6s ease-default infinite

### Stepper（步骤条）
- Step circle: 32×32, radius 50%
- 已完成: bg `--brand`, text `#FFFFFF`, "✓"
- **当前**: bg `#FFFFFF`, border `2px solid --brand`, text `--brand`, **呼吸脉冲** box-shadow 4px↔8px, 2s ease-in-out infinite
- 未开始: bg `#FFFFFF`, border `2px solid --line`, text `--text-3`
- 连接线: height 2px, 已完成 `--brand` / 未完成 `--line`

### Circular（环形进度）
- SVG circle, r=44, stroke-width 6, `stroke-dasharray: 276.46`
- 入场动效链: ① 卡片 scale(0.85→1) spring 400ms stagger → ② 弧线 stroke-dashoffset 1200ms ease-out(4%过冲) → ③ 数字 count-up 1200ms(延迟 150ms)
- 成功态特殊: 先画满圆，再弹出勾选图标 (delay 900ms, spring)

### Segmented（分段进度）
- Dots: flex gap 4px, 每段 height 6px radius 3px
- 已完成 `--brand` / 当前 `--brand` + pulse 1.2s / 未完成 `--line-soft`

---

## 9. Components — Feedback ← 整章新增

### Toast（操作反馈）
- 白底卡片, radius 10px, shadow `--sh-lg`, padding 12px 16px
- 无左侧色条（v2.0 去除）
- 图标: 24×24 圆形语义色底 + 16×16 白色粗体内联 SVG
  - 信息: 蓝底 + 铃铛 (stroke-width 2.5)
  - 成功: 绿底 + 勾选 (stroke-width 3.5)
  - 失败: 红底 + X 叉 (stroke-width 3.5)
  - 警告: 橙底 + 感叹号 (stroke-width 3)
- 关闭: 14×14 X SVG, `--text-4`

### Alert（行内提示）
- 四种语义: info(--brand-bg) / success(--success-bg) / danger(--danger-bg) / warning(--warning-bg)
- 图标: 18×18 内联 SVG, **全部统一 18px** ← v2.0 对齐
- padding 14px 16px, radius 10px

### Confirm（确认弹窗）
- 居中卡片 max-width 360px, radius 14px, shadow `--sh-xl`
- 图标: 56×56 圆角方形容器(radius 14px) + 26px 内联 SVG
  - 删除: bg `--danger-bg`, color `--danger`, icon 垃圾桶
  - 发布: bg `--brand-bg`, color `--brand`, icon 火箭
- 按钮组: Secondary "取消" + Primary/Danger-Fill "确认"

### Notification（通知列表）
- 每项: padding 12px 14px, radius 10px, border `1px solid --line-soft`
- 未读: 蓝色圆点 8×8 `--brand` / 已读: 灰色圆点 `--line`
- Hover: bg `--page-bg`

---

## 10. Components — Empty States ← 整章新增

统一结构: 虚线边框卡片 (border: 1px dashed --line) + 居中图标 + 标题 + 描述 + 操作按钮

图标容器: 72×72, radius 18px, 32px 内联 SVG icon

| 场景 | 容器色 | 图标 | 按钮 |
|------|--------|------|------|
| 暂无内容 | bg `--brand-bg`, color `--brand` | file-list | Primary "创建项目" |
| 搜索无结果 | bg `--page-bg`, color `--text-3`, border `--line-soft` | search | Secondary "清除筛选" |
| 网络异常 | bg `--warning-bg`, color `--warning` | wifi-off | Secondary "重新加载" |
| 无权限 | bg `--danger-bg`, color `--danger` | lock | Secondary "联系管理员" |

---

## 11. Components — Navigation ← 整章新增

### Sidebar
- Width 220px, bg `#FFFFFF`, border-right `1px solid --line`
- Brand: 22×22 logo mark(渐变蓝圆角) + 14px 品牌名
- Section label: 10px mono uppercase `--text-4`, letter-spacing 0.08em
- Nav item: height 36px, padding 0 16px, 13px weight 400
- Active: bg `--brand-bg`, text `--brand`, left `3px solid --brand`
- Badge: bg `--danger-bg`, color `--danger`, mono 10px

### TopBar
- Height 64px, bg `#FFFFFF`, border-bottom `1px solid --line`
- Breadcrumb: 12px `--text-3`, current page `--text-2` weight 500
- Search: 30px height, radius 6px, bg `--page-bg`
- Avatar: 28×28 circle, 渐变品牌色底, 白字

---

## 12. Components — Table ← 整章新增

- 容器: bg `#FFFFFF`, border `1px solid --line-soft`, radius 12px
- Header: bg `--page-bg`, mono 11px uppercase weight 600 `--text-2`
- 排序箭头: 10px, 默认 `--text-4`, 激活 `--brand`
- Body: row 48px height, 13px body, border-bottom `--line-soft`
- Hover: bg `--brand-tint`
- Selected: bg `--brand-bg`, first-child `box-shadow: inset 3px 0 0 --brand`
- Checkbox: 16×16, accent-color `--brand`
- 数字列: `font-family: --font-mono; font-variant-numeric: tabular-nums; text-align: right`
- Pagination: 28×28 按钮, radius 6px, active bg `--brand` text `#FFFFFF`

---

## 13. Components — Modal & Drawer ← 整章新增

### Modal
- Backdrop: `rgba(15,27,60,0.35)`, backdrop-filter blur(4px), fade 200ms
- Panel: bg `#FFFFFF`, radius 14px, max-width 480px, shadow `--sh-xl`
- Header: 18px title weight 600, 分割线 `--line-soft`
- Footer: flex justify-end, gap 10px, Secondary + Primary
- 入场: scale(0.85→1), 320ms ease-spring
- 退场: scale(1→0.96) + fade, 200ms ease-default

### Drawer
- 右侧面板 width 340px, bg `#FFFFFF`, border-left `1px solid --line`
- 遮罩: `rgba(15,27,60,0.04)` ← 极轻遮罩
- 入场: translateX(100%→0), 320ms ease-out
- 退场: translateX(0→100%), 200ms ease-default

---

## 14. Components — Tooltip & Popover ← 整章新增

### Tooltip
- bg `--text-1`, text `#FFFFFF`, radius 6px, padding 6px 10px, font 11px weight 500
- 箭头: 6×6 旋转45°同色方块
- 四方向: top / bottom / left / right
- 入场: opacity 0→1 + translateY/X(4px→0), 120ms ease-out
- 触发: hover (纯 CSS)

### Popover（操作菜单）
- bg `#FFFFFF`, border `1px solid --line`, radius 10px, shadow `--sh-lg`, min-width 180px
- Menu item: padding 7px 10px, radius 6px, 13px, gap 8px (icon 14px + text)
- Hover: bg `--brand-tint`, text `--brand`
- Danger item hover: bg `--danger-bg`, text `--danger`
- 分割线: height 1px, bg `--line-soft`, margin 4px 0
- 入场: opacity 0→1, 200ms ease-out

---

## 15. Components — Avatar & Badge ← 整章新增

### Avatar 尺寸
- 24 / 32 / 40 / 48 px, radius 50%
- 默认: 渐变品牌蓝底 + 白色首字母

### 在线状态
- 10×10 圆点, border 2px solid #FFFFFF, 位于右下角
- online: `--success` / busy: `--danger` / offline: `--text-4`

### 头像堆叠
- margin-left: -8px, border 2px solid #FFFFFF
- 溢出计数: bg `--page-bg`, text `--text-3`, mono 11px "+N"

### Badge 角标
- 数字: min-width 16px, height 16px, bg `--danger`, text #FFFFFF, mono 10px weight 600, radius 8px, border 2px solid #FFFFFF
- 红点: 8×8, bg `--danger`, border 2px solid #FFFFFF

---

## 16. Components — Icons ← 整章新增

### 规范
- 内联 SVG（不使用字体图标 CDN，保证离线渲染）
- 统一属性: `fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"`
- 三档尺寸: 16px(列表/表格) / 20px(标准) / 24px(大图标)
- 颜色: 继承父级 `currentColor`

### 常用图标（18 个）
编辑 · 删除 · 搜索 · 新增 · 上传 · 下载 · 分享 · 查看 · 复制 · 时间 · AI星标 · 通知 · 设置 · 团队 · 数据 · 视频 · 排行 · 审核

### Toast 图标特殊规范
- 容器: 24×24 圆形语义色实心底
- 图标: 16×16, stroke `#FFFFFF`, stroke-width **3-3.5px**（比常规粗，小尺寸辨识度）

---

## 17. Responsive

### Breakpoints

| Name | Width | Sidebar | KPI 列数 |
|------|-------|---------|---------|
| Mobile | <640px | 隐藏 + 汉堡菜单 | 1 列 |
| Tablet | 640-1024px | 折叠 64px 图标 | 2 列 |
| Desktop S | 1024-1280px | 展开 220px | 2-4 列 |
| Desktop | 1280-1440px | 展开 220px | 4 列 |
| Wide | >1440px | max-width 1440px 居中 | 4 列 |

### Touch Targets
- 主按钮: 桌面 36px → 移动 44px
- 图标按钮: 桌面 32×32 → 移动 40×40
- 表格行: 桌面 48px → 移动卡片化(padding 16px)

### Collapsing Strategy
- Sidebar: 展开 → 图标折叠 → 汉堡抽屉
- KPI: 4 列 → 2 列 → 1 列
- 表格: 完整列 → 移动端卡片化(key-value 竖排)
- 数字展示: 32px → 移动端 24px
- 抽屉: 340px → 移动端全屏

---

## 18. Do's and Don'ts

### Do
- 主色 `#3662EC` 只用在交互元素上——按钮、链接、焦点、选中态
- 三层背景: `#F7F9FD`(页面) → `#FFFFFF`(卡片) → `#F5F8FF`(品牌区)
- 字体三通道: Noto Sans SC / Inter / JetBrains Mono
- 动效默认 **200ms ease-out**——MindLink 节奏签名
- 阴影单层微蓝: `rgba(15,27,60,...)`, 禁止多层堆叠
- 圆角四档为主: 4(tag) / 8(按钮) / 12(卡片) / 999(pill)
- 数字必须 count-up, 列表必须 stagger, 图表必须 path-draw
- 所有交互组件四态完备: hover / active / focus / disabled
- 图标统一内联 SVG, stroke currentColor, 不用字体图标 CDN
- 危险按钮实心态阴影用红色 `rgba(255,66,69,.28)`, 不用品牌蓝
- 响应 `prefers-reduced-motion`
- AI 模块必带 `--brand-bg → --brand-tint` 淡品牌渐变

### Don't
- 不要引入第二个品牌色
- 不要使用字重 700 以上（中文 700 显笨重）
- 不要让中文行高低于 1.5 或高于 1.8
- 不要用纯黑 `#000000` 做正文——用 `#0F1B3C`
- 不要让 hover 动效超过 200ms
- 不要给 Toast 加左侧色条（v2.0 已移除，保持白底干净）
- 不要用字体图标 CDN（国内加载不稳定，全部内联 SVG）
- 不要在数字列用可变宽字体
- 不要给卡片加多层阴影

---

## 19. Agent Prompt Guide

### Quick Color Reference
```
Brand: #3662EC · Press: #2753D9 · Hover: #4A74F0 · Bg: #EAEFFD
Deep:  #0A34AA · Page: #F7F9FD · Card: #FFFFFF · Tint: #F5F8FF
T-1: #0F1B3C · T-2: #3A4868 · T-3: #6B7A9C · T-4: #9BA7C3 · T-5: #C8D0E0
Line: #E5EBF5 · Line-soft: #EEF2FA · Focus: 0 0 0 3px rgba(54,98,236,.15)
Success: #2DAC0C · Danger: #FF4245 · Warning: #FF8F1F · Warn-soft: #FAC814
```

### Quick Motion Reference
```
Duration:  120ms (fast) · 200ms (normal/default) · 320ms (slow)
Easing:    ease-default(.4,0,.2,1) · ease-out(.16,1,.3,1) · ease-spring(.34,1.56,.64,1)
Default:   200ms ease-out
Card lift: translateY(-2px) + shadow-lg, 200ms
Modal:     scale 0.85→1, 320ms spring
Stagger:   each delay 40-80ms
```

### Example Component Prompts

- **Primary Button**: "bg #3662EC, text white, 14px Inter weight 500, 36px height, 20px h-padding, 8px radius. Hover: bg #4A74F0 + shadow 0 6px 16px rgba(54,98,236,.28) + translateY(-1px). Active: bg #2753D9. Transition 120ms ease-default."

- **Danger Fill Button**: "bg #FF4245, text white, 8px radius. Hover: bg #FF6B6E + shadow 0 6px 16px rgba(255,66,69,.28). Active: bg #E3272A. 绝不使用蓝色阴影。"

- **KPI Card**: "#FFFFFF bg, 12px radius, 24px padding, shadow 0 4px 12px rgba(15,27,60,.06). Label 12px #6B7A9C. Number 32px JetBrains Mono weight 600 #0F1B3C. Trend tag #EFFFEB bg #2DAC0C text. 入场 stagger slide-up 200ms spring, 数字 count-up 1200ms."

- **Sidebar**: "220px width, #FFFFFF bg, right border 1px #E5EBF5. Section label 10px mono uppercase #9BA7C3. Nav item 36px height, 13px. Active: bg #EAEFFD, text #3662EC, left 3px solid #3662EC. Transition 120ms ease-default."

- **Table**: "Header: #F7F9FD bg, mono 11px uppercase #3A4868. Body: 48px row, 13px, border-bottom #EEF2FA. Hover: #F5F8FF. Selected: #EAEFFD + inset 3px #3662EC. Numeric: JetBrains Mono right-aligned. Pagination 28px btns."

- **Toast**: "白底卡片, radius 10px, shadow-lg. 无左侧色条。24px 圆形语义色底 + 16px 白色粗体 SVG 图标(stroke-width 3+)。信息=铃铛/成功=勾选/失败=叉/警告=感叹号。"

- **Modal**: "Backdrop rgba(15,27,60,0.35) + blur(4px). Panel #FFFFFF, 14px radius, max-width 480px, shadow-xl. 入场 scale 0.85→1, 320ms spring."

- **Circular Progress**: "SVG circle r=44, stroke-width 6, stroke-dasharray 276.46. 入场: ① 卡片 scale(0.85→1) spring stagger → ② 弧线描边 1200ms ease-out(4%过冲) → ③ 数字 count-up 同步。成功态先画满圆再弹勾选(delay 900ms)。"

### Iteration Guide
1. 交互元素 = `#3662EC`，无例外
2. 背景三层: `#F7F9FD` → `#FFFFFF` → `#F5F8FF`
3. 字体三通道: Noto Sans SC / Inter / JetBrains Mono
4. 动效默认 **200ms ease-out**
5. 阴影单层微蓝、圆角四档(4/8/12/999)
6. 危险操作: 红色阴影 `rgba(255,66,69,.28)`, 不用蓝色
7. 图标: 内联 SVG + currentColor, 不用 CDN 字体图标
8. Tab 切换: 滑动指示器 200ms ease-default
9. 四态完备: hover / active / focus / disabled
10. 尊重 `prefers-reduced-motion`

---

**版本**：v2.0 · 2026-04-17
**适用产品**：思链智能管理系统（DOCK管理系统）
**品牌主体**：思链科技（MindLink）
**维护**：闫霞
**架构参照**：Material Design 3 · Ant Design 5 · Arco Design
