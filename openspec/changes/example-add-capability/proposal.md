# Proposal: Add an Example Capability

## Why

使用者需要一个可验证的能力入口，但当前系统缺少该入口或其行为没有明确契约。

## What Changes

- 增加一个最小能力，接收经过认证的请求并返回确定性结果；
- 为该能力定义可测试的行为、错误和权限边界；
- 增加对应的自动化验证与运行文档。

## Non-goals

- 不引入未被需求证明的异步处理、持久化、外部依赖或管理界面；
- 不改变现有无关能力的 API、数据或权限模型。

## Impact

- Capability: `example-capability`（新增）；
- Backend impact: B1，除非 design 的影响评估发现状态持久化、跨服务调用或高权限风险；
- Validation: V1 + V2，若部署装配或真实用户入口受影响则补 V3/V4；
- Documentation: 更新项目的接口、配置和运行文档索引（按实际影响选择）。

## Acceptance Evidence

- 未认证请求被拒绝；
- 合法请求返回设计约定的结果；
- 路由在真实应用装配中可达；
- 所有受影响的验证层通过，或未运行原因被如实记录。
