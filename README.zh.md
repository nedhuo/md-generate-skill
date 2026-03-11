# md-generate-skill

一个用于约束 AI 生成高可读性 Markdown 文档的 skill 规则集。

## 解决什么问题

AI 默认生成的 Markdown 文档存在以下问题：

- 滥用加粗/斜体，重点反而不突出
- 标题层级混乱，H1/H2/H3 随意嵌套
- 过度使用列表，连续性叙述被打碎成 bullet fragments
- 内容冗余啰嗦，充斥套话开头和总结结尾
- 代码块缺少语言标注，语法高亮失效
- 表格滥用，简单键值对也用表格
- 笔记结构不统一，每次生成格式都不一样
- 缺乏视觉层次，大段文字堆砌

这个 skill 通过明确的规则和场景模板，让 AI 在生成 Markdown 时有判断依据，而不是靠直觉乱用格式。

## 使用方式

### OpenCode / Kiro（远程加载）

在项目的 `.kiro/skills/` 目录下创建引用文件：

```yaml
# .kiro/skills/md-generate.md
url: https://raw.githubusercontent.com/nedhuo/md-generate-skill/main/skill.md
```

### OpenCode（本地安装）

```bash
mkdir -p ~/.opencode/skills/md-generate
curl -o ~/.opencode/skills/md-generate/SKILL.md \
  https://raw.githubusercontent.com/nedhuo/md-generate-skill/main/skill.md
```

安装后重启 OpenCode，当你说"整理笔记"、"生成文档"、"写教程"等关键词时，skill 会自动加载。

### 任意 AI 助手

将 `skill.md` 的内容粘贴到 prompt 开头，再让 AI 生成 Markdown 文档。

## Skill 规则概览

### Part 1：通用规则（所有文档适用）

| 规则 | 内容 |
|---|---|
| 1.1 标题层级 | 每篇文档只有一个 H1，H2 为主章节，H3 为子节，禁止跳级 |
| 1.2 加粗/斜体 | 每段最多 1-2 处加粗，只用于真正关键术语，禁止装饰性加粗 |
| 1.3 列表 | 3 项以上无序枚举用列表，步骤用有序列表，其余写成散文 |
| 1.4 代码块 | 必须标注语言，行内代码只用于技术标识符 |
| 1.5 表格 | 只在多实体多属性对比时使用，禁止用表格替代简单列表 |
| 1.6 视觉间距 | 段落间一空行，H2 章节间两空行，禁止连续堆叠标题 |
| 1.7 精简写作 | 禁止套话开头、重复总结、免责声明式语言 |
| 1.8 链接保留 | 整理外部内容时保留原文链接和文中提到的有价值链接 |
| 1.9 内容密度 | 操作步骤写完整，背景信息写精简，高风险警告加粗说清楚后果 |
| 1.10 输出方式 | 默认写入文件，用户说"输出/展示/show me"时才内联输出 |

### Part 2：场景模板

- **技术笔记**：概念 → 原理 → 用法 → 示例 → 注意事项 → 参考链接
- **项目文档**：标题+一句话描述 → Quick Start → What/Why → 架构 → 配置/API → 贡献
- **教程/How-to**：目标 → 前置条件 → 步骤 → 验证 → 常见问题
- **会议/阅读笔记**：来源/背景 → 关键点 → 决策/行动项 → 待解决问题

### Part 3：反模式速查表

每个规则都有对应的"为什么这样做是错的"和"正确做法"，方便快速对照。

## 文件结构

```
md-generate-skill/
  skill.md          # Skill 规则文件（AI 加载此文件）
  README.md         # 英文说明
  README.zh.md      # 中文说明（本文件）
  examples/
    good.md         # 正确示例
    bad.md          # 反面示例
```

## 许可证

MIT
