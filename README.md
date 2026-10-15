# SDD Starter Template

一个可复制到任意软件仓库根目录的**规格驱动开发（Specification-Driven Development, SDD）**起步模板。它将变更分流、可审计设计、测试先行和分层验证固化为团队与 AI 编码代理共享的工作约定。

本模板不包含业务代码、产品名称、真实地址、账号、令牌、云资源或内部架构细节。所有尖括号占位符必须由采用项目自行替换。

## 适用范围

- 有多个贡献者或 AI 编码代理的仓库；
- 需要让需求、设计、测试与发布证据可追溯的团队；
- 使用 OpenSpec 或兼容的变更目录工作流的项目。

它不是重量级流程：纯文档、格式化、测试修复以及不改变能力契约的低风险修复，可以按 `AGENTS.md` 的分流规则快速处理。

## 目录

```text
sdd-starter/
├── AGENTS.md                         # 贡献者与编码代理的执行规则
├── .gitignore                        # 本地机密、运行产物与登录态忽略规则
├── docs/
│   ├── sdd-operating-model.md        # 工件职责、门禁与审查角色
│   ├── testing-pyramid.md            # V0–V4 金字塔、决策树、B0–B3 映射
│   ├── test-growth-governance.md     # 用例准入、超预算处置与 V4 选择规则
│   ├── verification-budget.example.yaml # 预算、历史阈值与执行模式样例
│   ├── e2e-coverage-map.example.json # 按改动选择 V4 的安全缺省样例
│   └── verification-strategy.md      # 证据、隔离、预算和结果记录
└── openspec/
    ├── config.yaml                   # 通用 OpenSpec 工作流规则
    ├── templates/                    # 可复制的 proposal/design/spec/tasks 技术方案模板
    └── changes/
        ├── README.md                 # 变更目录约定
        └── example-add-capability/   # 含 proposal/design/spec/tasks 的完整示例
```

## 采用步骤

1. 将本目录内容复制到目标仓库根目录；不要复制任何源仓库的本地配置、构建产物或历史变更。
2. 在 `AGENTS.md` 中把 `<static-command>`、`<unit-command>`、`<integration-command>`、`<build-command>`、`<smoke-command>`、`<e2e-command>` 替换为项目的真实命令。
3. 在 `openspec/config.yaml` 中选择目标项目已安装的 schema，并补充项目特有的兼容性、数据归属和文档索引规则。
4. 先阅读 `docs/testing-pyramid.md` 和 `docs/test-growth-governance.md`，将项目的实际测试命令、层级预算、历史阈值、用例准入、真实环境前置、e2e 资源清理及按改动选择规则固化下来；从 `verification-budget.example.yaml` 与 `e2e-coverage-map.example.json` 创建项目自己的版本化配置。
5. 从 `openspec/templates/` 复制 proposal、design、spec、tasks 到描述性 `change-id`；`example-add-capability/` 只用于学习完整工件如何相互对应。
6. 先在一个小变更上试运行：确认 RED 测试能失败、GREEN 后各层验证能运行、归档流程能同步主规格。
7. 把分支保护、必需检查、代码审查和发布审批配置到代码托管平台；仓库文字规则不能替代平台权限控制。

## 设计原则

1. **规格先于实现**：新增能力、跨模块改动，以及涉及 API、数据、权限、异步生命周期或部署边界的改动，先形成可评审规格。
2. **测试先行且可归因**：每个实现任务前都有独立的 RED 测试任务；测试通过不等于功能生效，必须保留可观察的正向证据。
3. **验证逐层升级**：能由静态检查、单元测试或自给自足的集成测试覆盖的断言，不进入昂贵的冒烟或端到端测试。
4. **安全缺省**：缺少真实环境、凭据、关键断言或覆盖映射时，验收应明确失败或升级验证范围，不能伪装为通过。
5. **文档与契约同属交付物**：接口、配置、数据、部署和运行手册的变更必须有同步任务。
6. **最小公开面**：示例仅使用占位符；真实机密放在受忽略的本地或密钥管理系统中。

## 深入阅读与复制入口

- `docs/sdd-operating-model.md`：了解 proposal、design、spec、tasks 和验证记录如何形成一条证据链。
- `docs/testing-pyramid.md`：为项目定义 V0–V4 的职责、断言放置决策树、B0–B3 最低验证组合、资源隔离和预算规则。
- `docs/test-growth-governance.md`：定义新增用例准入记录、重复覆盖约束、超预算处置顺序、MR 子集与发布全量 V4 的分工。
- `docs/verification-budget.example.yaml` 与 `docs/e2e-coverage-map.example.json`：分别是预算/历史阈值和按改动选择 V4 的机器可读配置样例。
- `openspec/templates/`：复制完整的 proposal、design、spec、tasks 技术方案骨架；其中 design 含 API/事件、数据、生命周期、权限、迁移、回滚、运维和测试策略的固定章节。

## 发布到 GitHub 前

- 选择并添加适合团队的开源许可证；
- 删除或重写所有项目专有的名称、域名、IP、端口、内部系统名、账号、令牌、数据样本和事件记录；
- 执行全文机密扫描，并由未参与整理的人独立复核；
- 确认 `.gitignore` 覆盖本地环境文件、浏览器登录态、测试报告、trace、录像和构建目录；
- 在 README 中写清模板的适用边界，而不是把它宣传为自动保证质量或安全的工具。

## 最小验收

复制后，至少应做到：

- `AGENTS.md` 中的每个验证占位命令均已替换；
- 一个示例变更包含 proposal、design、tasks 和对应规格；
- 实施任务可以呈现一次预期 RED，再呈现 GREEN；
- 变更影响的验证层、结果和未运行原因被如实记录；
- `git diff` 与机密扫描均未发现不应公开的内容。
