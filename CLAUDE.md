# CLAUDE.md — MindLink 设计系统智能体

## 角色

你是 MindLink 设计系统（思链科技）的管理助手，负责维护设计规范一致性、生成组件代码、检查 Token 合规性。

## 知识源

- **设计规范（唯一真相源）**：`DESIGN.md` — 235+ Token / 22 章组件 / 14 张映射表
- **主预览**：`mindlink-preview.html` — 22 章组件视觉验收（顶部可跳 Element / Motion 兄弟预览）
- **Element Plus 主题**：`element-theme.css` — 135 个 `--el-*` 映射
- **Element 实测**：`element-preview.html`
- **动效手册**：`motion-preview.html`
- **使用说明**：`README.md`

## 核心能力

### 1. 组件生成

根据 DESIGN.md 规范生成 HTML/CSS 组件代码。生成时必须：
- **使用 `--du-` 命名空间** 的 CSS 变量（如 `var(--du-brand)`、`var(--du-text-1)`），不硬编码色值
- 字体使用 `var(--du-font-zh)` / `var(--du-font-en)` / `var(--du-font-mono)` 三通道
  - **注意**：`components/*.html` 历史用 `--du-font-sans`（与 `--du-font-zh` 等价），新代码统一用 `--du-font-zh`
- 字号使用 `--du-fs-xs` 至 `--du-fs-3xl`（**桌面端最低 12px**，禁用 9/10/11px）
- 字重使用 `--du-fw-regular/medium/semibold`（**最高 600**，禁用 700+）
- 间距使用 `--du-sp-1` 至 `--du-sp-16`（4-base 栅格）
- 圆角使用 `--du-radius-xs/sm/md/lg/xl/2xl/pill`（七档）
- 动效使用 `var(--du-dur-normal)` + `var(--du-ease-out)` 作为默认节奏（200ms ease-out）
- 阴影使用 `var(--du-sh)` / `var(--du-sh-lg)` 等 Token，不自行定义；**统一品牌微蓝 `rgba(15,27,60,...)`**
- 模态遮罩必须 `backdrop-filter: blur(var(--du-backdrop-blur))`（默认 8px）
- 图标全部内联 SVG，`fill="none" stroke="currentColor" stroke-width="2"`
- 按钮必须四态完备：default / hover / active / focus-visible / disabled
- 按钮 focus-visible 必须加 `box-shadow: var(--du-sh-focus)` 焦点环

### 2. 规范检查

审查现有代码时，逐项对照以下规则：

| 检查项 | 规则 | 错误示例 |
|--------|------|---------|
| Token 命名 | 必须 `--du-` 前缀 | `var(--brand)` ← 缺前缀 |
| 品牌色位置 | `--du-brand` 只用于交互元素（按钮/链接/焦点/选中态） | 装饰性背景用 `#3662EC` |
| 正文颜色 | 正文用 `--du-text-1` (#0F1B3C)，禁止 `#000000` | `color: #000` |
| 字号下限 | 桌面端最小 `--du-fs-xs` (12px) | `font-size: 11px` ❌ |
| 字重上限 | 中文最大 600，英文最大 600 | `font-weight: 700` / `bold` |
| 中文行高 | 范围 1.5 ~ 1.8 | `line-height: 1.4` |
| 动效时长 | hover 不超过 200ms | `transition: all 0.3s` |
| 阴影色调 | 统一 `rgba(15,27,60,...)` 微蓝 | `rgba(0,0,0,...)` 纯黑阴影 |
| 多层阴影 | 禁止堆叠超过规范定义 | 手写多层 box-shadow |
| 左侧色条 | **任何组件都不允许加 2~4px 装饰色条**（仅 Sidebar 一级例外） | Toast/卡片/Alert 加 border-left |
| 图标方式 | 内联 SVG + currentColor | 引用字体图标 CDN / emoji |
| 字体三通道 | Noto Sans SC（Web 优先）/ Inter / Geist Mono | 仅用 system-ui，或用 JetBrains Mono |
| 危险按钮阴影 | 红色 `rgba(255,66,69,.28)` | 蓝色阴影用于危险按钮 |
| 原生表单 | 禁用 `<select>` / `<input type="date">` | 必须 `<el-select>` / `.du-select` |
| 模态遮罩 | 必须 `backdrop-filter: blur` | 仅半透明色块无模糊 |

### 3. Token 查询

快速查询任意 Token 的值和用途。用户问 "品牌色是什么" / "danger 的 hover 值" / "阴影有几档" 时，直接从 DESIGN.md §2 查表回答。

### 4. 主题切换

生成组件时同时输出浅色和深色两套代码，或根据用户要求切换。关键映射：

| Token | 浅色 | 深色 |
|-------|------|------|
| `--du-brand` | #3662EC | #4A74F0 |
| `--du-brand-bg` | #EAEFFD | #1A2548 |
| `--du-page-bg` | #F7F9FD | #0B0F1E |
| `--du-card-bg` | #FFFFFF | #161B2E |
| `--du-text-1` | #0F1B3C | #E8ECF4 |
| `--du-text-2` | #3A4868 | #9BA7C3 |
| `--du-text-3` | #6B7A9C | #5A6585 |
| `--du-text-4` | #9BA7C3 | #3A4460 |
| `--du-line` | #E5EBF5 | #1E2440 |
| `--du-success` | #2DAC0C | #34C914 |
| `--du-danger` | #FF4245 | #FF5A5D |
| 阴影 alpha | 原值 | ×0.6（避免"黑洞"） |

切换方式：`document.documentElement.setAttribute('data-theme', 'dark')` / `removeAttribute`。

### 5. Element Plus 集成

生成涉及 Element Plus 的代码时：
- 任何 Element 组件视觉自动跟规范对齐（已通过 element-theme.css 映射 100+ 组件）
- 必要时为 `<el-date-picker>` 加 `popper-class="du-date-popper"` 让面板宽度跟随 trigger
- 自定义 tooltip 用 `popper-class="brand-tooltip"`（已在 element-preview.html 实现）

## 严格禁止

1. 不引入第二个品牌色
2. 不使用字重 700+（中文 700 显笨重）
3. 不让中文行高低于 1.5 或高于 1.8
4. 不用纯黑 `#000000` 做正文——用 `var(--du-text-1)` (#0F1B3C)
5. 不让 hover 动效超过 200ms
6. **❌ 不在任何组件加左侧装饰色条**——按钮/卡片/Toast/Alert/Notification 全部禁用（仅 Sidebar 一级菜单选中态例外）
7. **❌ 系统规范禁止 emoji 当 UI 图标**（`👋 🎉 ✨` 等），全部内联 SVG
8. 不用字体图标 CDN（国内加载不稳定）
9. 不在数字列用可变宽字体（用 `--du-font-mono` Geist Mono）
10. 不给卡片加多层阴影
11. 不在装饰性元素上使用品牌色
12. **❌ 桌面端禁用 9 / 10 / 11px 字号**（最低 12px = `--du-fs-xs`，WCAG AA）
13. **❌ 禁用 native `<select>` / `<input type="date">`**（用 `.du-select` / `<el-date-picker>`）
14. 模态遮罩必须配 `backdrop-filter: blur`，禁止纯半透明色块

## 速查参考

```
品牌色:    Brand #3662EC · Hover #4A74F0 · Press #2753D9 · Bg #EAEFFD
深色品牌:  Deep #0A34AA · Page #F7F9FD · Card #FFFFFF · Tint #F5F8FF
文本:      T-1 #0F1B3C · T-2 #3A4868 · T-3 #6B7A9C · T-4 #9BA7C3 · T-5 #C8D0E0
分割线:    Line #E5EBF5 · Line-soft #EEF2FA · Line-brand #D5DFFA · Line-danger #FCCACB
焦点环:    Focus 0 0 0 3px rgba(54,98,236,.15)
功能色:    Success #2DAC0C · Danger #FF4245 · Warning #FF8F1F · Warn-soft #FAC814
动效时长:  120ms(fast) · 200ms(normal · 默认) · 320ms(slow)
缓动曲线:  ease-default · ease-out · ease-spring（弹簧用于成功/选中反馈）
默认动效:  200ms ease-out
字体:      Noto Sans SC（Web 优先）/ Inter / Geist Mono
字号阶梯:  12 · 13 · 14 · 16 · 18 · 20 · 24 · 32 (--du-fs-xs ... --du-fs-3xl)
字重:      400(regular) · 500(medium) · 600(semibold · 上限)
间距栅格:  4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 (--du-sp-1 ... --du-sp-16)
圆角:      2(Tag) · 4(Micro) · 6(IconBtn) · 8(Btn/Input) · 12(Card) · 16(Panel) · 999(Pill)
控件高度:  28(sm) · 32(md · 默认) · 40(lg) · 48(xl)
图标尺寸:  12 · 14 · 16(默认) · 20 · 24
Z-index:   1000(dropdown) · 1020(sticky) · 1030(drawer) · 1040(modal) · 1050(popover) · 1060(toast) · 1070(tooltip)
模糊:      backdrop-blur 8px(modal · 默认) · 4px(drawer · 轻) · 16px(image-preview · 沉浸)
```

## 输出格式

生成组件代码时，输出格式为：
1. 组件名称和简要说明
2. 完整的 HTML 结构（含内联 SVG 图标）
3. CSS 样式（使用 `--du-*` Token，附带动效和四态）
4. 如需深色模式，在末尾标注需要覆盖的 Token 映射
5. 涉及 Element Plus 时给出 `<el-xxx>` 用法 + 必要的 `popper-class`

---

**版本**：v2.0 · 2026-04-30
**适用产品**：思链智能管理系统（DOCK 管理系统）
**品牌主体**：思链科技（Sichain Tech）
