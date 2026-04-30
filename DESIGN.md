# Design System: 思链科技 MindLink v2.0

> MindLink 新媒体内容系统 · AI 驱动的内容生产与分发 SaaS
> 品牌：思链科技（Sichain Tech）
> 架构参照：Material Design 3 / Ant Design 5 / Arco Design

---

## 1. Visual Theme & Atmosphere

MindLink 是一家专注于人工智能与系统研发的技术企业，深耕人工智能、大数据、云计算及物联网等前沿技术领域。AI数字系统，视觉语言建立在"冷静的生产力"之上——大面积留白与克制的浅色背景承载高密度数据与创作流程，让界面退居幕后，把注意力还给创新本身。

排版构建整体骨架。Noto Sans SC（Web 优先，PingFang SC / Microsoft YaHei 兜底）承担中文显示，保证跨端视觉一致，Inter 承担英文，Geist Mono 承担数字与代码。大标题 32-40px 字重 600、行高 1.25、负字距 -0.01em；正文 14px 字重 400、行高 1.6。

色彩由 MindLink 蓝 `#3662EC` 主线驱动，仅出现在交互元素上。背景三层：`#F7F9FD`（页面）/ `#FFFFFF`（卡片）/ `#F5F8FF`（品牌区）。语义色仅用于状态反馈。

**Key Characteristics:**
- Noto Sans SC（Web 优先）+ Inter + Geist Mono 三通道排版
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
| `--du-brand` | `#3662EC` | `#2753D9` | `#4A74F0` | `#ADBDED` | `#EAEFFD` | 主按钮、链接、焦点环、选中态 |
| `--du-brand-deep` | `#0A34AA` | `#04288A` | `#2450C9` | `#7D94D4` | `#E8EEFF` | 标题、强调文字 |

### 2.2 Color — Semantic

| Token | 值 | Press | Hover | Disable | Bg | 用途 |
|-------|-----|-------|-------|---------|-----|------|
| `--du-success` | `#2DAC0C` | `#259C08` | `#53C736` | `#BCDEB4` | `#EFFFEB` | 成功、已发布、正向趋势 |
| `--du-danger` | `#FF4245` | `#E3272A` | `#FF6B6E` | `#FCCACB` | `#FFF2F2` | 错误、删除、下跌趋势 |
| `--du-warning` | `#FF8F1F` | `#E37D17` | `#FFB061` | `#F7DCC1` | `#FFF7F0` | 注意、待处理 |
| `--du-warning-soft` | `#FAC814` | `#E6B400` | `#FCD442` | `#FCEFC0` | `#FFFBEB` | 轻提示、温和警告 |

### 2.3 Color — Neutral / Gray（辅助色）

| Token | 值 | 用途 |
|-------|-----|------|
| `--du-text-1` | `#0F1B3C` | 主文字——标题、正文、表格主信息 |
| `--du-text-2` | `#3A4868` | 次级文字——卡片描述、次要段落 |
| `--du-text-3` | `#6B7A9C` | 三级文字——辅助说明、placeholder |
| `--du-text-4` | `#9BA7C3` | 四级文字——时间戳、禁用文字、元信息 |
| `--du-text-5` | `#C8D0E0` | 五级——弱化图标、列表辅助图标 |

### 2.4 Color — Surface & Line

| Token | 值 | 用途 |
|-------|-----|------|
| `--du-page-bg` | `#F7F9FD` | 页面底色（微蓝冷灰） |
| `--du-card-bg` | `#FFFFFF` | 卡片、模态、输入框底色 |
| `--du-brand-tint` | `#F5F8FF` | 品牌区底——引导区、AI 提示区 |
| `--du-brand-bg` | `#EAEFFD` | 选中态底——活跃行、活跃 tab |
| `--du-line` | `#E5EBF5` | 标准分割线、卡片边框 |
| `--du-line-soft` | `#EEF2FA` | 柔性分割线——表格行、次要边界 |
| `--du-line-brand` | `#D5DFFA` | 品牌边框——AI 卡片、品牌提示条 |
| `--du-line-danger` | `#FCCACB` | 错误边框——表单验证失败 |

### 2.5 Color — Dark Mode 映射

| Token | Light | Dark | 说明 |
|-------|-------|------|------|
| `--du-page-bg` | `#F7F9FD` | `#0B0F1E` | 页面底色 |
| `--du-card-bg` | `#FFFFFF` | `#161B2E` | 卡片底色 |
| `--du-brand` | `#3662EC` | `#4A74F0` | 深色亮度+5% |
| `--du-brand-bg` | `#EAEFFD` | `#1A2548` | 品牌底色 |
| `--du-text-1` | `#0F1B3C` | `#E8ECF4` | 主文字 |
| `--du-text-2` | `#3A4868` | `#9BA7C3` | 次文字 |
| `--du-text-3` | `#6B7A9C` | `#5A6585` | 三级文字 |
| `--du-line` | `#E5EBF5` | `#1E2440` | 分割线 |
| `--du-success` | `#2DAC0C` | `#34C914` | 深色亮度+8% |
| `--du-danger` | `#FF4245` | `#FF5A5D` | 深色亮度+6% |
| `--du-sh*` (全套阴影) | alpha 原值 | alpha ×0.6 | 避免"黑洞" |

### 2.6 Shadow

| Token | 值 | 用途 |
|-------|-----|------|
| `--du-sh-sm` | `0 1px 2px rgba(15,27,60,.04), 0 1px 3px rgba(15,27,60,.06)` | 按钮、小控件 |
| `--du-sh` | `0 4px 12px rgba(15,27,60,.06), 0 2px 4px rgba(15,27,60,.04)` | 标准卡片 |
| `--du-sh-lg` | `0 12px 32px rgba(15,27,60,.08), 0 4px 12px rgba(15,27,60,.04)` | 浮层、下拉 |
| `--du-sh-xl` | `0 24px 56px rgba(15,27,60,.14), 0 10px 24px rgba(15,27,60,.08)` | 模态框 |
| `--du-sh-focus` | `0 0 0 3px rgba(54,98,236,.15)` | 键盘焦点 |

### 2.7 Typography

**Font Stack**（v2.0 调整 · 2026-04-30）
- 中文（**Web 字体优先**）：`"Noto Sans SC", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif`
- 英文：`"Inter", -apple-system, BlinkMacSystemFont, sans-serif`
- 数字/代码：`"Geist Mono", "JetBrains Mono", "SF Mono", ui-monospace, Menlo, monospace`

**说明**：
1. **中文 Web 字体优先**——`Noto Sans SC`（Google 出品，OFL 开源，Variable Font）作为头位，**保证 Mac / Windows / Linux 所有平台视觉完全一致**——这对设计师跨设备评审、产品截图归档、用户口碑统一至关重要；如 Web 字体加载失败，降级到 macOS/iOS 的 `PingFang SC` → 老 Mac 的 `Hiragino Sans GB` → Windows 的 `Microsoft YaHei`。一次 woff2 加载（~600KB，浏览器缓存后零成本）换取永久跨端一致。
2. **Geist Mono 替换 JetBrains Mono**——Geist Mono（Vercel 2023，OFL）在 KPI 大数字、Token 名、时间戳等场景比 JetBrains Mono 更克制现代；保留 JetBrains Mono 作为二级 fallback 兼容老页面。
3. **Inter 保留**——已是 OFL 开源、Variable Font、SaaS 行业标杆，无需替换。

| Role | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|--------|-------------|----------------|-------|
| Display Hero | 40px | 600 | 1.20 | -0.01em | hero 首屏 |
| Page Title | 32px | 600 | 1.25 | -0.005em | 页面主标题 |
| Section Heading | 24px | 600 | 1.30 | normal | 模块标题 |
| Card Title | 18px | 600 | 1.40 | normal | 卡片标题 |
| Subtitle | 16px | 500 | 1.50 | normal | 小节标题 |
| Body | 14px | 400 | 1.60 | normal | 标准正文 |
| Body Emphasis | 14px | 500 | 1.60 | normal | 强调正文 |
| Caption | 12px | 400 | 1.50 | normal | 辅助说明、tag、元信息（**桌面端字号最低值**） |
| Data Display | 20-32px | 600 | 1.10 | normal | KPI 大数字（Mono） |
| Data Inline | 13px | 500 | 1.50 | normal | 表格数字（Mono） |

> **🔒 桌面端最小字号 = 12px（`--du-fs-xs`）**
> 9 / 10 / 11px 在 1080p+ 桌面屏幕上视觉过密、可读性差，已废弃。Caption / 状态标签 / mono 元数据等小号场景统一用 12px。原有 11px Micro 档已并入 Caption。WCAG 2.1 AA 也要求正文 ≥ 12px 才不强制放大。
> 移动端在 ≤ 430px 视口下可临时降至 11px（仅元信息），见 §17 Responsive。

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
| 0 Flat | 无阴影 + `1px solid --du-line-soft` | 表格行、分割区 |
| 1 Surface | `--du-sh-sm` | 按钮、输入框 |
| 2 Card | `--du-sh` | 卡片、看板模块 |
| 3 Popover | `--du-sh-lg` | 下拉菜单、tooltip |
| 4 Modal | `--du-sh-xl` | 模态框、抽屉 |
| Focus | `--du-sh-focus` | 键盘焦点、输入聚焦 |

### 2.11 Backdrop · 模态遮罩（v2.0 新增）

```css
:root {
  --du-backdrop-blur:        8px;                       /* 默认模糊半径 */
  --du-backdrop-blur-light:  4px;                       /* 轻量浮层（Drawer / 侧滑面板）*/
  --du-backdrop-blur-heavy:  16px;                      /* 强沉浸（图片预览 / 全屏 Modal）*/

  --du-modal-backdrop:       rgba(15,27,60,.35);        /* 浅色 · 半透明 + 模糊 */
  --du-modal-backdrop-dark:  rgba(0,0,0,.50);           /* 深色 · 因暗底已够暗，模糊半径相同 */
}
```

**应用规则**：所有"打开后会盖住主页面"的浮层（Modal / Dialog / Drawer / Image Preview / MessageBox / 全屏 Loading）都**必须**用 `backdrop-filter: blur(var(--du-backdrop-blur))` + 半透明蒙层。

**为什么**：
1. 模糊创造视觉层级（前景清晰 vs 背景虚化），符合人眼对焦逻辑
2. 半透明色块本身能保证视觉降噪，但纯色块会"吃掉信息"；模糊保留了背景结构感
3. 对比度合规：模糊后即使背景内容仍隐约可见，也不会干扰前景文字阅读

**禁用场景**：
- 性能敏感页面（特别老旧机型 / 大量列表后台）可降级为纯色不透明遮罩 `rgba(15,27,60,.6)`，但必须配 `prefers-reduced-transparency` 媒体查询自动切换

```css
@media (prefers-reduced-transparency: reduce) {
  .modal-overlay {
    backdrop-filter: none;
    background: rgba(15,27,60,.6);
  }
}
```

---

## 3. Motion Tokens（动效系统）

### 3.1 时长 Duration — 三档

| Token | 值 | 用途 |
|-------|-----|------|
| `--du-dur-fast` | **120ms** | 色彩过渡、hover、switch、tab 切换 |
| `--du-dur-normal` | **200ms** | 标准进入/离开、卡片悬浮、列表切换（默认档） |
| `--du-dur-slow` | **320ms** | 模态、抽屉、折叠面板 |

### 3.2 缓动 Easing — 三种

| Token | 值 | 用途 |
|-------|-----|------|
| `--du-ease-default` | `cubic-bezier(0.4, 0, 0.2, 1)` | 对称加减速——hover、tab、透明度 |
| `--du-ease-out` | `cubic-bezier(0.16, 1, 0.3, 1)` | 指数减速——入场首选（MindLink 节奏签名） |
| `--du-ease-spring` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | 弹簧回弹——成功、勾选、选中反馈 |

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
- Background: `--du-brand` (#3662EC)
- Text: `#FFFFFF`
- Padding: 0 20px; Height: 36px; Radius: 8px
- Hover: bg `--du-brand-hover`, shadow `0 6px 16px rgba(54,98,236,.28)`, translateY(-1px)
- Active: bg `--du-brand-press`, translateY(0)
- Disabled: bg `--du-brand-disable`, cursor not-allowed, opacity 0.7
- Focus: `--du-sh-focus`

### Secondary Ghost（次按钮）
- Background: `#FFFFFF`; Text: `--du-brand`; Border: `1px solid --du-brand`
- Hover: bg `--du-brand-bg`

### Tertiary Plain（三级按钮）
- Background: transparent; Text: `--du-text-2`
- Hover: bg `--du-brand-tint`, text `--du-brand`

### Danger Ghost（危险-轮廓）
- Background: `#FFFFFF`; Text: `--du-danger`; Border: `1px solid --du-line-danger`
- Hover: bg `--du-danger-bg`

### **Danger Fill（危险-实心）** ← v2.0 新增
- Background: `--du-danger`; Text: `#FFFFFF`
- Hover: bg `--du-danger-hover`, shadow `0 6px 16px rgba(255,66,69,.28)`, translateY(-1px)
- Active: bg `--du-danger-press`
- Use: 确认删除弹窗中的红色主按钮

### **Loading（加载态）** ← v2.0 新增
- 基于 Primary 样式 + cursor: wait
- 内容: 14px spinner(白色) + "处理中..." 文字
- spinner: 14×14, border 2px solid rgba(255,255,255,0.3), border-top-color #fff, spin 0.8s linear infinite

### Pill Control（药丸筛选）
- 未选: bg `#FFFFFF`, text `--du-text-3`, border `1px solid --du-line`, radius 999px
- 选中: bg `--du-brand-bg`, text `--du-brand`, border `1px solid --du-brand`
- Active press: scale(0.96), 120ms

### Icon Button
- Size: 32×32(standard) / 28×28(compact); Radius: 6px
- Icon: 16-20px, `--du-text-3`; Hover: bg `--du-brand-tint`, icon `--du-brand`

---

## 5. Components — Cards

### Standard Card
- bg `#FFFFFF`, radius 12px, shadow `--du-sh`, padding 20-32px
- Hover(如可点击): translateY(-2px), shadow `--du-sh-lg`, 200ms ease-out

### Data Card（KPI 卡片）
- Label: 12px `--du-text-3` + trend tag(Success/Danger Bg)
- Value: 28-32px Geist Mono weight 600 `--du-text-1`
- 入场: stagger slide-up, 数字 count-up 1200ms

### Brand Card（AI 引导卡）
- bg: `linear-gradient(135deg, --du-brand-bg 0%, --du-brand-tint 100%)`
- border: `1px solid --du-line-brand`

### **Radio Card（可选中卡片）** ← v2.0 新增
- 未选: border `1.5px solid --du-line`, bg `#FFFFFF`
- 选中: border `--du-brand`, bg `--du-brand-bg`, shadow `0 0 0 3px rgba(54,98,236,0.1)`
- 内含 radio dot: 18×18 圆形，选中后内填 8px 品牌蓝实心圆

### Status Tags

| 类型 | Text | Background |
|------|------|-----------|
| Brand | `--du-brand` | `--du-brand-bg` |
| Success | `--du-success` | `--du-success-bg` |
| Danger | `--du-danger` | `--du-danger-bg` |
| Warning | `--du-warning` | `--du-warning-bg` |
| Warning Soft | `--du-warning-soft-press` | `--du-warning-soft-bg` |
| Neutral | `--du-text-3` | `--du-page-bg` |

Tags: height 22px, padding 0 8px, radius 4px, font 11-12px weight 500。

---

## 6. Components — Forms

### Text Input
- Height 36px, bg `#FFFFFF`, border `1px solid --du-line`, radius 8px
- **Placeholder 颜色必须 `var(--du-text-4)`（#9BA7C3）**——禁止依赖浏览器默认（默认值是 input color 的 60% 不透明度，跨浏览器不一致，且 Chrome/Safari 会偏暗）
- Focus: border `--du-brand`, shadow `--du-sh-focus`
- Error: border `--du-danger`, shadow `0 0 0 3px rgba(255,66,69,.12)`

**全局规则**（必须在每个使用 input/textarea 的页面 `<style>` 顶部注入）：
```css
input::placeholder,
textarea::placeholder { color: var(--du-text-4); }
```
这条放在 `* { box-sizing }` 重置之后，相当于一个全局 baseline，避免每个具体 input 类都要重写一遍。

### **Select（下拉选择）** ← v2.0 全量重设计

> ⚠️ **不允许使用 native `<select>`**——原生 dropdown panel 由 OS 控制（Mac/Windows 表现完全不同），无法应用 MindLink 视觉。必须用自定义 `.du-select` 组件，或在 Element Plus 项目中用 `<el-select>`（已通过 element-theme.css 主题映射自动达标）。

**Trigger（触发按钮）**
- 高度 `--du-input-h` (32px) · padding 0 12px · radius `--du-radius-lg` (8px)
- bg `--du-card-bg` · border `1px solid --du-line` · color `--du-text-1`
- Hover: border `--du-text-4`
- Focus / Open: border `--du-brand` + shadow `--du-sh-focus`（品牌焦点环）
- Placeholder 状态: color `--du-text-4`
- 右侧 chevron SVG 14px stroke 2px `--du-text-3`，open 时旋转 180° 并变品牌色 `--du-brand`

**Panel（下拉面板）**
- 位置：trigger 下方 4px gap，宽度撑满 trigger
- bg `--du-card-bg` · radius `--du-radius-lg` (8px) · border `1px solid --du-line` · shadow `--du-sh-lg`
- padding 4px · max-height 240px（超出滚动）· z-index `--du-z-dropdown` (1000)
- 入场: opacity 0→1 + translateY(-4px)→0 + scale(0.98)→1，120ms ease-default
- 退场: 反向 120ms

**Option（选项）**
- 高度 32px · padding 0 8px · radius `--du-radius-md` (6px)
- 字号 `--du-fs-sm` (13px) · color `--du-text-1`
- **Hover**: bg `--du-brand-tint`（极轻品牌底，**不要用 hover-overlay**——下拉面板应给用户清晰指向）
- **Selected**: bg `--du-brand-bg` + color `--du-brand` + weight 500 + 右侧品牌色对勾 SVG（14px stroke 3）
- **Disabled**: color `--du-text-4` · cursor not-allowed
- 选项之间无 border，靠 padding 视觉分组；分组间用 `--du-select-divider`（1px `--du-line-soft`，上下 4px margin）

**Group Label（分组标签）· 可选**
- padding 6px 8px 4px · font-mono 11px uppercase letter-spacing 0.06em · color `--du-text-4`

**交互行为**
- 点击 trigger 切换 open/close
- 选中 option 后立即关闭 panel
- 点击 panel 外区域关闭
- ESC 键关闭
- 焦点环用 keyboard 导航时显示（`focus-visible`）

**禁忌**
- ❌ 不允许 native `<select>` 直接出现在生产页面
- ❌ 不要用 `border-left: 3px solid var(--du-brand)` 这种左侧色条做选中态（违反 §18 Don't）
- ❌ 选中态不要用 `background: var(--du-brand)` 实色——会与悬停按钮视觉撞色，应用浅 bg `--du-brand-bg`

### Textarea
- 同 Text Input，min-height 96px，padding 10px 12px

### Checkbox / Radio
- Size 16×16; Unchecked: `1px solid --du-line`, bg `#FFFFFF`
- Checked: bg `--du-brand`, white glyph; Checkbox radius 4px, Radio radius 50%

### **Radio Group** ← v2.0 新增
- 垂直排列，每项 gap 10px
- 每项: radio circle 16×16 + 13px label

### Switch / Toggle
- Track: 36×20px, bg `--du-line`(off) / `--du-brand`(on), radius 999px
- Thumb: 16×16 white circle, shadow-sm
- Transition: **120ms** ease-default ← v2.0 修正（原 180ms）

### Date Input · 日历选择 ← v2.0 全量重设计

> ⚠️ **不允许使用 native `<input type="date">`**——原生日历由 OS 控制，Mac/Windows 完全不同视觉。生产用 Element Plus `<el-date-picker>`（已通过 element-theme.css 主题映射达标），静态预览用自定义 `.du-date-picker`（视觉对齐 Element + MindLink 风）。

**Trigger（输入框）**
- 完全等同 Text Input：32px 高、`--du-radius-lg` 圆角、`--du-line` 边框
- 显示格式 `YYYY-MM-DD` · 字体 `--du-font-mono`（数字等宽、不跳）
- 右侧日历图标 16px stroke 2，open 时变品牌色
- Open / Focus 时 border `--du-brand` + `--du-sh-focus`

**Panel（日历面板）**
- **宽度自适应 trigger**（width: 100%）· 但 `min-width: 280px`（最窄保 7 列日期可读）· `max-width: 360px`（防超宽）
- bg `--du-card-bg` · radius `--du-radius-xl` (12px) · border `1px solid --du-line` · shadow `--du-sh-lg`
- padding 12px · z-index `--du-z-dropdown`
- 入场: opacity 0→1 + translateY(-4px)→0 + scale(0.98)→1，120ms ease-default

**Header**
- 5 个按钮：« 上一年 / ‹ 上一月 / 月份标题（点击切换月/年视图）/ › 下一月 / » 下一年
- 标题字号 `--du-fs-sm` weight 500
- 导航按钮 24×24 圆角 `--du-radius-md`，hover 浅品牌底
- 下方 1px `--du-line-soft` 分割线 + 8px gap

**Day Grid**
- 7 列表格 · `table-layout: fixed`
- 表头：周一到周日，11px 灰字 `--du-text-4`
- 单元格：28×28 圆形（`border-radius: 50%`），数字 `--du-fs-sm` font-mono
- 状态：
  - 默认：text `--du-text-1`
  - Hover：bg `--du-brand-bg`，text `--du-brand`
  - 上 / 下月日期 (`.muted`)：text `--du-text-4`
  - 周末 (`.weekend`)：text `--du-text-3`（区分但不抢眼）
  - 今天 (`.today`)：内描边 `inset 0 0 0 1px --du-brand` + text `--du-brand` + weight 600
  - 选中 (`.selected`)：实色 bg `--du-brand` + text `#fff` + weight 500
  - 禁用 (`.disabled`)：text `--du-text-4` + bg `--du-line-soft`

**Footer**
- 左：清除（灰字链接）· 右：今天（品牌色链接）
- 上方 1px `--du-line-soft` 分割线
- 链接 hover 加浅 bg

**Element Plus 集成**
- 在 `el-date-picker` 上加 `style="width: 100%"` 让 trigger 宽度跟父级
- 加 `popper-class="du-date-popper"` 让 panel 宽度跟随 trigger（默认 Element 是固定 322px）
- `element-theme.css` 已提供：

```css
.du-date-popper.el-popper {
  min-width: 280px;
}
.du-date-popper .el-date-picker {
  width: 100% !important;
}
```

**禁忌**
- ❌ 不允许 native `<input type="date">` 出现在生产代码
- ❌ 不要让选中态和今天态同时出现（视觉混乱）：选中态优先级高于今天态
- ❌ 不要在选中单元格上加 `border-radius: 0`（违反规范圆形单元格）

---

## 7. Components — Tabs ← 整章新增

### Pill Tabs（个人中心视图切换）
- 独立圆角药丸，每个可带数量 badge
- 未选: bg `#FFFFFF`, text `--du-text-2`, border `1px solid --du-line`
- 选中: bg `--du-brand`, text `#FFFFFF`, shadow `0 3px 10px rgba(54,98,236,0.25)`
- Active press: scale(0.96), 120ms
- Badge: 未选 bg `--du-page-bg` text `--du-text-3` / 选中 bg `rgba(255,255,255,0.25)` text `#FFFFFF`

### Segmented Pill（iOS 分段切换）
- 容器: bg `--du-page-bg`, padding 3px, radius 10px
- 选中项: bg `#FFFFFF`, text `--du-brand`, shadow `--du-sh-sm`
- **滑动指示器**: 白色 slider div，`transform: translateX()` + `width`, 200ms ease-default

### Underline Tabs（主工作区切换）
- gap 28px, border-bottom `1px solid --du-line`
- 未选: text `--du-text-3`, 14px weight 400
- 选中: text `--du-brand`, 14px weight 600
- **滑动指示器**: 2px 高品牌蓝 slider，`translateX` + `width`, 200ms ease-default
- 可带数字 badge: bg `--du-brand-bg`, text `--du-brand`, mono 10px

---

## 8. Components — Progress ← 整章新增

### Linear（线性进度）
- Track: height 8px(standard) / 4px(thin) / 12px(thick), bg `--du-line-soft`, radius 4px
- Fill: `linear-gradient(90deg, --du-brand 0%, --du-brand-hover 100%)`, radius 4px
- 语义变体: success / warning / danger 各自渐变
- **条纹动画**: `background-image: repeating-linear-gradient(135deg, ...)`, animation 1s linear infinite
- **不定态**: 40% 宽 fill 块，translateX(-40%→100%), 1.6s ease-default infinite

### Stepper（步骤条）
- Step circle: 32×32, radius 50%
- 已完成: bg `--du-brand`, text `#FFFFFF`, "✓"
- **当前**: bg `#FFFFFF`, border `2px solid --du-brand`, text `--du-brand`, **呼吸脉冲** box-shadow 4px↔8px, 2s ease-in-out infinite
- 未开始: bg `#FFFFFF`, border `2px solid --du-line`, text `--du-text-3`
- 连接线: height 2px, 已完成 `--du-brand` / 未完成 `--du-line`

### Circular（环形进度）
- SVG circle, r=44, stroke-width 6, `stroke-dasharray: 276.46`
- 入场动效链: ① 卡片 scale(0.85→1) spring 400ms stagger → ② 弧线 stroke-dashoffset 1200ms ease-out(4%过冲) → ③ 数字 count-up 1200ms(延迟 150ms)
- 成功态特殊: 先画满圆，再弹出勾选图标 (delay 900ms, spring)

### Segmented（分段进度）
- Dots: flex gap 4px, 每段 height 6px radius 3px
- 已完成 `--du-brand` / 当前 `--du-brand` + pulse 1.2s / 未完成 `--du-line-soft`

---

## 9. Components — Feedback ← 整章新增

### Toast（操作反馈）
- 白底卡片, radius 10px, shadow `--du-sh-lg`, padding 12px 16px
- 无左侧色条（v2.0 去除）
- 图标: 24×24 圆形语义色底 + 16×16 白色粗体内联 SVG
  - 信息: 蓝底 + 铃铛 (stroke-width 2.5)
  - 成功: 绿底 + 勾选 (stroke-width 3.5)
  - 失败: 红底 + X 叉 (stroke-width 3.5)
  - 警告: 橙底 + 感叹号 (stroke-width 2.5)
- 关闭: 14×14 X SVG, `--du-text-4`

### Alert（行内提示）
- 四种语义: info(--du-brand-bg) / success(--du-success-bg) / danger(--du-danger-bg) / warning(--du-warning-bg)
- 图标: 18×18 内联 SVG, **全部统一 18px** ← v2.0 对齐
- padding 14px 16px, radius 10px

### Confirm（确认弹窗）
- 居中卡片 max-width 360px, radius 14px, shadow `--du-sh-xl`
- 图标: 56×56 圆角方形容器(radius 14px) + 26px 内联 SVG
  - 删除: bg `--du-danger-bg`, color `--du-danger`, icon 垃圾桶
  - 发布: bg `--du-brand-bg`, color `--du-brand`, icon 火箭
- 按钮组: Secondary "取消" + Primary/Danger-Fill "确认"

### Notification（通知列表）
- 每项: padding 12px 14px, radius 10px, border `1px solid --du-line-soft`
- 未读: 蓝色圆点 8×8 `--du-brand` / 已读: 灰色圆点 `--du-line`
- Hover: bg `--du-page-bg`

---

## 10. Components — Empty States（缺省态 v2.0 · 8 类规范）

### 10.1 设计原则

1. **明确告诉用户"为什么是空"** — 是首次进入、筛选不命中、还是出错了
2. **永远给一条出路** — 除"完成态"外，每个空状态必须有明确 CTA
3. **情绪与状态匹配** — 完成态用积极色（绿）、错误用警示色（橙/红）、首次用品牌色（蓝）
4. **简短不啰嗦** — 标题 ≤ 12 字，描述 ≤ 25 字，最多 2 行
5. **零口语化** — 禁止"哎呀！"、"啊呀"、"什么都没有耶"等卖萌写法
6. **不裸露错误码** — 描述里禁止出现 `Error 500`、`ECONNREFUSED` 等技术栈细节，给用户人话

### 10.2 通用结构（五段式）

```
┌─────────────────────────────┐
│      ┌──┐                    │
│      │ ⊙│  ← 图标容器 72×72   │
│      └──┘                    │
│                              │
│      标题（fs-md / fw-600）    │
│      描述（fs-sm / text-3）    │
│      [ 行动按钮 ]              │
└─────────────────────────────┘
```

**容器规则**：居中布局；外层卡片可选（虚线 dashed border 或纯空白展示均可），上下 padding 至少 `--du-sp-12 = 48px`。

### 10.3 Empty State Token 表

```css
:root {
  --du-es-padding:     var(--du-sp-12) var(--du-sp-6);  /* 容器内边距 48 / 24 */
  --du-es-max-width:   360px;                      /* 文字内容最大宽 */
  --du-es-spacing:     var(--du-sp-3);                /* 段间垂直间距 12 */
  --du-es-icon-size:   72px;                       /* 图标容器大小 */
  --du-es-icon-radius: var(--du-radius-2xl);          /* 图标容器圆角 16 */
  --du-es-icon-svg:    32px;                       /* 内联 SVG 大小 */
  --du-es-title-fs:    var(--du-fs-md);               /* 标题字号 16 */
  --du-es-title-fw:    var(--du-fw-semibold);         /* 标题字重 600 */
  --du-es-desc-fs:     var(--du-fs-sm);               /* 描述字号 13 */
  --du-es-desc-color:  var(--du-text-3);              /* 描述色 */
  --du-es-desc-mt:     var(--du-sp-2);                /* 描述上间距 8 */
  --du-es-cta-mt:      var(--du-sp-5);                /* CTA 上间距 20 */
}
```

### 10.4 8 类配方表

| # | 类型 | 触发场景 | 容器底色 | 图标色 | 推荐图标 | CTA 类型 | 标题示例 | 描述示例 |
|---|---|---|---|---|---|---|---|---|
| 1 | **首次使用** | 用户从未创建过 | `--du-brand-bg` | `--du-brand` | plus-circle / sparkles | Primary | 还没有任何智能体 | 创建你的第一个 AI 助手，开启自动化工作流 |
| 2 | **完成态** | 全部完成 / 主动清空 | `--du-success-bg` | `--du-success` | check-circle | Ghost 或无 | 全部已完成 | 没有需要处理的任务 |
| 3 | **筛选无结果** | 筛选条件不命中 | `--du-page-bg` | `--du-text-3` | filter-x | Secondary | 当前筛选无匹配 | 试试调整筛选条件 |
| 4 | **搜索无结果** | 搜索词不命中 | `--du-page-bg` | `--du-text-4` | search-x | Secondary | 未找到"关键词" | 换个关键词试试 |
| 5 | **网络异常** | 接口报错 / 断网 | `--du-warning-bg` | `--du-warning` | wifi-off / cloud-x | Secondary | 网络异常 | 请检查网络后重试 |
| 6 | **无权限** | 未授权访问 | `--du-danger-bg` | `--du-danger` | lock | Ghost | 您没有访问权限 | 请联系管理员开通权限 |
| 7 | **404 不存在** | 资源被删 / URL 错误 | `--du-page-bg` | `--du-text-3` | file-question | Secondary | 页面不存在 | 该资源可能已被删除或移动 |
| 8 | **配额耗尽** | 限额用尽 / 付费墙 | `--du-warning-soft-bg` | `--du-warning-soft` | zap-off / crown | Primary | 本月调用已用完 | 升级套餐解锁更多额度 |

### 10.5 浅 / 深色映射

深色模式下，所有"容器底色"按 `--*-bg` token 自动切换；图标色保持品牌色 token 自动适配。无需为每个 empty 单独定义深色版本。

### 10.6 Do's and Don'ts

**Do**
- 标题用陈述句（"未找到结果"），不用问句
- 同一页面同时只展示 1 个 empty state
- 完成态可加微交互（图标进入时弹一下，参考 `--du-ease-spring`）
- 长列表筛选无结果时，把当前筛选关键词回显在描述里（"未找到 \"王\" 的结果"）

**Don't**
- 不堆文字（描述超过 2 行视为失败）
- 不用 emoji 替代图标
- 不让 CTA 同时出现 2 个以上
- 不把"加载中"骨架屏当 empty state（两套不同体系）
- 不在错误描述里暴露错误码或技术栈名（用户看不懂）

### 10.7 ASCII 落地示意

```
首次使用                    完成态                     筛选无结果
┌──────────────────┐      ┌──────────────────┐      ┌──────────────────┐
│      ╭───╮        │      │      ╭───╮        │      │      ╭───╮        │
│      │ ✦ │ ←蓝底 │      │      │ ✓ │ ←绿底 │      │      │ ▽ │ ←灰底 │
│      ╰───╯        │      │      ╰───╯        │      │      ╰───╯        │
│  还没有任何智能体  │      │   全部已完成      │      │  当前筛选无匹配   │
│  创建你的第一个… │      │  没有需要处理的… │      │  试试调整筛选条件 │
│  [ + 创建智能体 ] │      │   (无 CTA)        │      │  [ 清除筛选 ]     │
└──────────────────┘      └──────────────────┘      └──────────────────┘
```

---

## 11. Components — Navigation ← 整章新增

### Sidebar
- Width 220px, bg `#FFFFFF`, border-right `1px solid --du-line`
- Brand: 22×22 logo mark(渐变蓝圆角) + 14px 品牌名
- Section label: 10px mono uppercase `--du-text-4`, letter-spacing 0.08em
- Nav item（一级）: height 36px, padding 0 16px, 13px weight 400, border-radius `8px`（默认/hover 状态）
- Nav item Active（一级）: bg `--du-brand-bg`（**通栏底色**：抵消 sidebar 容器内边距，延伸到侧栏左右边缘）, text `--du-brand`, weight 500, **直线无圆角**（`border-radius: 0`）, **3px 品牌色竖条紧贴侧栏左边缘**（`box-shadow: inset 3px 0 0 --du-brand` 或 `border-left`，禁止内缩留白）
- Sub-nav item（二级 / 筛选项）: height 32px, padding 0 12px, 13px weight 400, color `--du-text-3`
- Sub-nav Hover（二级）: bg `--du-brand-tint`, text `--du-brand`
- Sub-nav Active（二级）: bg `--du-brand-bg`, text `--du-brand`, weight 500, **不加左侧蓝条**（避免与一级层级混淆，二级仅靠底色和字重区分选中态）
- Badge: bg `--du-danger-bg`, color `--du-danger`, mono 10px

### TopBar
- Height 64px, bg `#FFFFFF`, border-bottom `1px solid --du-line`
- Breadcrumb: 12px `--du-text-3`, current page `--du-text-2` weight 500
- Search: 30px height, radius 6px, bg `--du-page-bg`
- Avatar: 28×28 circle, 渐变品牌色底, 白字

---

## 12. Components — Table ← 整章新增

- 容器: bg `#FFFFFF`, border `1px solid --du-line-soft`, radius 12px
- Header: bg `--du-page-bg`, mono 11px uppercase weight 600 `--du-text-2`
- 排序箭头: 10px, 默认 `--du-text-4`, 激活 `--du-brand`
- Body: row 48px height, 13px body, border-bottom `--du-line-soft`
- Hover: bg `--du-brand-tint`
- Selected: bg `--du-brand-bg`, first-child `box-shadow: inset 3px 0 0 --du-brand`
- Checkbox: 16×16, accent-color `--du-brand`
- 数字列: `font-family: --du-font-mono; font-variant-numeric: tabular-nums; text-align: right`
- Pagination: 28×28 按钮, radius 6px, active bg `--du-brand` text `#FFFFFF`

---

## 13. Components — Modal & Drawer ← 整章新增

### Modal
- Backdrop: `var(--du-modal-backdrop)` = `rgba(15,27,60,0.35)`, **必须 `backdrop-filter: blur(var(--du-backdrop-blur))`（默认 8px）**, fade 200ms
- Panel: bg `#FFFFFF`, radius `var(--du-radius-xl)` (12px), max-width 480px, shadow `--du-sh-xl`
- Header: 18px title weight 600, 分割线 `--du-line-soft`
- Footer: flex justify-end, gap 10px, Secondary + Primary
- 入场: scale(0.85→1), 320ms ease-spring
- 退场: scale(1→0.96) + fade, 200ms ease-default

### Drawer
- 右侧面板 width 340px, bg `#FFFFFF`, border-left `1px solid --du-line`
- Backdrop: `var(--du-modal-backdrop)` 同 Modal, **必须配 `backdrop-filter: blur(var(--du-backdrop-blur-light))`（默认 4px，比 Modal 更轻，因为 Drawer 主页面仍可见一半）**
- 入场: translateX(100%→0), 320ms ease-out
- 退场: translateX(0→100%), 200ms ease-default

### Image Preview / 全屏 Loading
- Backdrop: `rgba(15,27,60,.55)` + `backdrop-filter: blur(var(--du-backdrop-blur-heavy))` (16px)
- 强沉浸场景，主页面被深度模糊化，焦点完全在浮层内容上

---

## 14. Components — Tooltip & Popover ← 整章新增

### Tooltip
- bg `--du-text-1`, text `#FFFFFF`, radius 6px, padding 6px 10px, font 11px weight 500
- 箭头: 6×6 旋转45°同色方块
- 四方向: top / bottom / left / right
- 入场: opacity 0→1 + translateY/X(4px→0), 120ms ease-out
- 触发: hover (纯 CSS)

### Popover（操作菜单）
- bg `#FFFFFF`, border `1px solid --du-line`, radius 10px, shadow `--du-sh-lg`, min-width 180px
- Menu item: padding 7px 10px, radius 6px, 13px, gap 8px (icon 14px + text)
- Hover: bg `--du-brand-tint`, text `--du-brand`
- Danger item hover: bg `--du-danger-bg`, text `--du-danger`
- 分割线: height 1px, bg `--du-line-soft`, margin 4px 0
- 入场: opacity 0→1, 200ms ease-out

---

## 15. Components — Avatar & Badge ← 整章新增

### Avatar 尺寸
- 24 / 32 / 40 / 48 px, radius 50%
- 默认: 渐变品牌蓝底 + 白色首字母

### 在线状态
- 10×10 圆点, border 2px solid #FFFFFF, 位于右下角
- online: `--du-success` / busy: `--du-danger` / offline: `--du-text-4`

### 头像堆叠
- margin-left: -8px, border 2px solid #FFFFFF
- 溢出计数: bg `--du-page-bg`, text `--du-text-3`, mono 11px "+N"

### Badge 角标
- 数字: min-width 16px, height 16px, bg `--du-danger`, text #FFFFFF, mono 10px weight 600, radius 8px, border 2px solid #FFFFFF
- 红点: 8×8, bg `--du-danger`, border 2px solid #FFFFFF

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
- 字体三通道: Noto Sans SC（Web 优先）/ Inter / Geist Mono
- 动效默认 **200ms ease-out**——MindLink 节奏签名
- 阴影单层微蓝: `rgba(15,27,60,...)`, 禁止多层堆叠
- 圆角四档为主: 4(tag) / 8(按钮) / 12(卡片) / 999(pill)
- 数字必须 count-up, 列表必须 stagger, 图表必须 path-draw
- 所有交互组件四态完备: hover / active / focus / disabled
- 图标统一内联 SVG, stroke currentColor, 不用字体图标 CDN
- 危险按钮实心态阴影用红色 `rgba(255,66,69,.28)`, 不用品牌蓝
- 响应 `prefers-reduced-motion`
- AI 模块必带 `--du-brand-bg → --du-brand-tint` 淡品牌渐变

### Don't
- 不要引入第二个品牌色
- 不要使用字重 700 以上（中文 700 显笨重）
- 不要让中文行高低于 1.5 或高于 1.8
- **❌ 桌面端禁止使用 9 / 10 / 11px 字号**——最低 12px（`var(--du-fs-xs)`），WCAG AA 可读性下限。Caption / 状态标签 / mono 元数据全部统一 12px。移动端 ≤ 430px 视口下仅元信息可临时用 11px
- 不要用纯黑 `#000000` 做正文——用 `#0F1B3C`
- 不要让 hover 动效超过 200ms
- **❌ 不要在任何组件上加左侧装饰色条**——按钮 / 卡片 / Toast / Alert / Notification 一律禁用左侧 2~4px 色条（含 `border-left` 实色 / `box-shadow: inset Npx 0 0 ...` / 伪元素 `::before` 模拟竖条）。状态用图标和文字色区分，不靠侧边色条。
  - **合法例外（语义性 / 结构性，非装饰）**：
    1. **Sidebar 一级菜单选中态** —— 3px 品牌色竖条贴侧栏左边缘（§11 Navigation 已明确，是项目签名设计）
    2. **Blockquote / 引用块** —— `border-left: 3px solid var(--du-brand)` + `padding-left: 12px`（HTML5 / Markdown 通用约定，国际惯例：GitHub / Notion / Discord 都这样）
    3. **Timeline / 时间轴垂直骨架** —— `border-left: 1~2px solid var(--du-line)` 用于纵向时间排列（结构线，不是状态指示）
  - 其他场景一律禁用，特别是禁止把 sidebar 的 3px 品牌色竖条复用到二级菜单 / 列表项 / 卡片选中态（这会破坏"侧栏专属"语义层级）
- **❌ 系统规范禁止使用 emoji 作为功能图标**——禁止在标题、按钮、状态、空状态、通知、问候语、欢迎语等任何 UI 位置使用 `👋 🎉 🚀 ✨ 🔥 ⭐` 等 emoji 替代图标。所有 UI 图标必须是**内联 SVG**（统一描边、可主题化、可访问性可控）。emoji 仅允许出现在用户输入内容里（聊天消息、富文本评论、用户昵称）
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

- **KPI Card**: "#FFFFFF bg, 12px radius, 24px padding, shadow 0 4px 12px rgba(15,27,60,.06). Label 12px #6B7A9C. Number 32px Geist Mono weight 600 #0F1B3C. Trend tag #EFFFEB bg #2DAC0C text. 入场 stagger slide-up 200ms spring, 数字 count-up 1200ms."

- **Sidebar**: "220px width, #FFFFFF bg, right border 1px #E5EBF5. Section label 10px mono uppercase #9BA7C3. Nav item（一级）36px, 13px, radius 8px。Active（一级）通栏直线（border-radius 0、抵消父 padding 撑满侧栏宽度）, bg #EAEFFD, text #3662EC weight 500, 3px 品牌竖条贴侧栏左边缘（inset shadow 实现）。Sub-nav（二级）32px, indent 30px, 选中态仅 bg+text 加重，不加左侧蓝条。Transition 120ms ease-default."

- **Table**: "Header: #F7F9FD bg, mono 11px uppercase #3A4868. Body: 48px row, 13px, border-bottom #EEF2FA. Hover: #F5F8FF. Selected: #EAEFFD + inset 3px #3662EC. Numeric: Geist Mono right-aligned. Pagination 28px btns."

- **Toast**: "白底卡片, radius 10px, shadow-lg. 无左侧色条。24px 圆形语义色底 + 16px 白色粗体 SVG 图标(stroke-width 3+)。信息=铃铛/成功=勾选/失败=叉/警告=感叹号。"

- **Modal**: "Backdrop rgba(15,27,60,0.35) + blur(4px). Panel #FFFFFF, 14px radius, max-width 480px, shadow-xl. 入场 scale 0.85→1, 320ms spring."

- **Circular Progress**: "SVG circle r=44, stroke-width 6, stroke-dasharray 276.46. 入场: ① 卡片 scale(0.85→1) spring stagger → ② 弧线描边 1200ms ease-out(4%过冲) → ③ 数字 count-up 同步。成功态先画满圆再弹勾选(delay 900ms)。"

### Iteration Guide
1. 交互元素 = `#3662EC`，无例外
2. 背景三层: `#F7F9FD` → `#FFFFFF` → `#F5F8FF`
3. 字体三通道: Noto Sans SC（Web 优先）/ Inter / Geist Mono
4. 动效默认 **200ms ease-out**
5. 阴影单层微蓝、圆角四档(4/8/12/999)
6. 危险操作: 红色阴影 `rgba(255,66,69,.28)`, 不用蓝色
7. 图标: 内联 SVG + currentColor, 不用 CDN 字体图标
8. Tab 切换: 滑动指示器 200ms ease-default
9. 四态完备: hover / active / focus / disabled
10. 尊重 `prefers-reduced-motion`

---

## 20. Element Plus 适配层（v2.0 新增）

### 20.1 立场

> 不重写 Element Plus 任何组件，**仅做主题映射**让 Element 100+ 组件自动跟 MindLink 视觉对齐；个别复杂多变体组件（如 Upload）补一份**使用约定**收敛研发选型。

### 20.2 接入步骤

1. **保证全局已注入 MindLink Token**（参考 §2 Tokens，约 235 个 `--du-brand / --du-text-1 / --du-sp-* / --du-radius-*` 等变量已挂在 `:root`）
2. **在入口文件按顺序引入**：
   ```js
   import 'element-plus/dist/index.css'   // ① Element 默认样式先
   import './element-theme.css'           // ② MindLink 主题层后（覆盖默认）
   ```
3. **深色模式切换**：在 `<html>` 上加 `data-theme="dark"`，Element 自动切换（兼容官方 `.dark` 写法）

### 20.3 主题变量映射（覆盖范围）

| 类别 | Element 变量 | 映射到 | 说明 |
|---|---|---|---|
| 品牌主色 | `--el-color-primary` 系（含 light-3/5/7/8/9 + dark-2） | `--du-brand` 系 | 按钮、链接、选中态、Switch、Slider |
| 功能色 | `--el-color-success / warning / danger / error / info` 全套 | `--du-success / --du-warning / --du-danger / --du-text-3` | Tag、Alert、Message、Result |
| 文本 | `--el-text-color-primary/regular/secondary/placeholder/disabled` | `--du-text-1/2/3/4/4` | 全局文字层级 |
| 背景 | `--el-bg-color / -page / -overlay` | `--du-card-bg / --du-page-bg` | 卡片/页面/浮层 |
| 边框 | `--el-border-color` 系 + `-hover` | `--du-line / --du-line-soft / --du-brand` | Input、Card、Table |
| 圆角 | `--el-border-radius-base/small/round` | `--du-radius-lg/md/pill` | 8/6/999 |
| 阴影 | `--el-box-shadow / -light / -dark` | `--du-sh-lg / --du-sh-sm / --du-sh-xl` | 微蓝阴影 |
| 字体 | `--el-font-family` + `-size-*` 6 档 | `--du-font-zh / --du-font-en` + `--du-fs-*` | 三通道协同 |
| 控件高度 | `--el-component-size-large/-/-small` | `--du-h-lg/md/sm` | 40/32/28 |
| 禁用 | `--el-disabled-text-color / -bg / -border` | `--du-text-4 / --du-page-bg / --du-line` | 一致禁用态 |
| 遮罩 | `--el-overlay-color / -mask-color` | `rgba(15,27,60,...)` | 微蓝遮罩 |
| 动效 | `--el-transition-duration / -function` | `--du-dur-* / --du-ease-*` | 节奏一致 |
| Z-index | `--el-index-popper/dialog/message/tooltip` | `--du-z-*` 层级栈 | 不撞层 |

完整映射文件：[`element-theme.css`](./element-theme.css)（172 行 / 80+ 变量）

### 20.4 局部硬覆盖说明

主题文件除变量映射外，对**少数 Element 不读 CSS 变量的硬编码场景**做了局部覆盖：

| 组件 | 覆盖原因 |
|---|---|
| `.el-button--primary` | 强制四态颜色一致（防 hover 偏离品牌色） |
| `.el-button:focus-visible` | 加 MindLink `--du-sh-focus` 焦点环 |
| `.el-input__wrapper.is-focus` | 焦点环统一 |
| `.el-card` | Level 0 Flat 默认无阴影（与 MindLink 卡片一致） |
| `.el-message / .el-notification` | **强制移除左侧色条**（执行 §18 Don't 禁令） |
| `.el-dialog / .el-drawer` | 圆角 + 阴影统一 |
| `.el-tag` | 圆角到 `--du-radius-xs`（2px）|
| `.el-scrollbar` | 滚动条统一品牌微蓝 |

---

## 20.5 Upload 使用约定（4 类形态选型）

### 20.5.1 形态选型决策树

```
要选哪种 el-upload？

  需要预览图 / 头像 / 缩略图？
    ├─ 是 → list-type="picture-card"  (网格头像/相册)
    │       OR list-type="picture"    (横向文件列表+缩略图)
    └─ 否 ─→ 文件多 + 拖拽体验？
            ├─ 是 → drag (大块拖拽区，落地页/批量场景)
            └─ 否 ─→ list-type="text"  (默认按钮+文件名列表)
```

| 形态 | 何时用 | 触发器 | 列表展示 |
|---|---|---|---|
| **text** （默认） | 单个/少量文档/附件 | 按钮 | 文件名 + 删除 |
| **picture** | 单图/几张图 + 文件名 | 按钮 | 横向卡片含缩略图 |
| **picture-card** | 头像 / 相册 / 多图网格 | 网格内 + 号 | 正方形卡片网格 |
| **drag** | 落地页主操作 / 批量 | 大块虚线框 | 文件列表 |

### 20.5.2 必备配置项

```vue
<el-upload
  v-model:file-list="fileList"
  action="/api/upload"
  :limit="5"                          <!-- ❗ 必须设上限 -->
  :on-exceed="handleExceed"
  :before-upload="beforeUpload"       <!-- ❗ 必须做前端校验 -->
  :accept="acceptTypes"               <!-- ❗ 限制 MIME 类型 -->
  :max-size="20 * 1024 * 1024"        <!-- ❗ 限制大小（运行时校验，prop 自实现）-->
  :on-success="handleSuccess"
  :on-error="handleError"
  :on-progress="handleProgress"
  drag                                <!-- 看场景启用 -->
>
  <!-- 触发器 slot -->
  <el-button type="primary">
    <i class="i-upload"></i>
    选择文件
  </el-button>
  <!-- 提示 slot -->
  <template #tip>
    <div class="upload-tip">
      支持 jpg / png / pdf · 单个 ≤ 20MB · 最多 5 个
    </div>
  </template>
</el-upload>
```

### 20.5.3 状态文案（中文化）

| 状态 | Element 默认 | MindLink 替换 |
|---|---|---|
| 上传中 | "ready / uploading" | "上传中…" |
| 成功 | "success" | "上传完成" |
| 失败 | "fail" | "上传失败，点击重试" |
| 超出数量 | 默认无提示 | Toast "最多上传 N 个文件" |
| 类型不符 | 静默拒绝 | Toast "不支持的格式：xxx" |
| 体积超限 | 静默拒绝 | Toast "单文件不能超过 20MB" |

### 20.5.4 Do / Don't

**Do**
- 在 `#tip` slot 明示**支持的格式 / 单文件大小 / 数量上限**——三件套缺一不可
- 上传按钮文案用动词："选择文件" / "上传图片"，禁用 "Upload"
- 失败状态用图标 + 文字双语义提示，可点击重试
- `picture-card` 模式下，最后一格永远是"+ 添加"占位
- 删除前必须二次确认（已上传到服务器的文件）

**Don't**
- 不省略 `:limit` 上限——前端不限制等于让用户选 1000 个文件
- 不省略 `accept` MIME 限制——对图片场景必须 `accept="image/*"`
- 不要在 `:before-upload` 里做空校验（必校验大小/格式/敏感词）
- 不要在 Upload 卡片上再嵌套一层带阴影的卡片（双层卡片视觉混乱）
- 不显示原始错误码（不写 `Error 413`，写 "文件过大"）

### 20.5.5 4 个典型场景

| 场景 | 形态 | limit | accept | 备注 |
|---|---|---|---|---|
| **附件上传**（合同/凭证）| `text` | 1–5 | `.pdf,.doc,.docx,.xls` | 列表显示文件名 |
| **头像上传** | `picture-card` | 1 | `image/*` | 启用裁剪 |
| **相册批量** | `picture-card` | 9 | `image/*` | + 占位最后一格 |
| **大文件 / 数据集** | `drag` | 3 | `.csv,.json,.zip` | 大拖拽区 + 进度条 |

### 20.6 后续扩展路径

DatePicker / Form / Table / Cascader 等高频组件按需补"使用约定"，模板沿用 §20.5 结构（决策树 → 必备配置 → 状态文案 → Do/Don't → 典型场景）。

---

**版本**：v2.0 · 2026-04-17
**适用产品**：思链智能管理系统（DOCK管理系统）
**品牌主体**：思链科技（MindLink）
**维护**：闫霞
**架构参照**：Material Design 3 · Ant Design 5 · Arco Design
