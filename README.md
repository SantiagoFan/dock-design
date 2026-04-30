# MindLink 设计系统 v2.0 · 使用说明

> 思链科技 · DOCK 管理系统设计规范  
> 协同对象：**前端 / 后端 / 设计交互 / 产品**  
> 当前版本：v2.0（2026-04）

---

## 一、3 分钟快速上手

打开浏览器，双击 `mindlink-preview.html` —— 进入主预览页，顶部两个按钮可跳到其他预览：

| 主页面 | 用途 | 你需要时打开 |
|---|---|---|
| 📘 **mindlink-preview.html** | 设计系统主预览（22 章组件） | 找规范、查 token、看视觉 |
| 🧩 **element-preview.html** | Element Plus 真实运行时主题 | 验证 Element 组件接入效果 |
| 🎬 **motion-preview.html** | 动效手册（14 类 32 demo） | 找动效曲线、复制代码 |

---

## 二、项目文件地图

```
思链科技设计系统/                  ← 纯规范项目，无业务代码
├── 📄 规范文档（必读）
│   ├── DESIGN.md          # 唯一真相源 · 235+ Token + 22 章组件规范
│   ├── CLAUDE.md          # AI 智能体执行守则（速查 + 禁止条）
│   ├── README.md          # 本文件 · 三角色使用说明
│   └── SKILL.md           # 跨项目通用方法论（移动端 / 动效 / 6 套设计风格）
│
├── 🎨 主题接入文件（前端必用）
│   └── element-theme.css  # Element Plus 主题映射，覆盖 100+ 组件
│
└── 👁 可视化样板（设计验收 / 前端参考）
    ├── mindlink-preview.html   # 主预览（5600+ 行 · 顶部跳转 Element / Motion）
    ├── element-preview.html    # Element Plus 真实运行时主题验证
    └── motion-preview.html     # 动效手册（14 类 32 demo）
```

> **业务代码不在本仓库**：DOCK 管理系统的业务页面（dock-home / agent-* / ai-team-org 等）由独立业务前端项目维护，仅引用本仓库的 token + 主题。本仓库专注规范与样板，不被业务迭代污染。

---

## 三、按角色分工

### 🎨 设计师 / 交互（找 token + 出稿验收）

#### 1. 查 token / 颜色 / 圆角 / 阴影
- 打开 `mindlink-preview.html`，顶部锚点跳到对应章节
- 每个章节末尾都有 **Token 映射表**，复制 token 名给前端
- 例：要查"按钮主色" → 跳到 #color → 看品牌色映射表 → 拷贝 `--du-brand`

#### 2. 出新页面 / 新模块
- 打开 `DESIGN.md`，按 §2 → §20 顺序对照规则
- 不确定的边界：先看 `mindlink-preview.html` 同类组件怎么做，仿写
- 新设计如果突破规范，**先在 DESIGN.md 加章节再画稿**，避免出图后返工

#### 3. 验收前端实现
- 让前端把页面跑起来，对照 `mindlink-preview.html` 同类组件
- 检查关键 4 项：
  - 颜色是不是品牌蓝 `#3662EC`，不是 Tailwind 蓝 / Element 默认蓝
  - 阴影有没有"微蓝感"（不是黑色）
  - 字号有没有 11px / 10px（违规，最低 12px）
  - 字重有没有 700+（违规，最高 600）

---

### 💻 前端工程师（接入 + 写代码）

#### 1. 项目初次接入（5 步，10 分钟）

**Step 1**：把这两个文件拷贝到你项目：
- `mindlink-preview.html` 顶部 `:root { --du-* }` 整段（约 100 行）→ 放到全局 CSS `index.css` / `app.scss`
- `element-theme.css` → 放到项目 assets 目录

**Step 2**：在入口文件 `main.ts` 按顺序引入：
```js
import 'element-plus/dist/index.css'   // ① Element 默认样式先
import './element-theme.css'           // ② MindLink 主题层后（覆盖默认）
```

**Step 3**：深色模式切换：
```js
// 切换到深色
document.documentElement.setAttribute('data-theme', 'dark');
// 切回浅色
document.documentElement.removeAttribute('data-theme');
```

**Step 4**：写组件用 token，禁止硬编码：
```css
/* ❌ 错 */
.my-card {
  background: #FFFFFF;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,.06);
}

/* ✅ 对 */
.my-card {
  background: var(--du-card-bg);
  border-radius: var(--du-radius-xl);
  box-shadow: var(--du-sh);
}
```

**Step 5**：用 Element 组件不需特殊处理，主题层已自动接管：
```vue
<el-button type="primary">主操作</el-button>  <!-- 自动是品牌蓝 #3662EC -->
<el-input v-model="value" />                 <!-- 自动是品牌焦点环 -->
<el-tag type="success">已发布</el-tag>        <!-- 自动是品牌成功色 -->
```

#### 2. 高频 Token 速查

| 用途 | Token |
|---|---|
| 主品牌色 | `var(--du-brand)` `#3662EC` |
| 文字主色 | `var(--du-text-1)` `#0F1B3C`（**禁用纯黑**）|
| 文字次级 | `var(--du-text-2)` 卡片描述 |
| 文字三级 | `var(--du-text-3)` placeholder |
| 卡片底色 | `var(--du-card-bg)` `#FFFFFF` |
| 页面底色 | `var(--du-page-bg)` `#F7F9FD` |
| 分割线 | `var(--du-line)` |
| 字号 | `--du-fs-xs/sm/base/md/lg/xl/2xl/3xl` (12/13/14/16/18/20/24/32) |
| 字重 | `--du-fw-regular/medium/semibold` (400/500/**最高 600**) |
| 间距 | `--du-sp-1/2/3/4/5/6/8/10/12` (4/8/12/16/20/24/32/40/48) |
| 圆角 | `--du-radius-sm/md/lg/xl/2xl/pill` (4/6/8/12/16/999) |
| 阴影 | `--du-sh-sm/sh/sh-lg/sh-xl` |
| 焦点环 | `var(--du-sh-focus)` |
| 动效 | `--du-dur-fast/normal/slow` (120/200/320ms) + `--du-ease-default/out/spring` |

#### 3. 必须遵守的 4 条铁律

| ❌ 禁止 | ✅ 改用 |
|---|---|
| `font-weight: 700` / `bold` | `var(--du-fw-semibold)` (600) |
| `font-size: 11px` | `var(--du-fs-xs)` (12px) |
| `color: #000` / `#333` | `var(--du-text-1)` (#0F1B3C) |
| `box-shadow: 0 ... rgba(0,0,0,...)` | `var(--du-sh)` 系列 |
| `<select>` / `<input type="date">` 原生组件 | `<el-select>` / `<el-date-picker>` |
| 任何组件加左侧装饰色条 | 无（仅 Sidebar 一级例外）|
| `👋 🎉 ✨` emoji 当 UI 图标 | 内联 SVG |

完整规则见 `DESIGN.md` §18 Don't 共 12 条。

---

### 🛠 后端工程师（涉及范围有限）

后端通常不直接接触设计系统，但下列场景需要遵循：

#### 邮件模板 / PDF 报表
- 品牌色固定 `#3662EC`，不要用其他蓝
- 字体优先 Noto Sans SC（跨端一致），PingFang SC 兜底，fallback 到 sans-serif
- 邮件不能用 CSS 变量（兼容性差），直接用色值

#### 数据返回的状态枚举建议遵循设计语义
- 状态英文 → 推荐对应 token：
  - `success` → 显示绿色 `--du-success`
  - `pending` / `processing` → 黄色 `--du-warning`
  - `failed` / `error` → 红色 `--du-danger`
  - `idle` / `offline` → 灰色 `--du-text-3`
- 这样前端拿到状态字段后能直接套色，不用业务约定 mapping。

#### 上传 / 文件大小限制
- 配合 `DESIGN.md` §20.5 Upload 规约：
  - 单图 ≤ 5MB（image 类）
  - 文档 ≤ 20MB（pdf/doc 类）
  - 数据集 ≤ 100MB（csv/zip 类）

---

### 📋 产品 / 项目经理（提需求 + 评审）

#### 提需求时先看一遍 `mindlink-preview.html`
- 确认现有组件能不能复用
- 复用比新设计省 80% 时间
- 如果必须新建，提前与设计师沟通是否需要扩规范

#### 评审时关注质量门禁
- 新页面打开后视觉是否与 `mindlink-preview.html` 同类组件一致
- 鼠标 hover / focus / active 四态是否完备
- 浅 / 深双模式切换是否都正确
- 移动端适配是否考虑（DESIGN.md §17）

---

## 四、协同流程

### 设计 → 前端 交付流程

```
设计师                          前端
  │                               │
  │  ① 在 mindlink-preview 找原型 │
  │ ────────────────────────────> │
  │                               │ 复用同类组件
  │  ② 标注用了哪些 token         │
  │ ────────────────────────────> │ 直接 var() 引用
  │                               │
  │  ③ 边界场景 (悬停/禁用/错误)  │
  │ ────────────────────────────> │ 按 DESIGN.md 四态规则
  │                               │
  │  ④ 走查实现                   │
  │ <──────────────────────────── │ 对照 mindlink-preview
```

### 规范变更管理

- **小调整**（改 token 值、加新组件 demo）：直接改 DESIGN.md → 同步改 mindlink-preview.html
- **大变动**（新 token 系列、新组件类）：
  1. 设计师在 DESIGN.md 加新章节
  2. 在 mindlink-preview.html 加可视化 demo
  3. 让前端 review，避免实现成本爆炸
  4. 合并后通知所有协作者
- **禁忌**：业务前端项目里临时改 token 值或写死硬编码而不反馈到 DESIGN.md → 规范与实现脱节，跨项目复用时双重标准

---

## 五、FAQ

#### Q1: 我看不出设计师给的 #ABCDEF 是哪个 token，怎么办？
打开 `mindlink-preview.html`，按 `Ctrl+F` 搜色值。或者直接问设计师，让他给 token 名（不是色值）。

#### Q2: Element Plus 某个组件视觉还是默认蓝色，不是品牌蓝？
检查引入顺序，必须 Element CSS 在前、`element-theme.css` 在后。或者该组件是 Element 个别硬编码，看 `element-theme.css` 末尾"局部硬覆盖"段，按需补一条。

#### Q3: 移动端要不要单独维护一套？
不用。`--du-bp-*` 断点 token 已定义。窄屏自动适配；如果某些组件需要紧凑，用 `--du-h-sm` `--du-fs-xs` 即可。

#### Q4: 我们项目还在用 v1 老 token（没 `--du-` 前缀），怎么迁移？
查 `mindlink-preview.html` 顶部 `:root` 看 v2.0 全套 token 名，跑批量 sed 加前缀：
```bash
sed -i \
  -e 's/--brand/--du-brand/g' \
  -e 's/--text-/--du-text-/g' \
  -e 's/--fs-/--du-fs-/g' \
  -e 's/--sp-/--du-sp-/g' \
  -e 's/--radius-/--du-radius-/g' \
  -e 's/--sh/--du-sh/g' \
  src/**/*.{vue,css,scss}
```
注意：`--el-*`（Element Plus）不要加前缀，与 `--du-*` 共存。

#### Q5: 改了 token 想看效果，每次都要重新打开 preview 吗？
打开 `mindlink-preview.html`，浏览器 DevTools 的 Console 里改 `:root` 变量，例：
```js
document.documentElement.style.setProperty('--du-brand', '#FF0000');
```
即时生效，不用刷新。

#### Q6: 我们要做新业务，规范里没有的组件怎么办？
分两种情况：
- **明显是 Element 已有组件**（如 Anchor / Carousel）：直接用 `<el-xxx>` + 主题层自动适配，不需要扩规范
- **真没有**（如自研图表、专属业务卡片）：先在 mindlink-preview 仿写一个 demo，再补到 DESIGN.md，最后才去业务页落地

---

## 六、版本历史

| 版本 | 日期 | 关键改动 |
|---|---|---|
| v2.0 | 2026-04 | 14 张 Token 表 / `--du-` 命名空间 / 8 类缺省态 / Element Plus 适配层 / Inter 统一数字字体（弃 Geist Mono） / Noto Sans SC Web 优先 |
| v1.x | 2026-03 | 基础规范 + 6 张表 |

---

## 七、问题反馈

- 规范不清楚：在 DESIGN.md 对应章节加 issue 注释
- 视觉不一致：附 mindlink-preview 截图 + 业务页截图对比
- 想加新组件：先在 mindlink-preview 写 demo，再讨论是否进规范

**维护人**：闫霞 · 思链科技  
**最后更新**：2026-04-30
