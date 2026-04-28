---
name: openclaw-ui-designer
description: |
  专为 AI 设计师设计的 UI 技能文件，覆盖桌面端与移动端界面设计全流程。
  触发场景：用户提到"设计页面"、"做UI"、"出原型"、"组件"、"桌面端布局"、"移动端适配"、
  "交互稿"、"设计规范"、"动效"、"风格"、"设计语言"等关键词时均应激活本技能。
  侧重可落地输出：HTML/CSS 原型、设计 Token、组件代码、动效代码、设计风格系统。
---

# OpenClaw · UI 设计师技能手册 v2.0

> 适用：桌面端（≥1280px）/ 移动端（≤430px）/ 响应式双端
> 输出：可运行 HTML 原型 · React 组件 · 设计 Token · 动效代码 · 风格系统


---

## 一、开工前：需求拆解模型

| # | 问题 | 决策影响 |
|---|------|---------|
| 1 | **谁用？** | 信息密度、字号、操作路径 |
| 2 | **在哪用？** 桌面/手机/双端 | 布局策略、触控 vs 鼠标 |
| 3 | **做什么？** 核心任务 | 主操作区权重、CTA 设计 |
| 4 | **情绪基调？** 专业/温暖/科技/活泼 | 配色、字体、圆角、动效风格 |
| 5 | **输出形式？** 看效果/可交互/要代码 | 选 HTML / React / 文档 |

---

## 二、设计 Token 系统

所有输出必须基于 CSS 变量，禁止硬编码颜色和尺寸。

```css
:root {
  /* 品牌色 */
  --color-primary:       #2563EB;
  --color-primary-light: #DBEAFE;
  --color-primary-dark:  #1D4ED8;
  --color-accent:        #F59E0B;

  /* 中性色 */
  --color-bg:          #F8FAFC;
  --color-surface:     #FFFFFF;
  --color-border:      #E2E8F0;
  --color-text:        #0F172A;
  --color-text-muted:  #64748B;

  /* 语义色 */
  --color-success: #10B981;
  --color-error:   #EF4444;
  --color-warning: #F59E0B;

  /* 排版 */
  --font-display: 'Sora', sans-serif;
  --font-body:    'DM Sans', sans-serif;
  --font-mono:    'JetBrains Mono', monospace;

  --text-xs:   0.75rem;   /* 12px */
  --text-sm:   0.875rem;  /* 14px */
  --text-base: 1rem;      /* 16px */
  --text-lg:   1.125rem;  /* 18px */
  --text-xl:   1.25rem;   /* 20px */
  --text-2xl:  1.5rem;    /* 24px */
  --text-3xl:  1.875rem;  /* 30px */
  --text-4xl:  2.25rem;   /* 36px */

  /* 间距（4pt 栅格）*/
  --space-1:  0.25rem;   /* 4px  */
  --space-2:  0.5rem;    /* 8px  */
  --space-3:  0.75rem;   /* 12px */
  --space-4:  1rem;      /* 16px */
  --space-6:  1.5rem;    /* 24px */
  --space-8:  2rem;      /* 32px */
  --space-12: 3rem;      /* 48px */
  --space-16: 4rem;      /* 64px */

  /* 圆角 */
  --radius-sm:   4px;
  --radius-md:   8px;
  --radius-lg:   12px;
  --radius-xl:   16px;
  --radius-2xl:  24px;
  --radius-full: 9999px;

  /* 阴影 */
  --shadow-sm: 0 1px 2px rgba(0,0,0,.05);
  --shadow-md: 0 4px 12px rgba(0,0,0,.08);
  --shadow-lg: 0 8px 24px rgba(0,0,0,.12);
  --shadow-xl: 0 20px 48px rgba(0,0,0,.16);

  /* 动效变量（统一管理）*/
  --ease-out:    cubic-bezier(.16, 1, .3, 1);
  --ease-spring: cubic-bezier(.34, 1.56, .64, 1);
  --ease-expo:   cubic-bezier(.19, 1, .22, 1);

  --dur-instant: 80ms;
  --dur-fast:    150ms;
  --dur-normal:  250ms;
  --dur-slow:    400ms;
  --dur-slower:  600ms;
}
```

---

## 三、桌面端布局

```
┌─────────────────────────────────────────────┐
│  Topbar (56–64px，固定)                      │
├────────────┬────────────────────────────────┤
│  Sidebar   │  Main Content Area             │
│  200–280px │  flex-1，最大宽 1200px          │
└────────────┴────────────────────────────────┘
```

```css
.layout-desktop {
  display: grid;
  grid-template-columns: 240px 1fr;
  grid-template-rows: 60px 1fr;
  min-height: 100vh;
}
.content-area {
  max-width: 1200px;
  margin: 0 auto;
  padding: var(--space-8) var(--space-6);
}
```

| 页面类型 | 布局结构 | 核心组件 |
|---------|---------|---------|
| Dashboard | 顶栏 + 侧边栏 + 卡片网格 | KPI卡、图表、数据表 |
| 列表/管理 | 顶栏 + 筛选栏 + 表格 | 搜索框、筛选标签、Table |
| 详情/编辑 | 顶栏 + 面包屑 + 表单 | 分组表单、侧边摘要 |
| 落地页 | 全宽英雄区 + 功能块 + CTA | Hero、Feature卡 |

---

## 四、移动端布局

**触控目标最小：44×44px（iOS）/ 48×48px（Android）**

```css
@media (max-width: 430px) {
  html { font-size: 16px; }
  .screen {
    padding-top: env(safe-area-inset-top);
    padding-bottom: max(env(safe-area-inset-bottom), 16px);
  }
  .bottom-nav {
    height: calc(56px + env(safe-area-inset-bottom));
    padding-bottom: env(safe-area-inset-bottom);
  }
}
```

| 元素 | 移动端 | 桌面端 |
|------|--------|--------|
| 导航 | 底部 TabBar | 左侧 Sidebar |
| 字号 | 16px 基准 | 14px 基准 |
| 间距 | 16px | 24px |
| 卡片列 | 1列 | 3–4列 |
| 按钮 | 全宽/min-h:48px | 内容宽/40px |
| 弹窗 | 底部 Sheet | 居中 Modal |

---

## 五、基础组件代码

### 5.1 按钮

```css
.btn {
  display: inline-flex; align-items: center; gap: var(--space-2);
  padding: var(--space-3) var(--space-6);
  border-radius: var(--radius-md);
  font-size: var(--text-sm); font-weight: 600;
  border: 1.5px solid transparent; cursor: pointer;
  transition: background var(--dur-fast) var(--ease-out),
              transform  var(--dur-fast) var(--ease-spring),
              box-shadow var(--dur-fast) var(--ease-out);
}
.btn-primary { background: var(--color-primary); color: #fff; }
.btn-primary:hover {
  background: var(--color-primary-dark);
  transform: translateY(-1px);
  box-shadow: var(--shadow-md);
}
.btn-primary:active { transform: scale(.97); }
```

### 5.2 KPI 数据卡

```css
.kpi-card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  box-shadow: var(--shadow-sm);
  transition: box-shadow var(--dur-normal) var(--ease-out),
              transform  var(--dur-normal) var(--ease-out);
}
.kpi-card:hover { box-shadow: var(--shadow-md); transform: translateY(-2px); }
.kpi-value { font-size: var(--text-3xl); font-weight: 700; font-family: var(--font-mono); }
.kpi-change.positive { color: var(--color-success); }
.kpi-change.negative { color: var(--color-error); }
```

### 5.3 骨架屏

```css
.skeleton {
  background: linear-gradient(90deg,
    var(--color-border) 25%, var(--color-bg) 50%, var(--color-border) 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
  border-radius: var(--radius-sm);
}
@keyframes shimmer { to { background-position: -200% 0; } }
```

### 5.4 底部弹层（Mobile Sheet）

```css
.sheet-overlay {
  position: fixed; inset: 0;
  background: rgba(0,0,0,.5);
  display: flex; align-items: flex-end;
  animation: fadeIn var(--dur-normal) var(--ease-out);
}
.sheet {
  width: 100%; max-height: 85vh;
  background: var(--color-surface);
  border-radius: var(--radius-2xl) var(--radius-2xl) 0 0;
  animation: slideUp var(--dur-slow) var(--ease-expo);
}
@keyframes fadeIn  { from { opacity: 0; } }
@keyframes slideUp { from { transform: translateY(100%); } }
```

### 5.5 Toast 通知

```javascript
function showToast(message, type = 'success') {
  const toast = document.createElement('div');
  toast.className = `toast toast-${type}`;
  toast.textContent = message;
  document.body.appendChild(toast);
  requestAnimationFrame(() => toast.classList.add('show'));
  setTimeout(() => { toast.classList.remove('show'); setTimeout(() => toast.remove(), 300); }, 2500);
}
```

```css
.toast {
  position: fixed; bottom: 80px; left: 50%;
  transform: translateX(-50%) translateY(20px);
  padding: var(--space-3) var(--space-6);
  border-radius: var(--radius-full);
  font-size: var(--text-sm); font-weight: 500;
  opacity: 0; transition: all .3s var(--ease-out);
  z-index: 9999; white-space: nowrap;
}
.toast.show    { opacity: 1; transform: translateX(-50%) translateY(0); }
.toast-success { background: var(--color-success); color: #fff; }
.toast-error   { background: var(--color-error);   color: #fff; }
```

---

## 六、基础动效系统

> **原则：** 有意义 > 好看。每个动效要回答：这在告诉用户什么？

### 6.1 动效分级

| 级别 | 时长 | 用途 | 示例 |
|------|------|------|------|
| **即时** | 80ms | 状态反馈 | 按钮按下、checkbox |
| **快速** | 150ms | 微交互 | 悬停高亮、图标变色 |
| **标准** | 250ms | 元素进出 | 下拉菜单、Tooltip |
| **缓慢** | 400ms | 页面转场 | 面板展开、路由切换 |
| **舒缓** | 600ms+ | 引导/庆祝 | 空状态、成功动效 |

### 6.2 进场动效

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes popIn {
  from { opacity: 0; transform: scale(.92); }
  to   { opacity: 1; transform: scale(1); }
}
@keyframes slideInRight {
  from { opacity: 0; transform: translateX(24px); }
  to   { opacity: 1; transform: translateX(0); }
}
@keyframes fadeDown {
  from { opacity: 0; transform: translateY(-8px); }
  to   { opacity: 1; transform: translateY(0); }
}

.animate-fade-up   { animation: fadeUp       var(--dur-slow)   var(--ease-expo)   both; }
.animate-pop-in    { animation: popIn        var(--dur-slow)   var(--ease-spring) both; }
.animate-slide-in  { animation: slideInRight var(--dur-slow)   var(--ease-expo)   both; }
.animate-fade-down { animation: fadeDown     var(--dur-normal) var(--ease-out)    both; }
```

### 6.3 列表交错进场（Stagger）

```css
.stagger-item { animation: fadeUp var(--dur-slow) var(--ease-expo) both; }
.stagger-item:nth-child(1) { animation-delay: 0ms; }
.stagger-item:nth-child(2) { animation-delay: 60ms; }
.stagger-item:nth-child(3) { animation-delay: 120ms; }
.stagger-item:nth-child(4) { animation-delay: 180ms; }
.stagger-item:nth-child(5) { animation-delay: 240ms; }
```

```javascript
// 动态数量版
document.querySelectorAll('.list-item').forEach((el, i) => {
  el.style.animation = `fadeUp 400ms cubic-bezier(.19,1,.22,1) ${i * 60}ms both`;
});
```

### 6.4 过渡动效

```css
/* 手风琴展开/收起 */
.accordion-body {
  overflow: hidden; max-height: 0; opacity: 0;
  transition: max-height var(--dur-slow) var(--ease-expo),
              opacity    var(--dur-normal) var(--ease-out);
}
.accordion-body.open { max-height: 500px; opacity: 1; }

/* 数字更新 */
@keyframes countUp {
  from { transform: translateY(8px); opacity: 0; }
  to   { transform: translateY(0);   opacity: 1; }
}
.number-update { animation: countUp var(--dur-fast) var(--ease-out); }
```

### 6.5 微交互

```css
/* 点赞弹跳 */
@keyframes heartBeat {
  0%  { transform: scale(1); }  30% { transform: scale(1.35); }
  60% { transform: scale(.9); } 100%{ transform: scale(1); }
}
.btn-like:active .icon { animation: heartBeat 400ms var(--ease-out); }

/* 涟漪效果 */
.ripple { position: relative; overflow: hidden; }
.ripple::after {
  content: ''; position: absolute;
  width: 200%; height: 200%; top: 50%; left: 50%;
  transform: translate(-50%,-50%) scale(0);
  background: rgba(255,255,255,.25); border-radius: 50%; pointer-events: none;
}
.ripple:active::after { animation: ripple 500ms var(--ease-expo); }
@keyframes ripple { to { transform: translate(-50%,-50%) scale(1); opacity: 0; } }

/* 抖动（表单错误）*/
@keyframes shake {
  0%,100%{ transform: translateX(0); }
  20%    { transform: translateX(-6px); }  40% { transform: translateX(6px); }
  60%    { transform: translateX(-4px); }  80% { transform: translateX(4px); }
}
.input-error { animation: shake 400ms var(--ease-out); }
```

### 6.6 加载动效

```css
/* 旋转圆环 */
@keyframes spin { to { transform: rotate(360deg); } }
.spinner {
  width: 20px; height: 20px;
  border: 2.5px solid var(--color-border);
  border-top-color: var(--color-primary);
  border-radius: 50%;
  animation: spin 600ms linear infinite;
}

/* 三点跳动 */
@keyframes bounce {
  0%,80%,100% { transform: translateY(0); }  40% { transform: translateY(-8px); }
}
.dot-1 { animation: bounce 1.2s infinite 0ms; }
.dot-2 { animation: bounce 1.2s infinite 200ms; }
.dot-3 { animation: bounce 1.2s infinite 400ms; }

/* 不定长进度条 */
.progress-bar { position: relative; overflow: hidden; height: 3px; background: var(--color-border); }
.progress-bar::after {
  content: ''; position: absolute; top: 0; bottom: 0;
  background: var(--color-primary);
  animation: progress-indeterminate 2s cubic-bezier(.65,.815,.735,.395) infinite;
}
@keyframes progress-indeterminate {
  0%   { left: -35%; right: 100%; }
  60%  { left: 100%; right: -90%; }
  100% { left: 100%; right: -90%; }
}
```

---

## 七、前沿动效技术

> 按需选择，不要全部堆叠。

### 7.1 View Transitions API（页面级丝滑切换）

**兼容：** Chrome 111+ | **场景：** SPA 路由、列表→详情

```javascript
async function navigateTo(newContent) {
  if (!document.startViewTransition) {
    document.querySelector('#app').innerHTML = newContent;
    return;
  }
  document.startViewTransition(() => {
    document.querySelector('#app').innerHTML = newContent;
  });
}
```

```css
::view-transition-old(root) { animation: 300ms ease-out both slide-out-left; }
::view-transition-new(root) { animation: 300ms ease-out both slide-in-right; }
@keyframes slide-out-left { to   { transform: translateX(-30%); opacity: 0; } }
@keyframes slide-in-right { from { transform: translateX(30%);  opacity: 0; } }

/* 共享元素补间（卡片→详情自动动效）*/
.card-thumbnail { view-transition-name: hero-image; }
.detail-hero    { view-transition-name: hero-image; }
```

### 7.2 Scroll-driven Animations（滚动驱动）

**兼容：** Chrome 115+ | **场景：** 落地页、内容营销页

```css
/* 阅读进度条 */
.reading-progress {
  position: fixed; top: 0; left: 0; right: 0; height: 3px;
  background: var(--color-primary);
  transform-origin: left; transform: scaleX(0);
  animation: scaleProgress linear both;
  animation-timeline: scroll(root block);
}
@keyframes scaleProgress { to { transform: scaleX(1); } }

/* 滚动进入视口淡入 */
.scroll-reveal {
  animation: fadeUp linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 30%;
}

/* 视差 */
.parallax-title {
  animation: parallaxMove linear both;
  animation-timeline: scroll(root block);
}
@keyframes parallaxMove {
  from { transform: translateY(-30px); }
  to   { transform: translateY(30px); }
}
```

### 7.3 CSS @property（可动画自定义属性）

**兼容：** Chrome 85+ | **场景：** 渐变动画、数字计数器

```css
@property --gradient-angle { syntax: '<angle>'; initial-value: 0deg; inherits: false; }
.gradient-card {
  background: conic-gradient(from var(--gradient-angle), #2563EB, #8B5CF6, #2563EB);
  transition: --gradient-angle 600ms var(--ease-expo);
}
.gradient-card:hover { --gradient-angle: 180deg; }

/* 纯 CSS 数字计数 */
@property --num { syntax: '<integer>'; initial-value: 0; inherits: false; }
.counter { --num: 0; counter-reset: count var(--num); transition: --num 1200ms var(--ease-expo); }
.counter::after { content: counter(count); }
.counter.in-view { --num: 12400; }
```

### 7.4 流光边框 + 鼠标光晕

**场景：** SaaS 卡片、Hero 区、AI 产品

```css
/* 流光旋转边框 */
@property --border-angle { syntax: '<angle>'; initial-value: 0deg; inherits: false; }
@keyframes borderSpin { to { --border-angle: 360deg; } }

.glow-card {
  padding: 1px; border-radius: var(--radius-lg);
  background-image: conic-gradient(
    from var(--border-angle),
    transparent 70%, var(--color-primary) 80%, #8B5CF6 90%, var(--color-primary) 100%
  );
  animation: borderSpin 3s linear infinite;
}
.glow-card-inner {
  background: var(--color-surface);
  border-radius: calc(var(--radius-lg) - 1px);
  padding: var(--space-6);
}

/* 鼠标跟随光晕 */
.card-spotlight { position: relative; overflow: hidden; }
.card-spotlight::before {
  content: ''; position: absolute;
  width: 300px; height: 300px; border-radius: 50%;
  background: radial-gradient(circle, rgba(37,99,235,.15) 0%, transparent 60%);
  left: var(--mouse-x, 50%); top: var(--mouse-y, 50%);
  transform: translate(-50%, -50%);
  pointer-events: none; opacity: 0; transition: opacity var(--dur-normal);
}
.card-spotlight:hover::before { opacity: 1; }
```

```javascript
document.querySelectorAll('.card-spotlight').forEach(card => {
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    card.style.setProperty('--mouse-x', `${e.clientX - rect.left}px`);
    card.style.setProperty('--mouse-y', `${e.clientY - rect.top}px`);
  });
});
```

### 7.5 磁性吸附按钮（Magnetic Button）

**场景：** 落地页主 CTA、品牌官网

```javascript
document.querySelectorAll('.btn-magnetic').forEach(btn => {
  btn.addEventListener('mousemove', e => {
    const rect = btn.getBoundingClientRect();
    const cx = rect.left + rect.width / 2;
    const cy = rect.top + rect.height / 2;
    btn.style.transform = `translate(${(e.clientX - cx) * .25}px, ${(e.clientY - cy) * .25}px)`;
    btn.style.transition = 'transform 100ms';
  });
  btn.addEventListener('mouseleave', () => {
    btn.style.transform = '';
    btn.style.transition = 'transform 500ms cubic-bezier(.34,1.56,.64,1)';
  });
});
```

### 7.6 文字动效

```css
/* 渐变文字 */
.gradient-text {
  background: linear-gradient(135deg, var(--color-primary), #8B5CF6, #EC4899);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}

/* 打字机 */
.typewriter {
  overflow: hidden; white-space: nowrap;
  border-right: 2px solid var(--color-primary); width: 0;
  animation: typing 2s steps(20) forwards, blink .7s step-end infinite;
}
@keyframes typing { to { width: 100%; } }
@keyframes blink  { 50% { border-color: transparent; } }

/* 逐字浮入 */
@keyframes charReveal {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
.char-reveal span { display: inline-block; animation: charReveal 500ms var(--ease-expo) both; }
```

```javascript
document.querySelectorAll('.char-reveal').forEach(el => {
  el.innerHTML = [...el.textContent].map((c, i) =>
    `<span style="animation-delay:${i * 30}ms">${c === ' ' ? '&nbsp;' : c}</span>`
  ).join('');
});
```

### 7.7 3D 翻转卡片

**场景：** 产品展示、成员介绍

```css
.card-3d { perspective: 1000px; }
.card-3d-inner {
  position: relative; width: 100%; height: 100%;
  transform-style: preserve-3d;
  transition: transform 600ms var(--ease-expo);
}
.card-3d:hover .card-3d-inner { transform: rotateY(180deg); }
.card-face { position: absolute; inset: 0; backface-visibility: hidden; border-radius: var(--radius-lg); }
.card-back { transform: rotateY(180deg); }
```

### 7.8 GSAP 集成

**场景：** 落地页、品牌官网、复杂时间轴编排

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
```

```javascript
gsap.registerPlugin(ScrollTrigger);

// 滚动触发批量进场
gsap.from('.feature-card', {
  scrollTrigger: { trigger: '.features', start: 'top 80%' },
  y: 40, opacity: 0, duration: 0.6, stagger: 0.1, ease: 'expo.out'
});

// 数字计数动画
gsap.to('.counter-num', {
  innerText: 12400, duration: 1.5, ease: 'power2.out',
  snap: { innerText: 1 },
  scrollTrigger: { trigger: '.stats', start: 'top 70%' }
});
```

### 7.9 性能规则

```css
/* 只对以下属性做动画（GPU 合成，不重排）*/
/* ✅ transform · opacity · filter */
/* ❌ 避免：width/height/top/left/margin/background-color */

.animated { will-change: transform, opacity; }

/* 尊重用户无动效偏好 */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
    transition-duration: .01ms !important;
  }
}
```

---

## 八、设计风格系统

> 每个项目选择**一种主风格**，不要混搭。

### 8.1 Glassmorphism（玻璃拟态）

**适用：** AI工具、科技产品、音乐App、游戏UI
**关键词：** 未来感 · 神秘 · 沉浸

```css
/* 必须有深色/渐变背景打底 */
.glass-bg {
  background:
    radial-gradient(ellipse at 20% 50%, rgba(37,99,235,.4) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 20%, rgba(139,92,246,.3) 0%, transparent 50%),
    radial-gradient(ellipse at 50% 80%, rgba(236,72,153,.2) 0%, transparent 50%),
    #050818;
  min-height: 100vh;
}

.glass-card {
  background: rgba(255,255,255,.08);
  backdrop-filter: blur(20px) saturate(180%);
  -webkit-backdrop-filter: blur(20px) saturate(180%);
  border: 1px solid rgba(255,255,255,.15);
  border-radius: var(--radius-xl);
  box-shadow: 0 8px 32px rgba(0,0,0,.3), inset 0 1px 0 rgba(255,255,255,.2);
}
.glass-nav {
  background: rgba(5,8,24,.6);
  backdrop-filter: blur(24px);
  border-bottom: 1px solid rgba(255,255,255,.08);
}
.glass-btn {
  background: rgba(255,255,255,.1);
  border: 1px solid rgba(255,255,255,.2);
  color: #fff; backdrop-filter: blur(8px);
  transition: background var(--dur-normal), border-color var(--dur-normal);
}
.glass-btn:hover { background: rgba(255,255,255,.18); border-color: rgba(255,255,255,.35); }
```

| 角色 | 值 |
|------|-----|
| 背景底 | `#050818` |
| 光晕色 | `#2563EB` / `#8B5CF6` |
| 玻璃描边 | `rgba(255,255,255,.12)` |
| 主文字 | `rgba(255,255,255,.9)` |
| 次文字 | `rgba(255,255,255,.5)` |

---

### 8.2 Neumorphism（新拟物）

**适用：** 健康医疗、智能家居、音频播放器
**关键词：** 触感 · 精致 · 克制

```css
:root {
  --neo-bg:           #E0E5EC;
  --neo-shadow-light: rgba(255,255,255,.8);
  --neo-shadow-dark:  rgba(163,177,198,.6);
}
.neo-raised {
  background: var(--neo-bg); border-radius: var(--radius-xl);
  box-shadow:  8px 8px 16px var(--neo-shadow-dark), -8px -8px 16px var(--neo-shadow-light);
}
.neo-inset {
  background: var(--neo-bg); border-radius: var(--radius-xl);
  box-shadow: inset 6px 6px 12px var(--neo-shadow-dark), inset -6px -6px 12px var(--neo-shadow-light);
}
.neo-circle {
  width: 80px; height: 80px; border-radius: 50%;
  background: var(--neo-bg);
  box-shadow: 6px 6px 12px var(--neo-shadow-dark), -6px -6px 12px var(--neo-shadow-light);
  display: flex; align-items: center; justify-content: center; cursor: pointer;
  transition: box-shadow var(--dur-normal);
}
.neo-circle:active {
  box-shadow: inset 4px 4px 8px var(--neo-shadow-dark), inset -4px -4px 8px var(--neo-shadow-light);
}
```

---

### 8.3 Brutalism（野蛮主义）

**适用：** 创意机构、Z世代品牌、艺术项目
**关键词：** 叛逆 · 力量 · 反精致

```css
:root {
  --brutal-black:  #0A0A0A;
  --brutal-yellow: #FFE500;
  --brutal-red:    #FF2B2B;
  --brutal-border: 2.5px solid #0A0A0A;
  --brutal-shadow: 4px 4px 0 #0A0A0A;
}
.brutal-card {
  background: #FAFAFA;
  border: var(--brutal-border); box-shadow: var(--brutal-shadow);
  border-radius: 0; padding: var(--space-6);
  transition: transform var(--dur-fast), box-shadow var(--dur-fast);
}
.brutal-card:hover { transform: translate(-2px,-2px); box-shadow: 6px 6px 0 #0A0A0A; }

.brutal-btn {
  background: var(--brutal-yellow); color: #0A0A0A;
  border: var(--brutal-border); box-shadow: var(--brutal-shadow);
  font-weight: 900; font-family: 'Space Mono', monospace;
  text-transform: uppercase; letter-spacing: .05em; border-radius: 0; cursor: pointer;
  transition: transform var(--dur-instant), box-shadow var(--dur-instant);
}
.brutal-btn:hover  { transform: translate(-2px,-2px); box-shadow: 6px 6px 0 #0A0A0A; }
.brutal-btn:active { transform: translate(2px,2px);   box-shadow: 2px 2px 0 #0A0A0A; }

.brutal-tag {
  background: var(--brutal-red); color: #fff;
  font-size: var(--text-xs); font-weight: 700; padding: 2px 10px;
  clip-path: polygon(8px 0, 100% 0, calc(100% - 8px) 100%, 0 100%);
}
```

---

### 8.4 Claymorphism（黏土风）

**适用：** 少儿教育、休闲游戏、消费品牌
**关键词：** 可爱 · 活泼 · 膨胀感

```css
/* 核心：多层彩色阴影制造厚度错觉 */
.clay-card {
  background: #7C9EFF; border-radius: 20px;
  box-shadow:
    0 1px 0 2px rgba(255,255,255,.4),
    0 6px 0 0 #4B6FCC,
    0 8px 16px rgba(75,111,204,.4);
  transition: transform var(--dur-normal) var(--ease-spring), box-shadow var(--dur-normal);
}
.clay-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 1px 0 2px rgba(255,255,255,.4), 0 10px 0 0 #4B6FCC, 0 14px 24px rgba(75,111,204,.5);
}
.clay-btn {
  background: #FF7043; border-radius: var(--radius-full);
  box-shadow: 0 1px 0 2px rgba(255,255,255,.4), 0 5px 0 0 #C4370A, 0 6px 12px rgba(196,55,10,.4);
  color: #fff; font-weight: 800; border: none; cursor: pointer;
  transition: transform var(--dur-instant) var(--ease-spring), box-shadow var(--dur-instant);
}
.clay-btn:active {
  transform: translateY(4px);
  box-shadow: 0 1px 0 2px rgba(255,255,255,.4), 0 1px 0 0 #C4370A, 0 2px 4px rgba(196,55,10,.3);
}
```

| 色系 | 背景 | 厚度色 |
|------|------|--------|
| 蓝 | `#7C9EFF` | `#4B6FCC` |
| 绿 | `#7DC88B` | `#4A9659` |
| 橙 | `#FF9F6B` | `#D46B3C` |
| 紫 | `#B88EFF` | `#7B5AC4` |
| 粉 | `#FF8EB4` | `#C45A80` |

---

### 8.5 Minimal Luxury（极简奢华）

**适用：** 高端品牌、时尚电商、精品酒店
**关键词：** 留白 · 克制 · 品味

```css
:root {
  --lux-black: #0C0C0C;
  --lux-white: #F9F6F1;   /* 暖白 */
  --lux-gold:  #C9A96E;
  --font-serif: 'Playfair Display', 'Noto Serif SC', serif;
}
.lux-heading {
  font-family: var(--font-serif);
  font-size: var(--text-4xl); letter-spacing: -.02em; line-height: 1.15;
}
.lux-card {
  background: var(--lux-white);
  border: 1px solid rgba(12,12,12,.1);
  padding: var(--space-12); position: relative;
}
/* 金色角标 */
.lux-card::before {
  content: ''; position: absolute; top: 16px; left: 16px;
  width: 20px; height: 20px;
  border-top: 1px solid var(--lux-gold);
  border-left: 1px solid var(--lux-gold);
}
/* 填充式悬停按钮 */
.lux-btn {
  background: transparent; border: 1px solid var(--lux-black); color: var(--lux-black);
  font-size: var(--text-xs); letter-spacing: .15em; text-transform: uppercase;
  padding: var(--space-4) var(--space-8);
  position: relative; overflow: hidden; cursor: pointer;
}
.lux-btn::after {
  content: ''; position: absolute; inset: 0;
  background: var(--lux-black); transform: translateY(101%);
  transition: transform 400ms var(--ease-expo);
}
.lux-btn:hover::after { transform: translateY(0); }
.lux-btn span { position: relative; z-index: 1; transition: color 400ms; }
.lux-btn:hover span { color: var(--lux-white); }

/* 金线分割 */
.lux-divider {
  display: flex; align-items: center; gap: var(--space-4);
  color: var(--lux-gold); font-size: var(--text-xs); letter-spacing: .2em;
}
.lux-divider::before,
.lux-divider::after { content: ''; flex: 1; height: 1px; background: var(--lux-gold); opacity: .4; }
```

---

### 8.6 Dark Tech（暗黑科技）

**适用：** 开发者工具、AI产品、数据平台、游戏、区块链
**关键词：** 极客 · 专业 · 霓虹 · 力量

```css
:root {
  --tech-bg:      #090E1A;
  --tech-surface: #0F1829;
  --tech-border:  rgba(37,99,235,.2);
  --tech-glow:    #00D9FF;
  --tech-green:   #00FF94;
  --tech-purple:  #A855F7;
}
/* 网格背景 */
.tech-grid-bg {
  background-color: var(--tech-bg);
  background-image:
    linear-gradient(rgba(37,99,235,.08) 1px, transparent 1px),
    linear-gradient(90deg, rgba(37,99,235,.08) 1px, transparent 1px);
  background-size: 40px 40px;
}
/* 扫描线叠层 */
.tech-scanlines::after {
  content: ''; position: fixed; inset: 0;
  background: repeating-linear-gradient(
    0deg, transparent, transparent 2px, rgba(0,217,255,.015) 2px, rgba(0,217,255,.015) 4px
  );
  pointer-events: none; z-index: 9999;
}
/* 霓虹卡片 */
.tech-card {
  background: var(--tech-surface);
  border: 1px solid var(--tech-border);
  border-radius: var(--radius-md);
  transition: border-color var(--dur-normal), box-shadow var(--dur-normal);
}
.tech-card:hover {
  border-color: rgba(0,217,255,.4);
  box-shadow: 0 0 20px rgba(0,217,255,.15), 0 4px 24px rgba(0,0,0,.6);
}
/* 霓虹文字 */
.neon-blue  { color: var(--tech-glow);  text-shadow: 0 0 8px var(--tech-glow),  0 0 20px rgba(0,217,255,.4); }
.neon-green { color: var(--tech-green); text-shadow: 0 0 8px var(--tech-green), 0 0 20px rgba(0,255,148,.4); }
/* 终端输入框 */
.terminal-input {
  background: rgba(0,0,0,.4); border: 1px solid var(--tech-border);
  color: var(--tech-green); font-family: var(--font-mono);
  padding: var(--space-3) var(--space-4); border-radius: var(--radius-sm);
  caret-color: var(--tech-green);
}
.terminal-input:focus { border-color: var(--tech-green); box-shadow: 0 0 12px rgba(0,255,148,.2); outline: none; }
/* 数据徽章 */
.tech-badge { font-family: var(--font-mono); font-size: var(--text-xs); padding: 2px 10px; border: 1px solid currentColor; border-radius: 2px; }
.badge-blue   { color: var(--tech-glow);   background: rgba(0,217,255,.08); }
.badge-green  { color: var(--tech-green);  background: rgba(0,255,148,.08); }
.badge-purple { color: var(--tech-purple); background: rgba(168,85,247,.08); }
```

---

### 8.7 风格速查对比表

| 风格 | 情绪 | 圆角 | 配色 | 字体 | 禁忌 |
|------|------|------|------|------|------|
| **Glassmorphism** | 科技·未来·神秘 | 大（16px+）| 深底+蓝紫渐变 | 无衬线细体 | 浅色背景 |
| **Neumorphism** | 温柔·精致·触感 | 中大（12-20px）| 单一中性色 | 细无衬线 | 高对比配色 |
| **Brutalism** | 叛逆·力量·个性 | 0（无圆角）| 高饱和撞色 | 粗体等宽 | 精致圆润感 |
| **Claymorphism** | 可爱·活泼·童趣 | 超大（20px+）| 高饱和亮色 | 圆体粗体 | 深底/细线条 |
| **Minimal Luxury** | 高端·克制·品味 | 极小或无 | 黑白金 | 衬线体 | 鲜色/拥挤排版 |
| **Dark Tech** | 极客·专业·力量 | 小（4-8px）| 深底+霓虹高亮 | 等宽/无衬线 | 浅色背景 |

---

## 九、响应式 + 深色模式

```css
/* 断点 */
@media (min-width: 768px)  { /* 平板及以上 */ }
@media (min-width: 1024px) { /* 桌面 */ }

/* 表格移动端卡片化 */
@media (max-width: 767px) {
  table, thead, tbody, tr, th, td { display: block; }
  thead { display: none; }
  tr { background: var(--color-surface); border: 1px solid var(--color-border); border-radius: var(--radius-md); margin-bottom: var(--space-3); padding: var(--space-4); }
  td::before { content: attr(data-label); font-weight: 600; color: var(--color-text-muted); font-size: var(--text-xs); display: block; margin-bottom: 4px; }
}

/* 深色模式 */
@media (prefers-color-scheme: dark) {
  :root {
    --color-bg:         #0F172A;
    --color-surface:    #1E293B;
    --color-border:     #334155;
    --color-text:       #F1F5F9;
    --color-text-muted: #94A3B8;
  }
}
```

---

## 十、无障碍清单

- [ ] 正文对比度 ≥ 4.5:1，大字/图标 ≥ 3:1
- [ ] 所有交互元素有 `focus-visible` 轮廓
- [ ] 用语义标签：`<nav>` `<main>` `<button>`
- [ ] 图片有 `alt`，装饰图用 `alt=""`
- [ ] 表单有关联 `<label>` 或 `aria-label`
- [ ] 动效加 `prefers-reduced-motion` 降级

```css
:focus-visible { outline: 2px solid var(--color-primary); outline-offset: 2px; border-radius: 2px; }
```

---

## 十一、需求 → 执行路径

| 用户说 | 你做的第一步 |
|--------|------------|
| "做个登录页" | 选风格 → 套 Token → 邮件/密码/提交 HTML |
| "做个 Dashboard" | 确认指标数 → 顶栏+侧栏+KPI卡+图表 |
| "移动端适配" | 断点+卡片化+TabBar+安全区 |
| "科技感/AI感" | Dark Tech + 霓虹 + 扫描线 + 流光边框 |
| "高端感" | Minimal Luxury + 衬线字 + 黑白金 + 覆盖动效 |
| "可爱活泼" | Claymorphism + 高饱和 + spring 弹性动效 |
| "未来感" | Glassmorphism + 深底光晕 + 磁性按钮 |
| "加滚动动效" | Scroll-driven API 或 GSAP ScrollTrigger |
| "页面切换丝滑" | View Transitions API + 共享元素 |
| "加深色模式" | Token 覆盖 + `prefers-color-scheme` |
| "设计规范文档" | Markdown：颜色/字体/间距/组件状态/动效规格 |

---

*OpenClaw UI 设计技能手册 v2.0*
*模块：基础布局 · 组件系统 · 基础动效 · 前沿动效 · 六种设计风格*
