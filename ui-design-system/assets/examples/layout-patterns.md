# 布局模式示例

这些示例展示常见的布局模式，供参考而非直接使用。

---

## 经典三栏布局

```
┌─────────────────────────────────────────────────────────┐
│                       Header (固定)                      │
├──────────┬───────────────────────────────┬──────────────┤
│          │                               │              │
│ Sidebar  │      Main Content             │  Optional    │
│ (固定)   │      (可滚动)                 │  Sidebar     │
│ 240px    │                               │  (固定)      │
│          │                               │              │
│          │                               │              │
└──────────┴───────────────────────────────┴──────────────┘
```

**CSS 实现**:
```css
.layout {
    display: grid;
    grid-template-columns: 240px 1fr 280px;
    grid-template-rows: 60px 1fr;
    height: 100vh;
}

.header {
    grid-column: 1 / -1;
}

.sidebar-left {
    grid-column: 1;
    grid-row: 2;
}

.main-content {
    grid-column: 2;
    grid-row: 2;
    overflow-y: auto;
}

.sidebar-right {
    grid-column: 3;
    grid-row: 2;
}
```

**适用场景**: 管理后台、文档网站、设置页面

---

## 顶部导航布局

```
┌─────────────────────────────────────────────────────────┐
│  Logo  |  Nav Links  |         |  User | Search        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│                     Main Content                        │
│                    (居中，最大宽度)                      │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**CSS 实现**:
```css
.layout {
    min-height: 100vh;
}

.header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 60px;
    background: #ffffff;
    border-bottom: 1px solid #e5e5e7;
    display: flex;
    align-items: center;
    padding: 0 20px;
    z-index: 100;
}

.main-content {
    max-width: 1200px;
    margin: 80px auto 40px;
    padding: 0 20px;
}
```

**适用场景**: 营销网站、博客、产品首页

---

## 应用程序布局

```
┌─────────────────────────────────────────────────────────┐
│                       Header (固定)                      │
├─────────────────────────────────────────────────────────┤
│  ┌─────┐                                                │
│  │     │                                                │
│  │ App │              Main Content                      │
│  │ Nav │              (可滚动)                          │
│  │     │                                                │
│  └─────┘                                                │
└─────────────────────────────────────────────────────────┘
```

**CSS 实现**:
```css
.layout {
    display: flex;
    flex-direction: column;
    height: 100vh;
}

.header {
    flex-shrink: 0;
    height: 60px;
}

.body {
    display: flex;
    flex: 1;
    overflow: hidden;
}

.app-nav {
    width: 64px;
    flex-shrink: 0;
    background: #f5f5f7;
    border-right: 1px solid #e5e5e7;
}

.main-content {
    flex: 1;
    overflow-y: auto;
}
```

**适用场景**: Web 应用、工具类产品、聊天应用

---

## 全屏沉浸布局

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│                                                         │
│                   Full Screen Content                   │
│                   (无固定元素)                           │
│                                                         │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**CSS 实现**:
```css
.layout {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
}

.full-screen-content {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
```

**适用场景**: 图片查看器、视频播放器、全屏游戏

---

## 卡片网格布局

```
┌─────────────────────────────────────────────────────────┐
│                      Header                             │
├─────────────────────────────────────────────────────────┤
│  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐               │
│  │      │  │      │  │      │  │      │               │
│  │Card 1│  │Card 2│  │Card 3│  │Card 4│               │
│  │      │  │      │  │      │  │      │               │
│  └──────┘  └──────┘  └──────┘  └──────┘               │
│  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐               │
│  │      │  │      │  │      │  │      │               │
│  │Card 5│  │Card 6│  │Card 7│  │Card 8│               │
│  │      │  │      │  │      │  │      │               │
│  └──────┘  └──────┘  └──────┘  └──────┘               │
└─────────────────────────────────────────────────────────┘
```

**CSS 实现**:
```css
.card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    padding: 20px;
}

.card {
    background: #ffffff;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}
```

**适用场景**: 图库、商品列表、仪表盘

---

## 分屏布局

```
┌──────────────────────────────┬──────────────────────────┐
│                              │                          │
│                              │                          │
│           Left               │         Right            │
│         (50% 宽度)           │       (50% 宽度)         │
│                              │                          │
│                              │                          │
└──────────────────────────────┴──────────────────────────┘
```

**CSS 实现**:
```css
.split-layout {
    display: flex;
    height: 100vh;
}

.split-left,
.split-right {
    flex: 1;
    overflow-y: auto;
}

.split-left {
    border-right: 1px solid #e5e5e7;
}
```

**适用场景**: 代码编辑器、对比工具、文档编辑

---

## 居中单列布局

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│                   ┌──────────────┐                      │
│                   │              │                      │
│                   │   Content    │                      │
│                   │   (最大宽度)  │                      │
│                   │              │                      │
│                   └──────────────┘                      │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**CSS 实现**:
```css
.layout {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #f5f5f7;
}

.content {
    width: 100%;
    max-width: 480px;
    padding: 40px;
    background: #ffffff;
    border-radius: 16px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}
```

**适用场景**: 登录页面、注册页面、表单页面

---

## 响应式断点建议

```css
/* 移动优先 */
.container {
    width: 100%;
    padding: 0 16px;
}

/* 平板 */
@media (min-width: 768px) {
    .container {
        padding: 0 24px;
        max-width: 720px;
        margin: 0 auto;
    }
}

/* 桌面 */
@media (min-width: 1024px) {
    .container {
        max-width: 960px;
    }
}

/* 大屏 */
@media (min-width: 1280px) {
    .container {
        max-width: 1140px;
    }
}

/* 超大屏 */
@media (min-width: 1536px) {
    .container {
        max-width: 1320px;
    }
}
```

---

## 常见尺寸规范

### 间距系统
```css
--spacing-xs: 4px;
--spacing-sm: 8px;
--spacing-md: 16px;
--spacing-lg: 24px;
--spacing-xl: 32px;
--spacing-2xl: 48px;
--spacing-3xl: 64px;
```

### 组件尺寸
```css
/* 按钮 */
--btn-height-sm: 32px;
--btn-height-md: 40px;
--btn-height-lg: 48px;

/* 输入框 */
--input-height: 40px;

/* 头像 */
--avatar-xs: 24px;
--avatar-sm: 32px;
--avatar-md: 40px;
--avatar-lg: 48px;
--avatar-xl: 64px;
```

### 容器宽度
```css
--container-sm: 640px;
--container-md: 768px;
--container-lg: 1024px;
--container-xl: 1280px;
--container-2xl: 1536px;
```

---

*注意: 这些是示例布局，实际项目中应根据内容和需求调整。*
