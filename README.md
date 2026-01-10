# AgentToybox | 智能体工坊
> 可爱俏皮但工程优先的智能体 Playground，专注于 Agentic AI 的可复现 Demo、清晰讲解与实用模式，从入门到进阶覆盖工具调用、记忆与 RAG、规划执行、评测基线与生产化落地。少点自嗨，多点跑通。
> A playful building Agentic AI. It focuses on reproducible demos, clear walkthroughs, and practical patterns—from “hello agent” to tool-use, memory/RAG, planning, evaluation, and production readiness. Less hype, more runnable code. 

---

## Why this repo
**Agentic AI**（代理式 / 智能体）正在从“概念与玩具”快速走向“工程与产品”。但大量内容存在：
- 只讲概念，不给可复现代码
- Demo 依赖隐式环境，跑不起来
- 缺乏从入门到进阶的系统路线
- 缺少评测、观测、可靠性与安全的工程方法

本仓库的目标是：**用一套可复现的工程化范式**，系统讲清 Agentic AI，并提供每一章对应的 Demo、测试与评测基线。

---

## Audience | 适合谁
- 想系统学习 Agentic AI 的工程师/研究者/产品同学
- 需要可复现 Demo、可测评结果、可扩展架构的人
- 希望把 Agent 做成“可上线、可运维”的系统的人

---

## Principles | 核心原则
1. **Reproducible first**：每个 Demo 都可一键运行（含依赖锁定、种子、最小数据集）
2. **Engineering-grade**：有评测、有日志、有回放、有错误处理与边界
3. **From basics to pro**：课程式结构，从 0 到 1，再到生产级实践
4. **Bilingual**：每篇文章提供中英文版本（内容一致，术语统一）
5. **Terminal-native authoring**：建议用终端 AI 辅助写作与代码（但所有结论必须可复现、可验证）

---

## Repo Structure | 仓库结构
```
.
├── docs/
│   ├── zh/                      # 中文文章
│   ├── en/                      # English posts
│   └── glossary.md              # 术语表 / Glossary
├── demos/
│   ├── 00-hello-agent/          # 最小可运行 Agent
│   ├── 10-tool-calling/         # 工具调用
│   ├── 20-rag-memory/           # RAG + Memory
│   ├── 30-planning/             # 规划/分解
│   ├── 40-multi-agent/          # 多智能体
│   ├── 50-evaluation/           # 评测基线
│   └── 60-production/           # 工程化：观测、回放、权限、成本
├── datasets/
│   └── mini/                    # 最小数据集（可公开、可复现）
├── scripts/
│   ├── setup.sh                 # 环境初始化
│   ├── run_demo.sh              # 统一入口：运行 demo
│   └── eval.sh                  # 统一入口：评测
├── assets/
│   ├── images/
│   └── donate/                  # 打赏二维码（WeChat/Alipay）
├── .github/
│   ├── workflows/               # CI：lint/test/eval
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── Makefile
├── pyproject.toml               # Python 依赖（建议锁定）
├── README.md
└── README.zh-CN.md              # 可选：单独中文 README
```

---

## Quickstart | 快速开始
> 目标：在 5 分钟内跑通第一个可复现 Demo。

### 1) Create env | 创建环境
- 推荐：Python 3.11+（或用 Docker）
- 建议提供 `Makefile` 统一入口

示例（你可以按项目实际工具替换）：
```bash
make setup
```

### 2) Run first demo | 跑第一个 Demo
```bash
make demo DEMO=demos/00-hello-agent
```

### 3) Run evaluation | 运行评测（可选）
```bash
make eval DEMO=demos/50-evaluation
```

---

## Content Roadmap | 内容路线（从入门到专业）
每个阶段都包含：
- 一篇文章（docs/zh + docs/en）
- 一个可复现 Demo（demos/xx）
- 一个最小评测或断言（tests/ 或 demos 内置 eval）

路线详见：`docs/zh/roadmap.md` & `docs/en/roadmap.md`

---

## Terminal AI Authoring | 用终端 AI 写作与维护（建议工作流）
你可以用任意“终端内的 AI 助手/编码助手”来：
- 生成章节骨架与 TODO
- 辅助写 Demo、补测试、补文档
- 自动化生成双语草稿（人工审校、术语统一、示例可运行）

**准则**：AI 产出必须通过 `make test` / `make eval`，并在文档中标注复现实验步骤与版本信息。

---

## Support | Star / Sponsor / 打赏
如果这个仓库对你有帮助：
- 给个 Star（对开源传播最重要）
- GitHub Sponsors（推荐）
- 或扫码打赏（见 `assets/donate/`）

> 你可以在 README 顶部加徽章：Stars、CI、License、Sponsor。

---

## Contributing | 贡献方式
欢迎：
- 提 Issue：缺失内容、Bug、想看的 Demo
- 提 PR：补充章节、修复复现问题、增加评测基线

建议约定：
- 文档：中英内容保持结构一致（先中文或先英文均可，但最终同步）
- Demo：必须包含 `README.md`（运行方式、期望输出、评测/断言）
- 代码：必须能在 CI 中跑通最小测试

---

## License
建议：Apache-2.0 或 MIT（按你的偏好选择）

---

## Disclaimer
本仓库内容用于学习与工程实践参考。涉及外部服务调用时，请遵循对应服务条款与安全合规要求。


![dashang]( ./images/pay.png)

