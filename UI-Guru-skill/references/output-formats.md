# Output Formats

输出格式规范 - 设计交付物的标准格式

---

## 目录

1. [交付物清单](#交付物清单)
2. [interactive.html 规范](#interactivehtml-规范)
3. [design-guide.html 规范](#design-guidehtml-规范)
4. [设计文档规范](#设计文档规范)
5. [文件组织结构](#文件组织结构)

---

## 交付物清单

### 核心交付物

| 文件 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `interactive.html` | HTML | ✅ | 可交互原型 |
| `design-guide.html` | HTML | ✅ | 设计规范页面 |
| `design-spec.md` | Markdown | ✅ | 主设计规范 |
| `tokens.md` | Markdown | ✅ | 设计令牌 |
| `components.md` | Markdown | ✅ | 组件文档 |
| `interactions.md` | Markdown | ✅ | 交互规范 |
| `dev-guide.md` | Markdown | ✅ | 开发指南 |
| `README.md` | Markdown | ✅ | 使用说明 |
| `progress.md` | Markdown | ✅ | 版本历史 |

### 可选交付物

| 文件 | 类型 | 说明 |
|------|------|------|
| `design-system.json` | JSON | 设计令牌 JSON 格式 |
| `components/` | 目录 | 组件代码片段 |
| `assets/` | 目录 | 设计资源文件 |

---

## interactive.html 规范

### 目的

创建完整的可交互原型，展示所有用户流程和交互状态。

### 文件结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>交互式原型 - [产品名称]</title>
    <style>
        /* 1. CSS 变量 (设计令牌) */
        :root {
            /* 颜色系统 */
            --color-primary: #0071e3;
            --color-background: #f5f5f7;
            /* ... */
        }

        /* 2. 全局样式 */
        * { box-sizing: border-box; }
        body {
            margin: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        }

        /* 3. 布局样式 */
        .app-container { /* ... */ }
        .header { /* ... */ }
        .chat-area { /* ... */ }

        /* 4. 组件样式 */
        .message { /* ... */ }
        .button { /* ... */ }

        /* 5. 动画定义 */
        @keyframes fadeIn { /* ... */ }
    </style>
</head>
<body>
    <!-- 页面结构 -->
    <div class="app-container">
        <header class="header"><!-- ... --></header>
        <main class="chat-area"><!-- ... --></main>
        <footer class="input-area"><!-- ... --></footer>
    </div>

    <!-- 交互脚本 -->
    <script>
        // 场景管理
        // 消息系统
        // 输入处理
        // 弹窗系统
        // 动画控制
    </script>
</body>
</html>
```

### 必需功能

1. **场景演示**
   - 至少 3-5 个典型场景
   - 场景切换按钮
   - 自动播放选项

2. **交互状态**
   - 所有交互状态可见
   - 加载状态演示
   - 错误状态演示

3. **响应式**
   - 适配桌面 (1200px+)
   - 适配平板 (768px-1199px)
   - 适配移动 (<768px)

### 场景示例

```javascript
// 场景管理器
const scenarios = [
    {
        name: '基础生成',
        steps: [
            { type: 'user', content: '生成一张风景画', delay: 0 },
            { type: 'typing', delay: 500 },
            { type: 'image', url: '...', delay: 2000 }
        ]
    },
    {
        name: '多轮对话',
        steps: [
            { type: 'user', content: '生成一张图片', delay: 0 },
            { type: 'typing', delay: 500 },
            { type: 'image', url: '...', delay: 2000 },
            { type: 'user', content: '换个风格', delay: 3000 },
            { type: 'typing', delay: 3500 },
            { type: 'image', url: '...', delay: 5000 }
        ]
    }
];
```

---

## design-guide.html 规范

### 目的

创建可视化的设计规范页面，让设计师和开发可以 1:1 还原设计。

### 布局结构

```
┌─────────────────────────────────────────────────────────┐
│  Sidebar              │  Preview Area  │  Specs Panel   │
│  (组件导航)           │  (实时预览)    │  (规范+代码)    │
│                       │                │                │
│  ┌─────────────────┐ │  ┌───────────┐ │  ┌───────────┐ │
│  │ • 布局组件      │ │  │           │ │  │ 尺寸: ... │ │
│  │ • 消息组件      │ │  │  组件预览  │ │  │ 颜色: ... │ │
│  │ • 加载状态      │ │  │           │ │  │ 代码:     │ │
│  │ • 图片组件      │ │  │           │ │  │ ```css    │ │
│  │ • 弹窗组件      │ │  └───────────┘ │  │ .class {} │ │
│  └─────────────────┘ │                │  │ ```      │ │
│                       │                │  └───────────┘ │
└─────────────────────────────────────────────────────────┘
```

### 文件结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>设计规范 - [产品名称]</title>
    <style>
        /* 布局样式 */
        .design-guide {
            display: grid;
            grid-template-columns: 240px 1fr 320px;
            height: 100vh;
        }

        .sidebar {
            background: #f5f5f7;
            border-right: 1px solid #e5e5e7;
            padding: 20px;
        }

        .preview-area {
            padding: 40px;
            overflow-y: auto;
        }

        .specs-panel {
            background: #f5f5f7;
            border-left: 1px solid #e5e5e7;
            padding: 20px;
            overflow-y: auto;
        }

        /* 组件展示 */
        .component-showcase {
            position: relative;
            padding: 40px;
            background: #ffffff;
            border-radius: 12px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
        }

        /* 尺寸标注 */
        .dimension-overlay {
            position: absolute;
            background: rgba(0, 113, 227, 0.9);
            color: #ffffff;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            pointer-events: none;
        }

        /* 代码块 */
        .code-block {
            background: #1d1d1f;
            color: #f5f5f7;
            padding: 16px;
            border-radius: 8px;
            font-family: 'SF Mono', Monaco, monospace;
            font-size: 13px;
            overflow-x: auto;
            position: relative;
        }

        .copy-button {
            position: absolute;
            top: 8px;
            right: 8px;
            padding: 4px 12px;
            background: rgba(255, 255, 255, 0.1);
            border: none;
            border-radius: 4px;
            color: #ffffff;
            cursor: pointer;
            font-size: 12px;
        }

        .copy-button:hover {
            background: rgba(255, 255, 255, 0.2);
        }
    </style>
</head>
<body>
    <div class="design-guide">
        <!-- 左侧导航 -->
        <nav class="sidebar">
            <h3>组件分类</h3>
            <ul class="nav-list">
                <li data-component="layout">布局组件</li>
                <li data-component="message">消息组件</li>
                <li data-component="loading">加载状态</li>
                <li data-component="image">图片组件</li>
                <li data-component="modal">弹窗组件</li>
            </ul>
        </nav>

        <!-- 中间预览 -->
        <main class="preview-area">
            <div class="preview-header">
                <h2 id="component-title">组件名称</h2>
                <p id="component-desc">组件描述</p>
            </div>
            <div class="preview-content">
                <div class="component-showcase" id="component-preview">
                    <!-- 组件预览 -->
                </div>
            </div>
        </main>

        <!-- 右侧规范 -->
        <aside class="specs-panel">
            <div id="component-specs">
                <!-- 规范内容 -->
            </div>
        </aside>
    </div>

    <script>
        // 组件数据
        const components = {
            layout: {
                title: '布局组件',
                desc: '页面布局结构',
                preview: '...',
                specs: {
                    dimensions: '...',
                    colors: '...',
                    spacing: '...',
                    code: '...'
                }
            },
            // ...
        };

        // 组件切换
        // 尺寸标注
        // 代码复制
    </script>
</body>
</html>
```

### 必需功能

1. **组件导航**
   - 分类列表
   - 当前项高亮
   - 快速搜索

2. **实时预览**
   - 组件实际效果
   - 悬停显示尺寸
   - 支持交互演示

3. **规范展示**
   - 尺寸标注
   - 颜色值
   - CSS 代码
   - 使用示例

4. **代码复制**
   - 一键复制
   - 复制成功提示
   - 格式化代码

---

## 设计文档规范

### design-spec.md

**目的**: 主设计规范文档

**内容结构**:
```markdown
# [产品名称] 设计规范

## 设计原则
- 原则 1
- 原则 2

## 布局规范
- 页面结构
- 尺寸规范
- 间距规范

## 颜色系统
- 主色调
- 功能色
- 中性色

## 组件规范
- 组件清单
- 组件说明

## 交互规范
- 动画时长
- 交互状态
```

### tokens.md

**目的**: 设计令牌，方便开发直接使用

**内容结构**:
```markdown
# 设计令牌

## 颜色系统
\`\`\`css
:root {
    --color-primary: #0071e3;
    --color-background: #f5f5f7;
    /* ... */
}
\`\`\`

## 字体系统
\`\`\`css
:root {
    --font-family: -apple-system, ...;
    --font-size-sm: 12px;
    --font-size-base: 14px;
    /* ... */
}
\`\`\`

## 间距系统
\`\`\`css
:root {
    --spacing-xs: 4px;
    --spacing-sm: 8px;
    --spacing-md: 16px;
    /* ... */
}
\`\`\`
```

### components.md

**目的**: 组件库文档

**内容结构**:
```markdown
# 组件库

## Button 按钮

### 用途
触发操作

### HTML 结构
\`\`\`html
<button class="btn btn-primary">按钮</button>
\`\`\`

### CSS 样式
\`\`\`css
.btn { ... }
.btn-primary { ... }
\`\`\`

### 状态
- Default
- Hover
- Active
- Disabled
- Loading

### 使用示例
\`\`\`html
<!-- 主要按钮 -->
<button class="btn btn-primary">确定</button>

<!-- 次要按钮 -->
<button class="btn btn-secondary">取消</button>
\`\`\`
```

### interactions.md

**目的**: 交互与动画规范

**内容结构**:
```markdown
# 交互与动画

## 动画系统

### fadeIn
- 用途: 淡入效果
- 时长: 0.3s
- 缓动: ease-out

\`\`\`css
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}
\`\`\`

## 交互状态

### Button
- Hover: 背景变深，translateY(-1px)
- Active: scale(0.98)
- Focus: outline 显示
```

### dev-guide.md

**目的**: 开发实现指南

**内容结构**:
```markdown
# 开发指南

## 快速开始

### 基础 HTML
\`\`\`html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="app-container">...</div>
    <script src="app.js"></script>
</body>
</html>
\`\`\`

### 文件结构
\`\`\`
src/
├── css/
│   ├── variables.css
│   ├── base.css
│   └── components.css
├── js/
│   ├── app.js
│   └── components.js
└── index.html
\`\`\`

## 测试检查点

### 视觉检查
- [ ] 设计一致性
- [ ] 间距统一性
- [ ] 颜色对比度

### 功能检查
- [ ] 所有交互状态
- [ ] 动画流畅性
- [ ] 响应式适配
\`\`\`
```

---

## 文件组织结构

### 标准目录结构

```
project/
├── interactive.html          # 可交互原型
├── design-guide.html         # 设计规范页面
├── design-spec.md            # 主设计规范
├── tokens.md                 # 设计令牌
├── components.md             # 组件文档
├── interactions.md           # 交互规范
├── dev-guide.md              # 开发指南
├── README.md                 # 使用说明
└── progress.md               # 版本历史
```

### 版本控制

**progress.md 格式**:
```markdown
# 进度日志

## v1.0 初始版本

### 主要改动
- 创建基础布局
- 实现核心组件
- 添加交互动画

### 文件变更
| 文件 | 操作 | 说明 |
|------|------|------|
| interactive.html | 新建 | 初始原型 |
| design-spec.md | 新建 | 设计规范 |

---

## v1.1 样式优化

### 用户反馈
- 颜色对比度不够
- 按钮太小

### 主要改动
- 调整颜色对比度
- 增大按钮尺寸
```

---

## 质量检查清单

### interactive.html 检查

- [ ] 所有场景可演示
- [ ] 交互状态完整
- [ ] 响应式适配
- [ ] 无控制台错误
- [ ] 动画流畅

### design-guide.html 检查

- [ ] 所有组件可见
- [ ] 尺寸标注正确
- [ ] 代码可复制
- [ ] 导航可切换
- [ ] 布局正确

### 文档检查

- [ ] 所有文档存在
- [ ] 内容完整
- [ ] 代码可运行
- [ ] 格式正确
- [ ] 无拼写错误

---

*最后更新: 2025-02-05*
