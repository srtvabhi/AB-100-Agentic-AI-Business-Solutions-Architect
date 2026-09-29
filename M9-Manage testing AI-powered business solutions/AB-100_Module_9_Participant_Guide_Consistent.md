# AB-100 Module 9 — Manage Testing AI-Powered Business Solutions

## Module Overview

The central idea of Module 9 is:

> AI testing is not just checking whether an answer is correct. You must test business outcomes, quality, performance, safety, grounding, integrations, and behavior across different scenarios.

The overall testing lifecycle is:

```text
Test Planning → Scenario Design → Test Execution → Measurement
      ↓
Analysis → Tuning → Re-Test → Approval → Deployment
```

---

# 1. Introduction

## Concept

AI-powered business solutions need structured testing because AI output can vary, business data changes, grounding sources change, prompts change behavior, and multiple applications may participate in one workflow.

Testing must validate both technical behavior and business outcomes.

## Architecture

```text
AI Business Solution
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Agent  Model  Prompt
 └──────┼──────┘
        ▼
 Business Process
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Knowledge Apps Workflows
        │
        ▼
      Testing
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Quality Performance Safety
        │
        ▼
    Validation
        │
        ▼
      Release
```

## Key Components

- Testing objectives
- Test scenarios
- Test data
- Expected outcomes
- Validation criteria
- Performance metrics
- Safety tests
- Grounding tests
- Integration tests
- User experience tests
- Governance checkpoints

## Example

Test a customer-service agent with normal questions, missing order numbers, multiple orders, unavailable CRM, follow-up questions, and restricted information.

## Key Takeaway

**AI testing must validate behavior across realistic business conditions, not just successful prompts.**

## Architecture Questions

1. What business outcome are you testing?
2. What happens when input is incomplete?
3. What happens when knowledge is unavailable?
4. What security boundaries must be tested?
5. How will test results be measured?

---

# 2. Recommend Process Metrics for Testing AI Agents

## Concept

Define the testing objective, scope, data, roles, and success criteria before execution.

## Architecture

```text
Testing Objective
       ↓
Test Scope
       ↓
Test Data
       ↓
Test Roles
       ↓
Test Scenarios
       ↓
Execution
       ↓
Quality / Performance / Safety
       ↓
Results → Analysis → Re-Test
```

## Key Components

### Scenario-Based Testing

Test real workflows, ambiguous inputs, incomplete inputs, different phrasing, multi-turn conversations, and follow-up questions.

### Performance Testing

Test high request volume, long interactions, complex tasks, and concurrent sessions.

### Safety and Compliance Testing

Test sensitive-data protection, role-based access, DLP rules, restricted actions, and disallowed instructions.

### Usability Testing

Evaluate clarity, helpfulness, conciseness, ease of use, and re-prompts.

## Key Metrics

| Metric | What it tells you |
|---|---|
| Accuracy | Is the answer correct? |
| Relevance | Does it answer the intended question? |
| Response Time | How quickly is useful output produced? |
| Success Rate | How many tasks complete successfully? |
| Failure Rate | How often does the agent fail? |
| Token Efficiency | How efficiently is generative AI used? |
| User Satisfaction | Are users satisfied? |
| Knowledge Coverage | Does the agent have required information? |
| Stability | Does it operate consistently? |
| Load Handling | Does it work under heavy usage? |
| Guardrail Compliance | Does it respect restrictions? |

## Example

```text
Accuracy:        95%
Success Rate:    91%
Latency:          2.4 sec
Failure Rate:     5%
Satisfaction:     4.2 / 5
```

Accuracy alone does not prove that the solution meets its business target.

## Key Takeaway

**Define measurable success criteria before testing starts.**

## Architecture Questions

1. What is the success-rate target?
2. What latency is acceptable?
3. What constitutes an incorrect answer?
4. What safety conditions must always pass?
5. Which tests should be automated?

---

# 3. Create Validation Criteria for Custom AI Models

## Concept

A custom AI model must be validated across quality, performance, safety, cost, user experience, and operational reliability.

## Architecture

```text
Custom AI Model
      │
 ┌────┼────┬────────┐
 ▼    ▼    ▼        ▼
Quality Performance Safety Cost
 │     │     │        │
 └─────┼─────┼────────┘
       ▼
User Experience
       ↓
Operational Reliability
       ↓
Validation
```

## Key Components

### Quantitative Criteria

- accuracy
- latency
- throughput
- error rate
- token efficiency
- drift indicators

### Qualitative Criteria

- relevance
- completeness
- reasoning consistency
- grounding integrity
- clarity
- coherence

### Safety Criteria

- role-based access
- DLP
- prohibited-content prevention
- auditability
- traceability
- human review for sensitive workflows
- authorized grounding sources

### Operational Criteria

- scalability
- resilience
- API/connector reliability
- observability

## Example Validation Table

| Validation Area | Example Criterion |
|---|---|
| Performance | Latency < 2 seconds |
| Quality | ≥ 90% accuracy |
| Incorrect Information | ≤ 3% |
| Guardrails | 0 violations |
| Sensitive Output | 100% blocked |
| User Satisfaction | ≥ 4.5 / 5 |

These are example criteria; actual thresholds should come from solution requirements.

## Key Takeaway

**A production-ready model must satisfy quality, performance, safety, cost, and operational criteria together.**

## Architecture Questions

1. What accuracy threshold is required?
2. What latency is acceptable?
3. What safety conditions are zero-tolerance?
4. How will drift be detected?
5. What happens when the model fails validation?

---

# 4. Validate Effective Copilot Prompt Best Practices

## Concept

A prompt is part of the AI solution architecture.

A useful prompt structure is:

```text
Goal + Context + Instructions + Examples
```

## Architecture

```text
Prompt
  │
  ├── Goal
  ├── Context
  ├── Instructions
  └── Examples
        ↓
     Copilot
        ↓
      Output
        ↓
Accuracy / Relevance / Safety
        ↓
      Refine
        ↓
     Re-Test
```

## Key Components

### Prompt Validation Lifecycle

```text
Define Goal
 ↓
Add Context
 ↓
Apply Structure
 ↓
Run Prompt
 ↓
Evaluate Output
 ↓
Refine
 ↓
Re-Test
 ↓
Approve
```

### Prompt Quality Metrics

- accuracy
- consistency
- relevance
- format compliance
- tone alignment
- re-prompts
- clarification requests
- incorrect or irrelevant output

### Enterprise Prompt Pattern

```text
Goal
 ↓
Context
 ↓
Instructions
 ↓
Constraints
 ↓
Expected Format
 ↓
Exclusions
```

## Example

Weak:

```text
Summarize this report.
```

Structured:

```text
Goal:
Summarize quarterly performance.

Context:
Use the Q2 executive report.

Instructions:
- Focus on revenue, margins, and risks.
- Produce 120–160 words.
- Use professional language.

Include:
- 3 major risk areas.

Exclude:
- Marketing campaign details.
- Customer quotes.
```

## Key Takeaway

**Prompt testing should measure repeatability, not just whether one response looks good.**

## Architecture Questions

1. Is the goal unambiguous?
2. Is sufficient context provided?
3. Are constraints explicit?
4. Is the expected output format defined?
5. Does the prompt remain effective across different scenarios?

---

# 5. Design End-to-End Test Scenarios for AI Solutions Using Multiple Dynamics 365 Apps

## Concept

When AI spans multiple Dynamics 365 applications, testing one application at a time is not enough.

Test the complete business process from the initial trigger through the final outcome.

## Architecture

```text
Business Event
     ↓
Dynamics 365 Sales
     ↓
AI / Workflow
     ↓
Dynamics 365 Finance
     ↓
Dynamics 365 Supply Chain
     ↓
Dynamics 365 Customer Service
     ↓
Final Outcome
     ↓
E2E Validation
```

## Key Components

### Integration Points

Test:

- data synchronization
- entity mappings
- AI actions
- Power Automate flows
- plugins
- event triggers
- connectors
- security roles
- data boundaries
- data refresh timing

### E2E Test Structure

1. Preconditions
2. Trigger
3. Execution steps
4. AI action
5. Cross-app data movement
6. Expected outcome
7. Post-condition
8. Exception path
9. Negative test

## Example

### Order-to-Cash

```text
Create Lead
    ↓
AI identifies opportunity
    ↓
Sales creates Order
    ↓
Order syncs to Finance
    ↓
AI evaluates credit information
    ↓
Order proceeds to Supply Chain
    ↓
AI monitors fulfillment
    ↓
Delivery exception
    ↓
Customer Service receives context
    ↓
Validate final outcome
```

## Validation Areas

### Functional

- AI action triggered correctly
- correct application provides data
- workflow completes

### Non-Functional

- latency
- failure recovery
- consistency
- resilience

### Outcome

- relevance
- decision accuracy
- summarization accuracy
- task completion time

## Key Takeaway

**For multi-app AI, test the business process from trigger to final outcome.**

## Architecture Questions

1. What systems participate in the workflow?
2. Where does data move between systems?
3. Which AI actions depend on another application?
4. What happens when one application is unavailable?
5. How are security boundaries preserved?

---

# 6. Build a Strategy for Creating Test Cases Using Copilot

## Concept

Copilot can accelerate test-case creation, but generated test cases still need validation against business requirements.

## Architecture

```text
Business Requirements
        ↓
Test Objectives
        ↓
Test Case Blueprint
        ↓
Copilot Prompt
        ↓
Generated Test Cases
        ↓
Completeness / Accuracy / Maintainability
        ↓
Human Review
        ↓
Approved Test Library
        ↓
CI/CD / Regression
```

## Key Components

### Test Case Blueprint

| Field | Purpose |
|---|---|
| Test ID | Unique identifier |
| Purpose | What is being validated |
| Preconditions | Required setup |
| Inputs | Test data |
| Steps | Execution sequence |
| Expected Results | Success criteria |
| Edge Cases | Boundary/failure conditions |
| Dependencies | External requirements |

### Copilot Prompt Structure

```text
Goal
+
Context
+
Constraints
+
Quality Expectations
```

## Example

Requirement:

> The agent should help sales representatives prepare an order summary.

Generate tests for:

- normal order
- missing customer
- multiple orders
- restricted data
- unavailable system
- incorrect input

Then validate every generated test against the real business requirement.

## Validate Generated Tests

### Completeness

- acceptance criteria covered
- key workflows covered
- boundary conditions included
- failure conditions included

### Accuracy

- business rules correct
- dependencies correct
- preconditions valid

### Clarity

- steps actionable
- expected results measurable

### Maintainability

- reusable
- consistent naming
- version-friendly

## Scaling Strategy

```text
Reusable Prompt Library
        ↓
Version-Controlled Templates
        ↓
Copilot Test Generation
        ↓
Human Validation
        ↓
Automated Testing
        ↓
CI/CD
        ↓
Regression Testing
```

## Key Takeaway

**Copilot should accelerate test creation, not replace test governance.**

## Architecture Questions

1. What should Copilot generate?
2. What must humans validate?
3. How will test templates be standardized?
4. How will prompts be version controlled?
5. How will generated tests enter regression and CI/CD?

---

# Module 9 Complete Architecture

```text
Business Requirements
        ↓
Test Objectives
        │
 ┌──────┼──────────┐
 ▼      ▼          ▼
Agent  Model     Prompt
Testing Validation Testing
 └──────┼──────────┘
        ▼
E2E Multi-App Testing
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
D365  Connectors Workflows
        │
        ▼
Test Case Generation
        ↓
Copilot
        ↓
Human Validation
        ↓
Automated Testing
        ↓
Regression Testing
        ↓
Metrics / Results
        ↓
Quality / Performance / Safety
        ↓
Approval
        ↓
Release
```

---

# Architecture Decision Model

```text
What are we testing?
        ↓
Agent / Model / Prompt / E2E Solution
        ↓
What is the business outcome?
        ↓
Define measurable success criteria
        ↓
Design scenarios
        ├── Normal
        ├── Ambiguous
        ├── Negative
        ├── Edge Case
        ├── Security
        └── Performance
        ↓
Does the solution cross applications?
        ↓
Yes → E2E integration testing
        ↓
Can Copilot generate repeatable test cases?
        ↓
Generate + Validate
        ↓
Execute → Measure → Analyze → Tune
        ↓
Re-Test → Approve
```

---

# Key Concepts to Remember

| Concept | Remember |
|---|---|
| Testing Framework | Define objective, scope, data, roles, and success criteria |
| Scenario Testing | Test realistic, ambiguous, incomplete, and multi-turn inputs |
| Performance | Test latency, throughput, concurrency, and stability |
| Safety | Test access, DLP, restricted actions, and prohibited instructions |
| Quality | Measure accuracy, relevance, consistency, and grounding |
| Custom Models | Validate quality, performance, safety, cost, UX, and operations |
| Prompt Testing | Validate goal, context, instructions, constraints, and output |
| E2E Testing | Test the complete business process across applications |
| Integration | Test data sync, mappings, workflows, connectors, and boundaries |
| Copilot Testing | Use Copilot to accelerate test creation |
| Test Blueprint | Standardize ID, purpose, preconditions, inputs, steps, expected results, edge cases, dependencies |
| Human Validation | Review generated test cases for correctness and completeness |
| Regression | Re-run tests when requirements or solution components change |
| Governance | Maintain repeatable testing and approval controls |

---

# What You Should Be Able to Design

By the end of Module 9, you should be able to design a testing architecture that answers:

1. What exactly needs to be tested?
2. What business outcome defines success?
3. Which metrics prove that the AI solution works?
4. How do we validate a custom AI model?
5. How do we validate a Copilot prompt?
6. How do we test negative and edge cases?
7. How do we test AI across multiple Dynamics 365 applications?
8. How do we validate security and compliance?
9. How can Copilot accelerate test-case creation?
10. How do we keep generated tests accurate and maintainable?
11. How do tests enter regression and CI/CD processes?
12. How do we decide whether a solution is ready for release?

The core operational pattern is:

> **Define → Design → Execute → Measure → Analyze → Tune → Re-Test → Approve → Deploy**
