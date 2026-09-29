# AB-100 Module 8 — Hands-On Lab Guide

## Lab Overview

| Lab | Module 8 Concept | Platform | Architect Skill |
|---|---|---|---|
| Lab 1 | Monitoring agents and performance metrics | Copilot Studio + Power Platform Admin Center + Power BI/Excel | Define monitoring signals and thresholds |
| Lab 2 | Backlog and user feedback analysis | Excel/Power BI + Copilot Studio analytics | Convert feedback into prioritized improvements |
| Lab 3 | Telemetry analysis and AI performance tuning | Azure Monitor/Log Analytics or Excel/Power BI + Copilot Studio | Correlate telemetry and select targeted tuning |

---

# Lab 1 — Monitor an AI Agent

## Platform

Copilot Studio + Power Platform Admin Center + Power BI/Excel

## Objective

Monitor agent health, performance, usage, and task outcomes.

## Part 1 — Open the Agent

1. Open your Copilot Studio environment.
2. Open an existing test agent or create a test agent.
3. Open the agent's analytics/monitoring area.
4. Review available conversation, session, engagement, and outcome metrics.
5. Record the metrics available in your environment.

**What to expect:** You should see analytics that can be used to understand agent usage and outcomes.

## Part 2 — Run Test Conversations

1. Open the agent test pane.
2. Run the questions in `Lab1_Test_Scenarios.md`.
3. Record:
   - response time
   - completion
   - fallback/error behavior
   - escalation requirement
4. Repeat each scenario at least once.
5. Compare the results with the expected business behavior.

**What to expect:** Different requests should produce different outcomes, including successful answers and controlled fallback behavior.

## Part 3 — Review Monitoring Data

1. Open the agent analytics view.
2. Review available usage and performance metrics.
3. Open Power Platform Admin Center.
4. Review the environment analytics and available monitoring information.
5. Export or copy the relevant metrics if your environment supports it.
6. Open `Lab1_Agent_Monitoring_Metrics.csv`.
7. Load the CSV into Excel or Power BI.
8. Create measures or calculations for:
   - error rate
   - successful task rate
   - abandonment rate
   - escalation rate
9. Compare the results with `Lab1_Monitoring_Thresholds.md`.
10. Identify dates that cross warning or critical thresholds.

**What to expect:** September 4 and September 5 should require investigation because multiple metrics exceed the defined thresholds.

## Part 4 — Create Monitoring Actions

1. Create a monitoring table with:
   - Metric
   - Current value
   - Threshold
   - Severity
   - Owner
   - Action
2. Add an action for every critical metric.
3. Define the evidence required before tuning the agent.
4. Identify whether each issue is likely:
   - operational
   - performance
   - quality
   - usage
   - governance
5. Save the monitoring results.

## Part 5 — Architecture Review

1. Map agent execution to telemetry.
2. Map telemetry to metrics.
3. Map metrics to alerts.
4. Map alerts to investigation.
5. Map investigation to tuning.
6. Map tuning to validation.

```text
Agent
  ↓
Execution
  ↓
Telemetry
  ↓
Metrics
  ↓
Alerts
  ↓
Investigation
  ↓
Tuning
  ↓
Validation
```

---

# Lab 2 — Analyze User Feedback and Build an Improvement Backlog

## Platform

Excel/Power BI + Copilot Studio analytics

## Objective

Analyze feedback, identify recurring issues, categorize the backlog, and select the evidence needed for tuning.

## Part 1 — Load Feedback

1. Open `Lab2_User_Feedback_Backlog.csv`.
2. Load the data into Excel or Power BI.
3. Verify the columns:
   - FeedbackID
   - Date
   - Channel
   - Scenario
   - Feedback
   - Category
   - Severity
   - Frequency
   - Status
4. Filter the data to `Status = Open`.

**What to expect:** You should see the unresolved feedback items requiring analysis.

## Part 2 — Analyze Frequency

1. Sort the open items by Frequency descending.
2. Identify the highest-frequency issue.
3. Group issues by Category.
4. Calculate total frequency by category.
5. Group issues by Severity.
6. Identify all High severity items.

**What to expect:** Performance, UX, integration, and knowledge issues should become visible as distinct problem groups.

## Part 3 — Create the Improvement Backlog

1. Create a new table with:
   - FeedbackID
   - Problem
   - Evidence
   - Root-cause hypothesis
   - Proposed change
   - Validation metric
   - Priority
2. Copy the open feedback items into the table.
3. Use `Lab2_Backlog_Prioritization_Rules.md`.
4. Prioritize recurring high-severity problems.
5. Keep the root-cause hypothesis separate from the confirmed root cause.

**What to expect:** The backlog should distinguish evidence from assumptions.

## Part 4 — Validate Against Agent Analytics

1. Open Copilot Studio analytics for the agent.
2. Review the scenarios associated with the highest-frequency feedback.
3. Compare feedback with conversation or usage data.
4. Identify whether the problem is reproducible.
5. Record the evidence.
6. Update the root-cause hypothesis if the evidence changes it.

**What to expect:** Feedback should be connected to actual agent behavior before a change is proposed.

## Part 5 — Select Tuning Actions

1. Select the three highest-priority open issues.
2. For each issue determine whether the likely tuning layer is:
   - knowledge
   - prompt/behavior
   - integration
   - workflow
   - UX
   - governance
3. Define one validation metric for each.
4. Define one test scenario for each.
5. Save the backlog.

## Part 6 — Architecture Review

```text
User Interaction
      ↓
Feedback / Analytics
      ↓
Issue Categorization
      ↓
Evidence
      ↓
Root-Cause Hypothesis
      ↓
Prioritized Backlog
      ↓
Targeted Change
      ↓
Validation
```

---

# Lab 3 — Interpret Telemetry and Tune AI Performance

## Platform

Azure Monitor + Log Analytics when available; otherwise Excel/Power BI with the supplied telemetry dataset

## Objective

Correlate telemetry signals and select targeted performance tuning.

## Part 1 — Load Telemetry

1. Open `Lab3_Telemetry_Data.csv`.
2. Load the data into Excel or Power BI.
3. Verify:
   - ModelCalls
   - InputTokens
   - OutputTokens
   - RetrievalItems
   - WorkflowTimeSec
   - ModelTimeSec
   - APITimeSec
   - TotalLatencySec
   - TaskCompletion
   - UserSatisfaction
   - CostUSD
4. Sort by `Timestamp`.

**What to expect:** September 3–5 show a noticeable degradation compared with September 1–2.

## Part 2 — Correlate Signals

1. Compare `InputTokens` with `TotalLatencySec`.
2. Compare `RetrievalItems` with `InputTokens`.
3. Compare `ModelCalls` with `ModelTimeSec`.
4. Compare `APITimeSec` with `TotalLatencySec`.
5. Compare `TotalLatencySec` with `TaskCompletion`.
6. Compare `TotalLatencySec` with `UserSatisfaction`.
7. Identify the strongest relationships.

**What to expect:** Higher context and token usage coincide with higher latency, lower completion, lower satisfaction, and higher cost.

## Part 3 — Identify the Root Cause

1. Open `Lab3_Tuning_Hypotheses.md`.
2. Evaluate Hypothesis A against the telemetry.
3. Evaluate Hypothesis B against the telemetry.
4. Evaluate Hypothesis C against the telemetry.
5. Evaluate Hypothesis D against the telemetry.
6. Mark each hypothesis:
   - Supported
   - Partially supported
   - Not supported
7. Record the evidence for each decision.

**What to expect:** Retrieval/context size and repeated model calls should be investigated before replacing the model.

## Part 4 — Apply Targeted Tuning

1. Reduce unnecessary retrieved context.
2. Keep only relevant knowledge items for the customer-summary scenario.
3. Refine the prompt to request only the required business summary.
4. Remove unnecessary repeated model calls where the workflow allows.
5. Keep the business outcome unchanged.
6. Do not remove required security or governance checks.

**What to expect:** The optimized design should reduce unnecessary context, model calls, tokens, and latency without removing required business information.

## Part 5 — Validate the Tuning

1. Open `Lab3_Tuning_Test_Scenarios.md`.
2. Run every scenario before tuning if baseline data is available.
3. Apply the tuning changes.
4. Run the same scenarios again.
5. Record:
   - latency
   - model calls
   - token usage
   - retrieval items
   - workflow time
   - API time
   - completion
   - quality
6. Open `Lab3_Tuning_Validation.csv`.
7. Compare the results with the target values.
8. Reject the change if quality or task completion falls below the acceptable level.
9. Keep the change if performance improves while business quality remains acceptable.

**What to expect:** The target is lower latency and cost with maintained or improved task completion.

## Part 6 — Optional Azure Monitor / Log Analytics Path

1. Open Azure Monitor.
2. Open the relevant Application Insights or Log Analytics resource if available.
3. Review request duration.
4. Review failed requests and dependency failures.
5. Review dependency/API duration.
6. Compare model execution time with dependency time.
7. Identify whether latency originates from the model, workflow, or API dependency.
8. Create an alert for a sustained latency threshold.
9. Document the alert condition.
10. Map the alert to an investigation action.

**What to expect:** Telemetry should allow you to distinguish end-to-end latency from a specific dependency or execution layer.

## Part 7 — Final Architecture Review

```text
Production Agent
      ↓
Telemetry
      ↓
Signal Correlation
      ↓
Root Cause
      ↓
Targeted Tuning
      ↓
Quality + Performance Validation
      ↓
Release
      ↓
Continuous Monitoring
```

---

# Module 8 Final Architecture

```text
                         USERS
                           │
                           ▼
                    ┌──────────────┐
                    │   AI Agent   │
                    └──────┬───────┘
                           │
            ┌──────────────┼──────────────┐
            ▼              ▼              ▼
         Knowledge       Tools         Workflows
            │              │              │
            └──────────────┼──────────────┘
                           ▼
                    Agent Execution
                           │
                           ▼
                    Telemetry / Logs
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
   Performance          Quality             Usage
   Metrics              Metrics             Analytics
        │                  │                  │
        └──────────────────┼──────────────────┘
                           ▼
                 User Feedback / Backlog
                           │
                           ▼
                    Issue Analysis
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
      Prompt            Knowledge        Integration
       Tuning             Tuning             Tuning
        │                  │                  │
        └──────────────────┼──────────────────┘
                           ▼
                    Validate / Test
                           │
                           ▼
                      Production
                           │
                           └───────────────► Monitoring
```
