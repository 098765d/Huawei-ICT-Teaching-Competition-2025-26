# TCREI Prompt：优化 README.md，使其看起来专业、清晰、可信

## Task

你是一位资深开源项目维护者、技术文档专家和 GitHub README 优化顾问。请基于我提供的现有 README.md 内容，重写并优化它，使其看起来更专业、更清晰、更适合 GitHub 开源仓库展示。

你的任务不是简单润色，而是完成以下工作：

1. 保留原 README 中所有真实、可验证的信息。
2. 重构 README 的信息架构，使读者能快速理解项目是什么、解决什么问题。
3. 改善语言表达，使其专业、简洁、可信，避免夸大。
4. 优化 Markdown 排版，包括标题层级、表格、代码块、列表、徽章占位、目录、项目结构等。
5. 如果原文缺少关键信息，不要编造。
6. 输出一个可以直接替换原 README.md 的完整 Markdown 文件。
7. 在最终 README 后附上一个简短的 “Change Summary”，说明你做了哪些主要优化。

## Context

我的目标是让 README.md 看起来更专业，适合放在 GitHub 仓库首页。请假设读者包括：

- 招聘方或面试官
- 研究合作者
- 开源用户
- 技术评审人员
- 对项目感兴趣但不了解背景的开发者

README 应该优先体现以下质量：

- 第一屏能快速说明项目价值
- 结构清楚，易于浏览
- 安装和运行步骤可复现
- 对项目亮点的描述专业但不夸张
- 对缺失信息保持诚实，不虚构
- Markdown 风格符合高质量 GitHub 项目的常见写法

请根据原 README 的内容自动判断项目类型，例如：

- Python / machine learning 项目
- Web app 项目
- Research code 项目
- Data science project
- Course / teaching material repository
- Library / package
- CLI tool
- Notebook-based project

然后选择最合适的 README 结构。

## References

请参考高质量 GitHub README 的常见结构，但不要机械套模板。可以根据项目内容选择以下模块：

1. Project Title
2. Badges（占位即可，例如 build status / license / Python version / framework version / documentation）
3. Overview
4. Key Features
5. Demo / Screenshots / Results
6. Project Motivation / Background
7. Tech Stack
8. Repository Structure
9. Installation
10. Quick Start
11. Usage Examples
12. Configuration
13. Dataset / Input Data（如果适用）
14. Model / Methodology（如果适用）
15. Results / Evaluation（如果适用）
16. API Documentation（如果适用）
17. Deployment（如果适用）
18. Testing（如果适用）
19. Roadmap
20. Contributing
21. Citation（如果是研究项目）
22. License
23. Contact / Acknowledgements

请遵循以下写作风格：

- 专业、直接、技术可信
- 避免营销化语言
- 避免空泛形容词（如 “powerful”, “amazing”, “revolutionary”），除非有证据支持
- 用具体信息替代笼统描述
- 多用主动语态
- 保持 README 对新用户友好
- 命令、路径、文件名、参数必须用代码格式标注
- 不要删除原 README 中的重要技术细节
- 不要编造不存在的 benchmark、论文、功能、许可证、作者、部署方式或结果

## Evaluate

在生成最终 README 前，请先在内部检查以下标准（不需要展示详细推理过程）：

1. Accuracy
   - 是否严格基于原 README 内容？
   - 是否避免虚构功能、数据、结果、论文、许可证或部署信息？
2. Clarity
   - 是否让首次访问者在 30 秒内理解项目定位与价值？
   - 章节顺序是否自然、可扫描？
3. Professionalism
   - 语言是否简洁、可信、适合 GitHub？
   - 是否避免夸张营销语？
4. Reproducibility
   - 安装与运行步骤是否完整、可执行、前置条件清晰？
5. Markdown Quality
   - 标题层级是否合理？
   - 代码块语言是否标注？
   - 表格、列表、目录是否易读？
   - 是否适合直接保存为 `README.md`？
6. Project Positioning
   - 是否在开头清楚说明项目是什么、为谁设计、解决什么问题？
   - 是否突出项目最重要的技术亮点？

若任一项不达标，请继续迭代直到达标。

## Iterate

请按以下迭代流程工作：

1. 第一轮：分析原 README 的问题（结构、语言、缺失信息、可信度、可复现性）。
2. 第二轮：设计更专业的 README 信息架构。
3. 第三轮：生成完整优化版 README.md。
4. 第四轮：自我审查并修正以下问题：
   - 是否有虚构内容？
   - 是否有不清楚的安装步骤？
   - 是否有过度宣传？
   - 是否有 Markdown 格式问题？
   - 是否有重复、冗长或不必要的段落？

最终只输出：
- 完整优化后的 README.md
- README 末尾附 “Change Summary”（3-8 条要点）

---

现在开始。以下是我的原始 README 内容：

```markdown
[在这里粘贴你的 README.md 全文]
```

补充事实（可选）：

```text
[在这里粘贴运行命令、目录结构、模型指标、已知问题、路线图等真实信息]
```
