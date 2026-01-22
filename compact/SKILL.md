---
name: compact
description: Context Compressor & State Manager to solve LLM context window overload.
---

# Role: Context Compressor & State Manager

## Description
此 Skill 用于解决 LLM 上下文窗口过载问题。当用户输入 `/compact` 时，你将停止当前的代码编写任务，转而对整个会话历史进行深度回顾、剪枝和摘要，生成一个高密度的“状态快照（State Snapshot）”。

## Triggers
- `/compact`
- `COMPACT`
- "总结当前进度以便迁移"

## Workflow Rules

当触发此 Skill 时，请严格按照以下步骤执行：

### 1. Analysis (分析与回顾)
* **扫描历史**：从会话开始，快速扫描所有的对话对。
* **识别噪音**：标记以下内容为“噪音”，在输出中丢弃：
    * 已修复的报错信息（Error Logs）。
    * 中间的尝试过程和失败的思路。
    * 闲聊或礼貌性的废话。
* **提取信号**：提取以下关键信息：
    * **最终决策**：我们最终决定采用的库、架构或算法。
    * **当前代码状态**：哪些文件被修改了？核心逻辑是什么？
    * **未竟事业**：当前卡在哪里？下一步原本计划做什么？

### 2. Synthesis (合成快照)
* 不要输出一般的“总结”，而是生成一段**可以直接作为新会话 Prompt 使用的指令**。
* 保持客观、技术性强、高密度。

### 3. Output Format (输出格式)
请严格使用 Markdown 代码块输出最终的快照，格式如下：

```markdown
# 📂 Project Context Snapshot

## 🎯 Original Goal
[一句话描述我们最初想要实现的功能]

## 🚧 Current Status
- **Completed:** [已完成的核心功能列表]
- **Pending:** [当前正在进行但未完成的任务]
- **Key Decisions:** [重要的技术选型或架构决策，如：使用 pydantic v2, 放弃了 sqlite 改用 pg 等]

## 💻 Code Context (Crucial)
**Modified Files:**
- `path/to/file1.py`: [简述该文件的核心变动]
- `path/to/file2.ts`: [简述该文件的核心变动]

**Key Variables/State:**
[如果有一些复杂的上下文变量需要记忆，请列在这里]

## 🚀 Next Action Plan
1. [立即要做的第一步]
2. [接下来的计划]

---
*Copy the content above and paste it into a new chat to resume work seamlessly.*
```
