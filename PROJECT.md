# UI-Guru Project

这是一个为 Claude Code 打造的 UI 设计系统 skill（技能）。

## 项目说明

本项目包含一个 Claude Code skill：`ui-design-system`

**功能**：完整的 UI 设计系统生成方法论，从需求分析到可交互设计规范页面

**目录结构**：
- `ui-design-system.skill` - 可直接下载使用的 skill 文件
- `ui-design-system/` - skill 源码目录

## 如何更新

当需要更新这个 skill 时：

1. 修改 `ui-design-system/` 目录中的文件
2. 重新打包：`zip -r ui-design-system.skill ui-design-system/`
3. 提交到 Git：`git add . && git commit -m "更新说明" && git push`

## 同步到本地 Claude Code

更新后需要同步到本地安装的 skill：

```bash
# 方式一：直接替换
cp ui-design-system.skill ~/.claude/skills/

# 方式二：解压后替换
unzip -o ui-design-system.skill -d ~/.claude/skills/
```

## Git 仓库

- **远程**: https://github.com/aa2246740/UI-Guru.git
- **本地**: /Users/wu/Documents/UI-Guru/

## 技能文件位置

- **源码**: `ui-design-system/SKILL.md`
- **打包**: `ui-design-system.skill`
- **本地安装**: `~/.claude/skills/ui-design-system.skill`
