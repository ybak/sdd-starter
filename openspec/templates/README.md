# OpenSpec 工件模板

本目录提供可复制的工件骨架，而不是一份真实变更。创建新变更时复制四个文件，并按项目 schema 放入对应位置：

```text
openspec/changes/<change-id>/
├── proposal.md                 # 来自 proposal.md
├── design.md                   # 来自 design.md
├── tasks.md                    # 来自 tasks.md
└── specs/<capability>/spec.md  # 来自 spec.md
```

使用规则：

1. 所有 `<placeholder>` 必须替换为事实、明确的 N/A 边界或已知未决项；禁止原样提交。
2. design 的 B0–B3 分档由最高风险决定；B2/B3 不能删除契约、数据、生命周期、身份、迁移、回滚与运维章节，只能填写事实性 N/A。
3. tasks 中 RED 和 GREEN 必须成对出现，且 RED 任务先于对应实现任务。
4. spec 描述可观察行为，不依赖内部类名、临时文件或实现步骤。
5. 提案归档前，将已批准的 delta spec 同步到能力主规格，并保留验证证据。
