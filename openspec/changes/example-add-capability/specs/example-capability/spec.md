# Example Capability Specification

## Purpose

为已认证调用者提供一个最小、确定性的示例能力，用于演示从需求到验证的 OpenSpec 工件如何对应。

## Requirements

### Requirement: Authenticated callers can use the capability

The system SHALL accept a valid request from an authenticated caller and return the deterministic result defined by the request contract.

#### Scenario: Valid request succeeds

- **GIVEN** an authenticated caller with access to the capability
- **WHEN** the caller sends a valid request
- **THEN** the system returns a successful response with the deterministic result
- **AND** the request does not create persistent state

#### Scenario: Unauthenticated request is rejected

- **GIVEN** a caller without valid authentication
- **WHEN** the caller invokes the capability
- **THEN** the system returns the project-standard authentication failure
- **AND** no result or persistent state is disclosed

### Requirement: Invalid input has no side effect

The system SHALL reject malformed input using the documented validation contract.

#### Scenario: Invalid input is submitted

- **GIVEN** an authenticated caller
- **WHEN** the caller sends invalid input
- **THEN** the system returns the documented validation failure
- **AND** no persistent state changes

## Out of Scope

- Persistent history, asynchronous execution, external calls and administrative configuration are outside this example capability.
