# UI-Guru

<div align="center">

**为 Claude Code 打造的专业 UI 设计系统生成方法论**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Ready-success.svg)](https://claude.ai/code)

*从需求分析到可交互原型，完整的设计系统生成流程*

</div>

---

## ✨ 简介

**UI-Guru** 是一个为 Claude Code 打造的 skill（技能），它提供了一套完整的 UI 设计系统生成方法论。不同于固定的组件模板库，它教 AI 如何根据产品定位和用户需求做出合适的设计选择。

### 核心特性

- 🎨 **动态设计** - 根据产品定位和用户需求动态选择设计风格
- 🚫 **反模板化** - 避免总是做纯黑/纯白界面，拒绝紫色渐变滥用
- 📋 **完整流程** - 从需求分析到可交互设计规范页面的完整方法论
- ✅ **交付验证** - 内置严格的交付验证机制，确保不遗漏任何需求
- 🇨🇳 **中文优先** - 所有输出默认使用中文（除非用户指定其他语言）

---

## 🎯 适用场景

当你需要以下功能时使用此 skill：

- 创建 Web 应用 UI 设计
- 建立完整的设计系统
- 生成设计文档或可交互原型
- 设计组件库或产品原型

---

## 📦 安装

### 方式一：手动安装

1. 下载 `UI-Guru.skill` 文件
2. 将文件复制到 Claude Code 的 skills 目录：
   - **macOS**: `~/.claude/skills/`
   - **Windows**: `%USERPROFILE%\.claude\skills\`
3. 重启 Claude Code

### 方式二：从源码构建

```bash
# 克隆仓库
git clone https://github.com/aa2246740/UI-Guru.git

# Skill 文件已在仓库根目录，直接复制即可
cp UI-Guru.skill ~/.claude/skills/
```

---

## 🚀 使用方法

### 在 Claude Code 中使用

在对话中直接调用 skill：

```
使用 UI-Guru skill 为我设计一个 [产品类型] 的 UI 系统

需求文档：/path/to/requirements.md
```

### 示例：企业运营平台设计

```markdown
请使用 UI-Guru skill，根据以下需求文档设计企业运营平台：

需求：
- 产品类型：B2B 后台管理系统
- 目标用户：企业管理者、运营人员
- 核心模块：首页中心、公告管理、订单管理
- 设计要求：专业、高效、数据驱动
```

---

## 📖 设计流程

此 skill 包含 8 个完整阶段：

### 阶段 1: 需求分析
- 产品类型、目标用户、行业特点分析
- 竞品参考和设计定位

### 阶段 2: 风格定位
- 行业色彩特征分析
- 配色方案和设计令牌建立

### 阶段 3: 设计系统定义
- 字体、间距、圆角系统

### 阶段 4: 组件设计模式
- 布局、反馈、展示、导航组件

### 阶段 5: 交互与动画
- 动画时长、缓动函数、交互状态

### 阶段 6: 原型开发
- interactive.html（可交互原型）
- design-guide.html（设计规范页面）

### 阶段 7: 文档输出
- design-spec.md、tokens.md、components.md 等

### 阶段 8: 交付验证 ⚠️
- **禁止画蛇添足** - 只实现需求文档中明确要求的内容
- **禁止空实现** - 所有页面、按钮都必须有完整功能
- **禁止视觉欺诈** - 不允许存在看起来可交互但实际无功能的元素

---

## 🏗️ 项目结构

```
UI-Guru/
├── UI-Guru.skill              # Skill 文件（可直接下载使用）
├── UI-Guru-skill/             # Skill 源码目录
│   ├── SKILL.md               # Skill 主文件
│   ├── references/            # 参考文档
│   │   ├── design-thinking.md      # 设计思维指南
│   │   ├── component-patterns.md   # 组件设计模式
│   │   ├── workflow.md             # 完整设计流程
│   │   ├── color-theory.md         # 配色理论
│   │   └── output-formats.md       # 输出格式规范
│   └── assets/examples/        # 示例资源
│       ├── layout-patterns.md      # 布局模式示例
│       └── color-palettes.md       # 配色方案示例
├── README.md                  # 项目说明
├── PROJECT.md                 # 项目文档（Claude Code 使用）
└── LICENSE                    # MIT 许可证
```

---

## 🤝 贡献指南

欢迎贡献！请遵循以下步骤：

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 提交规范

- 清晰描述你的更改
- 如果可能，提供使用示例
- 确保代码/文档风格一致

---

## 📝 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

---

## 🙏 致谢

- 感谢 Anthropic 团队打造的 Claude Code
- 感谢所有使用和改进此 skill 的开发者

---

## 📮 联系方式

- **Issues**: [GitHub Issues](https://github.com/aa2246740/UI-Guru/issues)
- **Discussions**: [GitHub Discussions](https://github.com/aa2246740/UI-Guru/discussions)

---

<div align="center">

**⭐ 如果这个 skill 对你有帮助，请给它一个 Star！**

Made with ❤️ by the community

</div>
