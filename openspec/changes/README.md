# 变更目录约定

每个需要 SDD 的改动使用独立目录：

```text
openspec/changes/<change-id>/
├── proposal.md
├── design.md
├── tasks.md
└── specs/
    └── <capability>/spec.md
```

`<change-id>` 使用小写连字符，描述要解决的问题或能力，而不是某个文件名或技术实现。

`../templates/` 是正式复制入口，提供完整的 proposal、design、spec、tasks 技术方案骨架。`example-add-capability/` 是教学样例，不代表真实能力、接口或数据模型；采用项目可用它理解工件之间的对应关系，但不应把样例目录当作真实变更台账。

## 最小质量要求

- proposal 说清楚为什么做、做什么、不做什么和如何验收；
- design 先给出影响评估，再给出决策、风险、测试策略和同步范围；
- spec 用可测试的 requirement/scenario 描述能力；
- tasks 将 RED、GREEN、验证和文档同步拆开；
- 未解决的契约、权限、数据或生命周期问题不允许被任务勾选掩盖。
