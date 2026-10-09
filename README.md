> **[中文化] text2mem**
>
> 此项目是 [MemTensor/text2mem](https://github.com/MemTensor/text2mem) 的中文翻译版本。
> 代码与上游保持一致，未做功能改动。
> - 原项目 Stars: 59
> - 主语言: Python
> - 许可证: MIT
> - 整理日期: 2026-10-09
> - 原始 README: [README_en.md](README_en.md)
>
> 著作权归上游作者所有。功能改动请提到上游仓库。

---
## 这是什么

Text2Mem 为记忆操作系统提出一套统一的记忆操作语言。它把欠约束的自然语言记忆意图，转成经过校验、可审计的 JSON IR，让同一份意图可以在不同 provider 和存储后端上一致执行。项目可用于原型验证，也可以作为生产记忆内核或教学参考。

## 核心能力

- **统一 Memory IR**：带 `stage / op / target / args / meta` 的类型化 JSON 契约，在运行前固化与执行相关的决策。
- **12 个标准操作**：覆盖编码（Encode）、检索（Retrieve、Summarize）和存储治理（Update、Label、Promote、Demote、Merge、Split、Delete、Lock、Expire）。
- **校验与不变量**：JSON Schema + Pydantic v2 双重校验，并对破坏性操作和生命周期规则（如 Lock/Expire 语义）加安全约束。
- **Provider 与后端抽象**：同一份 IR 可在不同模型服务和存储适配器上一致执行，参考后端是 SQLite，其它可插拔。
- **多 Provider**：Mock（测试）、Ollama（本地）、OpenAI（云端）。
- **语义检索**：混合检索，embedding 相似度加关键词匹配。
- **Clarify（体验增强）**：可选的预澄清步骤，在生成 IR 之前补足欠约束信息，不属于标准操作集。
- **两层基准评测**：计划层（自然语言到 IR）和执行层（IR 到状态转移），常用指标为 SMA、ESR、EMR。

## 快速开始

安装：

```bash
# Clone repository
git clone https://github.com/your-username/Text2Mem.git
cd Text2Mem

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install package
pip install -e .
```

首次运行（Mock 模式，无需 LLM）：

```bash
# Copy environment template
cp .env.example .env

# Use mock provider (no LLM required)
# Edit .env and ensure: TEXT2MEM_PROVIDER=mock

# Run demo
python manage.py demo
```

说明：上游 README 里的 clone 地址是占位符 `https://github.com/your-username/Text2Mem.git`，此处按原样保留。

## 与上游的差异

本仓库不做功能改动，只补充中文文档。如需提交功能改动，请提到上游仓库 [MemTensor/text2mem](https://github.com/MemTensor/text2mem)。

## 许可证

上游项目使用 MIT 许可证。本仓库的代码部分沿用上游同一许可证。
