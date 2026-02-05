# Component Patterns

组件设计模式 - 不是固定组件，而是设计方法论

---

## 目录

1. [设计原则](#设计原则)
2. [布局组件模式](#布局组件模式)
3. [反馈组件模式](#反馈组件模式)
4. [展示组件模式](#展示组件模式)
5. [导航组件模式](#导航组件模式)
6. [组件状态设计](#组件状态设计)
7. [组件组合模式](#组件组合模式)

---

## 设计原则

### 不是组件库，而是设计模式

**区别**:
- **组件库**: 预制的 UI 组件，直接使用
- **设计模式**: 设计组件的方法论，按需设计

**为什么不用固定模板**:
1. 每个产品的需求不同
2. 品牌调性不同
3. 用户场景不同
4. 技术限制不同

**正确做法**:
```
分析需求 → 确定功能 → 设计交互 → 编写代码 → 编写文档
```

---

## 布局组件模式

### Container / Wrapper

**目的**: 提供容器和约束

**设计考虑**:
- 最大宽度
- 居中对齐
- 响应式断点
- 内边距管理

**代码示例**:
```css
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}

@media (max-width: 768px) {
    .container {
        padding: 0 16px;
    }
}
```

### Header

**目的**: 页面顶部导航栏

**常见元素**:
- Logo / 品牌名
- 导航链接
- 用户头像
- 操作按钮

**设计考虑**:
- 固定定位 vs 普通流
- 高度 (48-64px)
- 阴影效果
- 响应式折叠

**代码示例**:
```css
.header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 56px;
    background: #ffffff;
    border-bottom: 1px solid #e5e5e7;
    display: flex;
    align-items: center;
    padding: 0 20px;
    z-index: 100;
}
```

### Sidebar

**目的**: 侧边导航栏

**设计考虑**:
- 固定宽度 (200-280px)
- 可折叠
- 当前项高亮
- 多级菜单支持

**代码示例**:
```css
.sidebar {
    position: fixed;
    left: 0;
    top: 56px;
    bottom: 0;
    width: 240px;
    background: #f5f5f7;
    border-right: 1px solid #e5e5e7;
    overflow-y: auto;
}

.sidebar-item {
    padding: 12px 16px;
    cursor: pointer;
    transition: background 0.2s;
}

.sidebar-item:hover {
    background: #e5e5e7;
}

.sidebar-item.active {
    background: #0071e3;
    color: #ffffff;
}
```

### Main Content Area

**目的**: 主要内容区域

**设计考虑**:
- 与侧边栏共存时需要 margin-left
- 与 header 共存时需要 padding-top
- 响应式断点
- 最大内容宽度

**代码示例**:
```css
.main-content {
    margin-left: 240px;
    margin-top: 56px;
    padding: 24px;
    min-height: calc(100vh - 56px);
}

@media (max-width: 768px) {
    .main-content {
        margin-left: 0;
        padding: 16px;
    }
}
```

---

## 反馈组件模式

### Button

**目的**: 触发操作

**类型**:
- 主要按钮 (Primary)
- 次要按钮 (Secondary)
- 文字按钮 (Text)
- 危险按钮 (Danger)

**状态**:
- Default（默认）
- Hover（悬停）
- Active（按下）
- Disabled（禁用）
- Loading（加载中）

**代码示例**:
```css
.btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 8px 16px;
    border-radius: 8px;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    border: none;
}

/* 主要按钮 */
.btn-primary {
    background: #0071e3;
    color: #ffffff;
}

.btn-primary:hover {
    background: #005bb5;
    transform: translateY(-1px);
}

.btn-primary:active {
    transform: translateY(0);
}

.btn-primary:disabled {
    background: #e5e5e7;
    color: #6e6e73;
    cursor: not-allowed;
}

/* 加载状态 */
.btn-loading {
    position: relative;
    color: transparent;
}

.btn-loading::after {
    content: '';
    position: absolute;
    width: 16px;
    height: 16px;
    border: 2px solid #ffffff;
    border-top-color: transparent;
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
}
```

### Input

**目的**: 输入文本

**类型**:
- 单行输入
- 多行输入 (Textarea)
- 搜索框
- 密码输入

**状态**:
- Default（默认）
- Focus（聚焦）
- Error（错误）
- Disabled（禁用）

**代码示例**:
```css
.input {
    width: 100%;
    padding: 10px 12px;
    border: 1px solid #e5e5e7;
    border-radius: 8px;
    font-size: 14px;
    transition: all 0.2s;
    background: #ffffff;
}

.input:focus {
    outline: none;
    border-color: #0071e3;
    box-shadow: 0 0 0 3px rgba(0, 113, 227, 0.1);
}

.input.error {
    border-color: #ff3b30;
}

.input.error:focus {
    box-shadow: 0 0 0 3px rgba(255, 59, 48, 0.1);
}

.input:disabled {
    background: #f5f5f7;
    color: #6e6e73;
    cursor: not-allowed;
}
```

### Checkbox / Radio

**目的**: 单选/多选

**设计考虑**:
- 尺寸 (16-20px)
- 选中状态图标
- 与文字对齐
- Indeterminate 状态

**代码示例**:
```css
.checkbox {
    position: relative;
    display: inline-flex;
    align-items: center;
    cursor: pointer;
}

.checkbox-input {
    appearance: none;
    width: 18px;
    height: 18px;
    border: 2px solid #e5e5e7;
    border-radius: 4px;
    margin-right: 8px;
    cursor: pointer;
    transition: all 0.2s;
}

.checkbox-input:checked {
    background: #0071e3;
    border-color: #0071e3;
}

.checkbox-input:checked::after {
    content: '';
    position: absolute;
    left: 5px;
    top: 2px;
    width: 5px;
    height: 9px;
    border: solid #ffffff;
    border-width: 0 2px 2px 0;
    transform: rotate(45deg);
}
```

### Modal / Dialog

**目的**: 弹窗交互

**设计考虑**:
- 遮罩层
- 居中显示
- 关闭方式 (按钮/ESC/点击外部)
- 动画效果

**代码示例**:
```css
.modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    animation: modalFadeIn 0.2s;
}

.modal {
    background: #ffffff;
    border-radius: 16px;
    padding: 24px;
    max-width: 500px;
    width: 90%;
    animation: modalScaleIn 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

@keyframes modalFadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

@keyframes modalScaleIn {
    from { opacity: 0; transform: scale(0.9); }
    to { opacity: 1; transform: scale(1); }
}
```

### Toast / Notification

**目的**: 消息提示

**类型**:
- 成功
- 错误
- 警告
- 信息

**设计考虑**:
- 显示位置 (顶/底/中)
- 自动消失
- 可手动关闭
- 堆叠处理

**代码示例**:
```css
.toast {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #ffffff;
    padding: 12px 16px;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    display: flex;
    align-items: center;
    gap: 12px;
    animation: toastSlideIn 0.3s;
    z-index: 2000;
}

.toast.success {
    border-left: 4px solid #34c759;
}

.toast.error {
    border-left: 4px solid #ff3b30;
}

@keyframes toastSlideIn {
    from { transform: translateX(400px); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
}
```

---

## 展示组件模式

### Card

**目的**: 内容卡片

**设计考虑**:
- 圆角 (8-16px)
- 阴影效果
- 内边距
- 悬停效果

**代码示例**:
```css
.card {
    background: #ffffff;
    border-radius: 12px;
    padding: 16px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    transition: all 0.2s;
}

.card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    transform: translateY(-2px);
}
```

### List

**目的**: 列表展示

**类型**:
- 无序列表
- 有序列表
- 定义列表
- 卡片列表

**代码示例**:
```css
.list {
    list-style: none;
    padding: 0;
    margin: 0;
}

.list-item {
    padding: 12px 16px;
    border-bottom: 1px solid #e5e5e7;
    display: flex;
    align-items: center;
    gap: 12px;
}

.list-item:last-child {
    border-bottom: none;
}

.list-item:hover {
    background: #f5f5f7;
}
```

### Avatar

**目的**: 用户头像

**设计考虑**:
- 尺寸 (24/32/40/48/64px)
- 圆形/圆角
- 占位符
- 在线状态

**代码示例**:
```css
.avatar {
    border-radius: 50%;
    object-fit: cover;
    background: #e5e5e7;
}

.avatar-sm { width: 24px; height: 24px; }
.avatar-md { width: 32px; height: 32px; }
.avatar-lg { width: 48px; height: 48px; }

.avatar-placeholder {
    display: flex;
    align-items: center;
    justify-content: center;
    background: #0071e3;
    color: #ffffff;
    font-weight: 500;
}
```

### Badge / Tag

**目的**: 标签/徽章

**类型**:
- 默认
- 主要
- 成功
- 警告
- 错误

**代码示例**:
```css
.badge {
    display: inline-flex;
    align-items: center;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 12px;
    font-weight: 500;
}

.badge-primary {
    background: #e0f2fe;
    color: #0071e3;
}

.badge-success {
    background: #dcfce7;
    color: #22c55e;
}

.badge-error {
    background: #fee2e2;
    color: #ef4444;
}
```

---

## 导航组件模式

### Menu

**目的**: 菜单导航

**设计考虑**:
- 当前项高亮
- 悬停效果
- 层级支持
- 响应式

**代码示例**:
```css
.menu {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.menu-item {
    padding: 10px 16px;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.2s;
}

.menu-item:hover {
    background: #e5e5e7;
}

.menu-item.active {
    background: #0071e3;
    color: #ffffff;
}
```

### Tabs

**目的**: 标签页切换

**类型**:
- 线性标签
- 胶囊标签
- 下划线标签

**代码示例**:
```css
.tabs {
    display: flex;
    gap: 8px;
    border-bottom: 1px solid #e5e5e7;
}

.tab {
    padding: 12px 16px;
    cursor: pointer;
    border-bottom: 2px solid transparent;
    transition: all 0.2s;
}

.tab:hover {
    color: #0071e3;
}

.tab.active {
    color: #0071e3;
    border-bottom-color: #0071e3;
}
```

### Breadcrumb

**目的**: 面包屑导航

**代码示例**:
```css
.breadcrumb {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 14px;
}

.breadcrumb-item:not(:last-child)::after {
    content: '/';
    color: #6e6e73;
}

.breadcrumb-link {
    color: #6e6e73;
    text-decoration: none;
}

.breadcrumb-link:hover {
    color: #0071e3;
}

.breadcrumb-item:last-child .breadcrumb-link {
    color: #1d1d1f;
}
```

---

## 组件状态设计

### 状态清单

每个交互组件都应该考虑：

1. **Default** - 默认状态
2. **Hover** - 鼠标悬停
3. **Active/Focus** - 激活/聚焦
4. **Disabled** - 禁用状态
5. **Loading** - 加载中
6. **Error** - 错误状态
7. **Success** - 成功状态

### 状态设计示例

```css
/* 按钮 - 完整状态 */
.button {
    /* Default */
    background: #0071e3;
    color: #ffffff;
}

.button:hover {
    /* Hover */
    background: #005bb5;
}

.button:active {
    /* Active */
    transform: scale(0.98);
}

.button:focus-visible {
    /* Focus */
    outline: 2px solid #0071e3;
    outline-offset: 2px;
}

.button:disabled {
    /* Disabled */
    background: #e5e5e7;
    color: #6e6e73;
    cursor: not-allowed;
}

.button.loading {
    /* Loading */
    position: relative;
    color: transparent;
}

.button.error {
    /* Error */
    background: #ff3b30;
}

.button.success {
    /* Success */
    background: #34c759;
}
```

---

## 组件组合模式

### 原子设计

```
原子 (Atoms) → 分子 (Molecules) → 组织 (Organisms) → 模板 (Templates) → 页面 (Pages)
```

**示例**:
- 原子: 按钮、输入框
- 分子: 搜索框 (输入框 + 按钮)
- 组织: 导航栏 (Logo + 菜单 + 用户)
- 模板: 页面布局
- 页面: 完整页面

### BEM 命名

```
Block (块) → Element (元素) → Modifier (修饰符)
```

**示例**:
```css
.card { }                  /* Block */
.card__title { }           /* Element */
.card__content { }         /* Element */
.card--featured { }        /* Modifier */
.card--compact { }         /* Modifier */
```

---

*最后更新: 2025-02-05*
