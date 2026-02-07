# Coolee Skills (中文)

[English](README.md) | [中文](README.zh.md)

Claude Code 的效率技能集合，遵循 `JimLiu/baoyu-skills` 的结构和标准。

## 项目概述

本仓库提供了一系列精心设计的技能，用于增强你的 Claude Code 工作流程，涵盖内容创作、AI 生成和实用工具自动化任务。

## 安装

在 Claude Code 中使用这些技能：

1. 克隆本仓库：
   ```bash
   git clone https://github.com/YOUR_USERNAME/coolee-skills.git
   ```

2. 按照 Claude Code 文档将本地技能添加到你的配置中。

## 技能列表

### 内容创作类

#### **coolee-leijun-speech**
将任意主题或文本转换为极具感染力的雷军风格演讲稿，包含数据驱动的叙事、宏大叙事和情感共鸣。适用于产品发布、演示文稿和营销内容。

**功能特性：**
- 数据驱动的叙事，包含精确数字和对比
- 宏大叙事与情感连接
- 专业术语创造
- 三段式结构（痛点 → 解决方案 → 价值揭晓）
- 雷军标志性口头禅和句式
- 默认输出简体中文

**使用方法：**
- "用雷军风格写一个关于[主题]的演讲稿"
- "将这段文字转换为雷军风格的演讲稿"
- "Write a Lei Jun-style speech about [topic]"

### 实用工具类

#### **coolee-claudian-updater**
自动更新 Obsidian 的 Claudian 插件，从 GitHub 检查最新版本并下载更新文件。

**功能特性：**
- 自动检测 Obsidian vault 和 Claudian 插件位置
- 从 GitHub releases 检查当前版本 vs 最新版本
- 更新前自动创建备份
- 安全下载和安装更新
- 支持回滚功能

**使用方法：**
- "更新我的 Claudian 插件"
- "检查 Claudian 是否需要更新"
- "Update my Claudian plugin"

## 开发指南

详见 [CLAUDE.md](./CLAUDE.md) 了解开发规范和项目约定。

**核心规范：**
- **运行时**：所有脚本和执行使用 Bun (`npx bun`)
- **语言**：所有逻辑优先使用 TypeScript
- **命名**：所有技能必须使用 `coolee-` 前缀（例如：`coolee-my-skill`）
- **描述**：`SKILL.md` 中的所有技能描述必须使用第三人称
- **结构**：技能按分类组织在 `skills/` 目录下

## 目录结构

```
coolee-skills/
├── skills/
│   ├── content-skills/          # 内容创作和处理
│   │   └── coolee-leijun-speech/
│   ├── ai-generation-skills/    # AI 驱动的生成工具
│   └── utility-skills/          # 通用工具和维护
│       └── coolee-claudian-updater/
├── CLAUDE.md                    # 项目规范和约定
└── README.md                    # 本文件
```

## 贡献

欢迎贡献！请确保：
1. 你的技能遵循 `coolee-` 命名规范
2. 文档清晰且使用第三人称描述
3. 代码遵循 TypeScript/Bun 规范
4. 技能放置在适当的分类目录中

## 路线图

计划中的技能：
- AI 图像生成工具
- 文档处理工具
- 版本控制自动化
- 更多内容创作助手

## 许可证

MIT

## 致谢

灵感来源于 [JimLiu/baoyu-skills](https://github.com/JimLiu/baoyu-skills) - 特别感谢其出色的技能结构和规范。
