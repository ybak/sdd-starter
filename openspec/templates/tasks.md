# Tasks: <change title>

> 每项最多一个工作日；每项完成后仓库保持可构建、测试可运行。勾选需在执行记录中引用命令和正向证据。

## 1. Contract and Design Readiness

- [ ] 1.1 确认 `<API/event/data/authorization>` 未决问题；未决项按 design 的 owner、截止点和默认行为处理，未确认者阻塞相关实现。
- [ ] 1.2 将 design 中的接口、数据、生命周期、权限、部署和文档影响转为本任务清单的具体工作项；无影响项写明事实性 N/A。
- [ ] 1.3 为每个新增 V2/V3/V4 用例登记行为/风险、低层不足、已有覆盖、预计成本、资源清理和维护归属；确认预算文件与覆盖映射的更新范围。

## 2. Test-first: RED

- [ ] 2.1 先行 RED：新增 `<unit test location>`，断言 `<behavior and edge case>`；运行并记录预期失败原因。
- [ ] 2.2 先行 RED：新增 `<integration/assembly/contract test location>`，断言 `<route/event/authorization/configuration behavior>`；运行并记录预期失败原因。
- [ ] 2.3 先行 RED：若涉及状态或异步，新增 `<migration/concurrency/lifecycle test location>`，断言 `<idempotency, retention, retry, cleanup, or recovery behavior>`。

## 3. Implementation: GREEN

- [ ] 3.1 实现 `<minimal domain behavior>`，使 2.1 GREEN；运行 V1。
- [ ] 3.2 实现 `<boundary, route, event, or adapter>`，使 2.2 GREEN；运行 V2。
- [ ] 3.3 实现 `<data/lifecycle/authorization/deployment behavior>`，使 2.3 GREEN；运行相应 V1/V2。
- [ ] 3.4 复核错误、日志、指标和审计不泄露机密或不必要的个人数据。

## 4. Migration and Operations

- [ ] 4.1 执行并验证 `<migration/backfill/configuration rollout>`；记录前置、成功条件和回滚触发条件。
- [ ] 4.2 实现或验证 `<metric/log/alert/runbook>`，使故障、降级、积压或权限拒绝可观察。
- [ ] 4.3 演练 `<rollback/recovery/cleanup>`，或记录经批准的 N/A 边界。

## 5. End-to-end and Release Evidence

- [ ] 5.1 运行受影响的 V0/V1/V2；记录命令、范围、结果和未运行原因。
- [ ] 5.2 更新并守卫 e2e 覆盖映射；MR 输出 V4 选择理由、选中/未选 spec 数，未知可执行路径按全量 V4 处理。
- [ ] 5.3 运行 V3，证明构建产物与运行配置中 `<capability>` 已实际生效；记录正向证据。
- [ ] 5.4 仅在设计要求时运行 V4；说明为什么该断言不能下移，使用隔离资源并记录清理结果。发布/定期回归以 enforce 模式跑全量 V4。
- [ ] 5.5 记录耗时、执行/跳过数与预算判定；超预算先按 design 的覆盖重分配顺序处置，不使用重试、放宽、全局加时或机器扩容。
- [ ] 5.6 更新 capability spec、接口/事件契约、配置/部署说明、运行手册和变更索引。
- [ ] 5.7 执行 diff、机密扫描和独立审查；未解决风险和延期项保持可见后再申请归档。
