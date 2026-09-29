# AB-100 Module 9 — Case Study 1: Customer Service AI Agent Testing

## Scenario

Contoso Industrial Systems is deploying a Copilot Studio customer service agent that helps support representatives find troubleshooting guidance, summarize customer cases, and recommend next actions.

The agent uses enterprise knowledge sources and business data. The architecture team must define a structured testing process before production release.

## Requirements

- Validate that the agent produces relevant and accurate responses.
- Measure response time and scenario success rate.
- Test incorrect, ambiguous, and unsupported questions.
- Validate safety and business-policy constraints.
- Create repeatable regression tests for future changes.
- Use measurable criteria instead of relying only on subjective review.

## Systems and Data

- Microsoft Copilot Studio agent
- Enterprise troubleshooting and product documentation
- Customer service case data
- Approved response policies
- Test prompts and expected outcomes
- User feedback from pilot testing

## Architecture Challenge

The team needs to decide what should be measured for each test scenario and how the results should determine whether the agent is ready for release.

The architecture should cover functional behavior, AI quality, performance, safety, and operational reliability.

## Architecture

```text
Users / Testers
      |
      v
Test Scenarios
      |
      +----------------------+
      |                      |
      v                      v
Prompt / Input         Expected Outcome
      |                      |
      +----------+-----------+
                 |
                 v
        Copilot Studio Agent
                 |
        +--------+---------+
        |                  |
        v                  v
Knowledge Sources     Business Data
        |
        v
Response / Action
        |
        v
Validation Metrics
  - Accuracy
  - Relevance
  - Success Rate
  - Response Time
  - Failure Rate
  - Safety / Guardrails
  - Stability
        |
        v
Release Decision / Regression Baseline
```

## Example

A test scenario asks:

> "A customer reports that the motor controller overheats after 30 minutes. What troubleshooting steps should the support representative follow?"

The test records:

| Metric | Example Validation |
|---|---|
| Accuracy | Response matches approved troubleshooting guidance |
| Relevance | Response addresses overheating rather than unrelated symptoms |
| Response time | Meets the defined business target |
| Success rate | Scenario completes without unsupported claims |
| Safety | Agent does not invent repair procedures |
| Grounding | Important guidance comes from approved knowledge |
| Stability | Repeated runs produce acceptable results |

The architecture team stores the scenario and its expected result so it can be executed again after prompt, knowledge, or agent changes.

## Architecture Questions

1. Which metrics should be mandatory for every AI-agent test?
2. Which metrics are specific to customer service scenarios?
3. How should unsupported questions be tested?
4. How can regression testing detect a quality decrease after a prompt change?
5. Which results should block production release?

## Expected Answers

1. Accuracy, relevance, success/failure rate, performance, safety/compliance, and operational reliability should be considered.
2. Case-resolution success, grounding in approved support content, response relevance, and escalation behavior are important.
3. Include prompts for missing information, unsupported requests, ambiguous questions, and requests outside the agent's scope.
4. Maintain a reusable test set and compare new results against the approved baseline.
5. Safety or compliance failures and critical business-process failures should be treated as release blockers according to organizational policy.

## Key Architectural Decisions

- Define measurable validation criteria before execution.
- Use scenario-based tests rather than testing only individual prompts.
- Separate quality metrics from operational metrics.
- Maintain a regression test set for future releases.
- Include safety and grounding checks in addition to response quality.
- Use test results as evidence for release approval.

## Final Architecture

```text
Define Business Outcomes
        |
        v
Define Test Scenarios
        |
        v
Define Metrics + Validation Criteria
        |
        v
Execute AI Agent Tests
        |
        v
Measure Results
        |
        v
Analyze Failures
        |
        +----> Tune Prompt / Knowledge / Agent
        |              |
        |              v
        |          Re-Test
        |
        v
Approved Regression Baseline
        |
        v
Production Release
```
