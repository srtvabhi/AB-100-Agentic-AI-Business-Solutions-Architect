# AB-100 Module 8 — Case Study 1: Customer Service Agent Monitoring and Tuning

## Scenario

Contoso Industrial Systems has deployed an AI customer-service agent that helps customers check orders, troubleshoot products, and find warranty information.

The agent uses:

- Copilot Studio
- Dynamics 365 Customer Service
- SharePoint knowledge
- Power Automate
- Enterprise monitoring and analytics

After several months in production, the service team reports:

- slower responses
- more escalations to human agents
- repeated customer questions
- occasional outdated warranty answers

The architecture team needs to establish a monitoring and tuning process.

## Requirements

1. Monitor operational health and latency.
2. Measure response quality and task completion.
3. Analyze customer feedback and support-agent escalations.
4. Identify whether issues originate from knowledge, prompts, integrations, or workflows.
5. Create alerts for significant performance degradation.
6. Validate tuning changes before production release.
7. Maintain human oversight for customer-impacting changes.

## Systems and Data

| System | Purpose |
|---|---|
| Copilot Studio | Customer-service agent |
| Dynamics 365 Customer Service | Customer and case context |
| SharePoint | Warranty and troubleshooting knowledge |
| Power Automate | Business workflows |
| Monitoring Platform | Telemetry and alerts |
| Support Tickets | User feedback and issue backlog |

## Architecture Challenge

The team initially assumes that every incorrect response requires a model or prompt change.

The architect needs to create a diagnostic approach that identifies the actual root cause before tuning.

## Architecture

```text
                         Customer
                            │
                            ▼
                    ┌──────────────┐
                    │ AI Service   │
                    │ Agent        │
                    └──────┬───────┘
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
       D365 Customer   SharePoint    Power Automate
          Service       Knowledge       Actions
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                     Agent Response
                           │
                           ▼
                Telemetry / Feedback
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
        Performance      Quality       Usage
          Metrics        Signals       Analytics
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                    Issue Backlog
                           │
                           ▼
                    Root Cause Analysis
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
       Knowledge        Prompt          Integration
        Tuning           Tuning            Tuning
          │                │                │
          └────────────────┼────────────────┘
                           ▼
                    Validate / Test
                           │
                           ▼
                       Production
```

## Example

Monitoring shows:

```text
Average latency:       2.1 sec → 4.8 sec
Task completion:       94% → 83%
Customer escalation:   6% → 14%
Warranty accuracy:     97% → 91%
```

Investigation finds that a new SharePoint warranty document is being retrieved together with an older document.

The primary problem is therefore **knowledge freshness and retrieval**, not necessarily the model.

The tuning process becomes:

```text
Identify conflicting documents
        ↓
Remove/archive obsolete document
        ↓
Validate knowledge retrieval
        ↓
Run warranty test scenarios
        ↓
Evaluate response quality
        ↓
Publish change
        ↓
Monitor metrics
```

## Architecture Questions

### 1. What should be monitored?

**Expected answer:**

Monitor:

- availability
- latency
- errors
- task completion
- response quality
- escalation rate
- user feedback
- knowledge retrieval behavior
- governance signals

### 2. How should the team determine the root cause?

**Expected answer:**

Correlate telemetry, conversation behavior, knowledge retrieval, integration failures, and user feedback before changing prompts or models.

### 3. What should happen when performance degrades?

**Expected answer:**

Create an alert, investigate the affected layer, identify root cause, apply targeted tuning, validate the change, and continue monitoring.

### 4. How should user feedback enter the improvement process?

**Expected answer:**

Convert recurring feedback and escalations into categorized backlog items and prioritize them using business impact, frequency, severity, and implementation effort.

## Key Architectural Decisions

- Use multilayer monitoring rather than uptime-only monitoring.
- Separate technical metrics from quality and business metrics.
- Diagnose knowledge, prompt, integration, and workflow issues independently.
- Use controlled validation before publishing tuning changes.
- Maintain continuous monitoring after every change.

## Final Architecture

```text
Agent
  ↓
Execution
  ↓
Telemetry + User Feedback
  ↓
Metrics / Analytics
  ↓
Root Cause Analysis
  ↓
Targeted Tuning
  ↓
Validation
  ↓
Production
  ↓
Continuous Monitoring
```
