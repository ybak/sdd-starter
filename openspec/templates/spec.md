# <Capability Name> Specification

## Purpose

<能力为谁解决什么问题；不描述内部实现。>

## Requirements

### Requirement: <observable behavior>

The system SHALL <normative behavior>.

#### Scenario: <successful path>

- **GIVEN** <precondition>
- **WHEN** <actor action>
- **THEN** <observable result>
- **AND** <state, event, authorization, or audit result if applicable>

#### Scenario: <rejection or failure path>

- **GIVEN** <precondition>
- **WHEN** <invalid, unauthorized, conflicting, or unavailable action>
- **THEN** <specific failure contract>
- **AND** <state must not change, if applicable>

### Requirement: <lifecycle, consistency, or security invariant>

The system SHALL <invariant>.

#### Scenario: <boundary condition>

- **GIVEN** <condition>
- **WHEN** <action>
- **THEN** <invariant remains true>

## Compatibility and Observability

- <consumer compatibility promise or N/A>
- <required user-visible, audit, metric, log, or event evidence>

## Out of Scope

- <explicit exclusion>
