# 更新日志

本项目的所有显著更改都将记录在本文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
本项目遵循 [语义化版本](https://semver.org/lang/zh-CN/spec/v2.0.0.html)。

## [0.2.0] - 2026-02-07

### 新增
- **coolee-leijun-speech**: 全新的内容创作 skill，将任意主题或文本转换为雷军风格的演讲稿
  - 数据驱动的叙事，包含精确数字和对比
  - 宏大叙事与情感共鸣
  - 专业术语创造
  - 三段式结构（痛点 → 解决方案 → 价值揭晓）
  - 雷军标志性口头禅和句式
  - Master Prompt 模板，确保输出一致性
  - 完整的智能台灯演讲稿示例
  - 支持中英文输入

### 变更
- 增强 README.md，添加详细的 skill 描述、安装指南和项目结构
- 更新项目文档，遵循开源项目最佳实践

### 修复
- 改进 SKILL.md 文档，添加中英文双语术语对照
- 为所有 skills 添加清晰的使用说明

## [0.1.0] - 2026-02-07

### 新增
- 基于 baoyu-skills 规范的初始项目结构
- **coolee-claudian-updater**: 用于自动更新 Obsidian Claudian 插件的工具 skill
  - 自动检测 Obsidian vault 和插件位置
  - 从 GitHub releases 检查版本
  - 更新前自动备份
  - 安全安装，支持回滚
- CLAUDE.md 项目开发指南
- MIT 许可证
- 基础 README 和文档结构
