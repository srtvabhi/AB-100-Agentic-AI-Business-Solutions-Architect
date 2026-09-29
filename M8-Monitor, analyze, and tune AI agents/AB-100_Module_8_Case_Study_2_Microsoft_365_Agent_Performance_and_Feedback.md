# AB-100 Module 8 — Case Study 2: Microsoft 365 Agent Performance and Feedback

## Scenario

Fabrikam Technology has deployed a Microsoft 365 agent for sales and service employees.

The agent helps users:

- summarize customer information
- locate product documentation
- prepare meeting follow-ups
- retrieve sales and service information
- initiate approved business actions

The agent is widely used, but adoption is uneven.

Some users report:

- slow responses
- excessive or irrelevant information
- incomplete answers
- difficulty completing actions
- inconsistent experiences between Teams and other Microsoft 365 experiences

The architecture team needs to analyze usage and feedback and determine where tuning is required.

## Requirements

1. Monitor agent adoption and usage.
2. Measure task completion and abandonment.
3. Analyze user feedback and conversation patterns.
4. Identify high-frequency failure scenarios.
5. Distinguish UX issues from knowledge and integration issues.
6. Establish performance baselines.
7. Create a backlog for continuous improvement.

## Systems and Data

| System | Purpose |
|---|---|
| Microsoft 365 Copilot / Agent | User-facing AI experience |
| Teams | Primary user interaction |
| Dynamics 365 Sales | Customer and opportunity context |
| Dynamics 365 Customer Service | Case context |
| SharePoint | Business knowledge |
| Usage Analytics | Adoption and usage |
| Feedback / Support Data | Improvement backlog |

## Architecture Challenge

The organization sees a high number of abandoned conversations.

The architect must determine whether abandonment is caused by:

- slow responses
- irrelevant answers
- insufficient knowledge
- missing business actions
- confusing interaction design

## Architecture

```text
                         Employee
                            │
                            ▼
                    Microsoft 365 Agent
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
           Teams       Dynamics 365    SharePoint
                         Sales/Service   Knowledge
              │             │             │
              └─────────────┼─────────────┘
                            ▼
                       Agent Output
                            │
          ┌─────────────────┼─────────────────┐
          ▼                 ▼                 ▼
       Usage             Feedback          Telemetry
      Analytics           Data               Data
          │                 │                 │
          └─────────────────┼─────────────────┘
                            ▼
                    Backlog Analysis
                            │
             ┌──────────────┼──────────────┐
             ▼              ▼              ▼
            UX          Knowledge      Integration
          Tuning          Tuning          Tuning
             │              │              │
             └──────────────┼──────────────┘
                            ▼
                     Validate Changes
                            │
                            ▼
                    Updated Agent
```

## Example

Analytics show:

```text
Agent usage:             High
Task completion:         76%
Conversation abandonment: 18%
Average latency:         4.9 sec
Knowledge accuracy:      95%
```

Feedback shows users frequently say:

> "The answer is useful, but I cannot find the next action."

The issue is not primarily knowledge accuracy.

The agent provides information but does not provide a clear path to the approved business action.

A possible improvement is:

```text
User Request
     ↓
Agent Understanding
     ↓
Grounded Customer Context
     ↓
Answer
     ↓
Recommended Next Action
     ↓
Approved Business Action
```

## Architecture Questions

### 1. Which metrics are important?

**Expected answer:**

Monitor:

- active users
- agent invocation
- task completion
- abandonment
- latency
- response quality
- action success
- user feedback

### 2. How can the architect identify whether abandonment is a performance problem?

**Expected answer:**

Compare abandonment with latency trends, task completion, conversation transcripts, and action failures.

If abandonment rises with latency, investigate performance. If latency is stable but users cannot complete tasks, investigate UX, knowledge, or action design.

### 3. How should the backlog be organized?

**Expected answer:**

Categorize issues into areas such as:

- performance
- knowledge
- UX
- integration
- accuracy
- governance

Then prioritize based on impact, frequency, severity, and effort.

### 4. What is the purpose of a performance baseline?

**Expected answer:**

A baseline provides the normal operating range against which future changes can be detected and evaluated.

## Key Architectural Decisions

- Measure adoption and business outcomes, not only system health.
- Correlate usage analytics with user feedback.
- Use conversation data to identify recurring friction.
- Separate knowledge accuracy from task-completion problems.
- Establish measurable baselines before tuning.
- Validate improvements against both technical and user-centered metrics.

## Final Architecture

```text
Microsoft 365 Agent
        ↓
User Interaction
        ↓
Usage + Telemetry + Feedback
        ↓
Performance / Quality Analysis
        ↓
Backlog
        ↓
Targeted Improvement
        ↓
Validation
        ↓
Agent Release
        ↓
Continuous Monitoring
```
