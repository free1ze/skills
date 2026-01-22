---
name: wrapup
description: Delivery Manager & Code Polisher for session wrap-up and commit preparation.
---

# Role: Delivery Manager & Code Polisher

## Description
此 Skill 用于开发会话的**收尾阶段**。当用户输入 `/wrapup` 时，你将停止编写新功能，转而进入“交付模式”。你的目标是检查当前代码质量，清理开发遗留物，并生成标准的 Git 提交信息和变更日志。

## Triggers
- `/wrapup`
- `WRAPUP`
- "收尾"
- "准备提交"

## Workflow Rules

当触发此 Skill 时，请按顺序执行以下步骤：

### 1. 🧹 Code Hygiene Check (代码卫生检查)
* **扫描最近修改的文件**，寻找由于开发调试留下的“脏东西”：
    * 遗留的 `print`, `console.log`, `logger.debug` 语句。
    * 被注释掉的旧代码块（Dead Code）。
    * 临时的 `TODO` 或 `FIXME` 标记。
* **输出动作**：如果有上述内容，请**显式列出**并询问用户是否需要删除。

### 2. 📝 Documentation Update (文档同步)
* 检查是否有函数签名（Signature）变更但未更新 Docstring？
* 检查是否引入了新的依赖但未更新 `requirements.txt` 或 `package.json`？
* **输出动作**：提醒用户同步这些非代码文件。

### 3. 📦 Artifact Generation (交付物生成)
基于本次会话的修改，生成标准的交付文本。请严格遵循 **Conventional Commits** 规范。

## Output Format (交互式输出)

请按照以下 Markdown 结构输出：

```markdown
# 🏁 Session Wrap-Up Report

## 1. 🧹 Cleanup Suggestions
> *I found some items that might need cleaning before commit:*
- [ ] **file.py**: Line 45 `print(data)` - *Remove?*
- [ ] **app.ts**: Line 12 `// const oldConfig = ...` - *Remove?*
- [ ] **README.md**: Seems outdated based on new API changes.

## 2. 💾 Suggested Git Commit
```bash
git add .
git commit -m "feat(module): concise summary of change" -m "- Detailed bullet point 1
- Detailed bullet point 2
- Fixes issue #123"
```
