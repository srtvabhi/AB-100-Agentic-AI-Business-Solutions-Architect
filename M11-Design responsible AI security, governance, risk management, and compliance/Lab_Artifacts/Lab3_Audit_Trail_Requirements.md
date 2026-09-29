# Lab 3 — AI Audit Trail Requirements

## Identity

Record:
- User identity
- Agent identity where applicable
- Role or authorization context
- Timestamp

## Agent Changes

Record:
- Agent version
- Previous version
- New version
- Configuration change
- Change owner
- Deployment environment

## Model Changes

Record:
- Model version
- Previous model
- New model
- Evaluation reference
- Approval
- Deployment date

## Data and Knowledge Changes

Record:
- Knowledge source
- Dataset/data version where applicable
- Source change
- Owner
- Effective date

## Connector and Tool Changes

Record:
- Connector/tool name
- Version/configuration
- Permission change
- Environment
- Approver

## Sensitive Actions

Record:
- User
- Agent
- Requested action
- Tool invoked
- Parameters where appropriate
- Authorization result
- Approval result
- Outcome

## Investigation Capability

The audit design should allow the organization to trace:

User
→ Agent
→ Prompt/Instruction
→ Knowledge/Data
→ Model
→ Tool/Connector
→ Business Action
→ Result

The objective is to reconstruct the relevant solution state after a security, compliance, or AI-quality incident.
