# AB-100 Module 6 — Case Study 2

# Regulated Financial Services Agent with Custom AI and MCP

## Scenario

Fabrikam Financial Services operates in multiple regulated markets.

The company wants an internal financial operations agent that helps employees analyze complex financial information and work with structured Dynamics 365 Finance & Operations data.

The organization has highly specialized financial terminology and business rules that are not consistently handled by a general-purpose model.

The architecture team is evaluating Microsoft Foundry custom models and Model Context Protocol (MCP) for structured business context.

## Business Requirements

The solution must:

1. Understand specialized financial terminology.
2. Retrieve current financial business context.
3. Work with structured Finance & Operations information.
4. Support complex multi-step analysis.
5. Respect regional data and access requirements.
6. Keep model and agent behavior governed.
7. Provide clear boundaries around business actions.
8. Allow business users to review high-impact outcomes.
9. Support model evaluation and monitoring.
10. Avoid creating unnecessary custom models when standard models are sufficient.

## Business Context

The organization manages:

- customers;
- vendors;
- products;
- financial dimensions;
- ledger models;
- approval chains;
- localization rules;
- business workflows.

These concepts must be interpreted consistently by the agent.

## Architecture Challenge

The architect must determine:

- whether a custom model is justified;
- how the model should be evaluated and governed;
- how structured financial context reaches the agent;
- how MCP can provide consistent business semantics;
- which actions should remain under human control.

## Proposed Architecture

```text
                         Financial Employee
                                |
                                v
                         Copilot / Agent
                                |
                                v
                       Copilot Studio Agent
                                |
                 +--------------+--------------+
                 |                             |
                 v                             v
          Custom AI Model                    MCP
       Microsoft Foundry                     Context
                 |                             |
                 |                   +---------+---------+
                 |                   |         |         |
                 |                   v         v         v
                 |              Customers   Vendors   Finance
                 |                                      Data
                 |                                       
                 +-------------------+-------------------+
                                     |
                                     v
                              Business Context
                                     |
                                     v
                               Agent Reasoning
                                     |
                          +----------+----------+
                          |                     |
                          v                     v
                    Recommendation        Human Review
                                                  |
                                                  v
                                           Approved Action
```

## Custom Model Decision

A custom model is considered because the organization has:

- specialized financial language;
- unique workflows;
- domain-specific reasoning requirements;
- strict governance requirements.

However, the architect should first confirm that a standard model cannot meet the required quality.

The decision process is:

```text
Business Requirement
        |
        v
Can a standard model meet it?
        |
    +---+---+
    |       |
   Yes      No
    |       |
    v       v
Standard   Evaluate
Model      Custom Model
             |
             v
        Training Data
             |
             v
        Fine-Tuning
             |
             v
         Evaluation
             |
             v
          Deploy
             |
             v
         Monitor
```

## Model Lifecycle

The custom model architecture includes:

```text
Data
 |
 v
Preparation
 |
 v
Training / Fine-Tuning
 |
 v
Evaluation
 |
 +--> Accuracy
 +--> Safety
 +--> Bias
 +--> Latency
 +--> Business Quality
 |
 v
Deployment
 |
 v
Monitoring
 |
 +--> Drift
 +--> Performance
 +--> Unexpected Outputs
 |
 v
Version / Rollback
```

## MCP Design

The agent needs structured financial context.

MCP provides a standardized way for the agent to work with business context such as:

```text
MCP
 |
 +--> Customer
 |
 +--> Vendor
 |
 +--> Product
 |
 +--> Financial Dimension
 |
 +--> Approval Chain
 |
 +--> Workflow
 |
 +--> Localization Rules
 |
 +--> Business Metadata
```

The agent can then reason using current structured context rather than relying only on unstructured documents.

## Human Control

The agent can:

- analyze;
- summarize;
- identify patterns;
- recommend actions;
- retrieve structured business context.

The agent should not independently make high-impact financial decisions without the required human review.

Example:

```text
Financial Data
      |
      v
MCP Context
      |
      v
Agent Reasoning
      |
      v
Recommendation
      |
      v
Human Review
      |
      +---- Approve
      |
      +---- Reject
      |
      +---- Request More Information
```

## Security and Governance

The solution should include:

- identity-based access;
- least privilege;
- regional data boundaries;
- context boundaries;
- audit logging;
- model version control;
- evaluation;
- monitoring;
- human oversight.

## Architecture Questions

### Question 1

Why might a custom model be appropriate?

**Expected Answer:**  
The organization has specialized financial terminology, domain-specific requirements, unique workflows, and potentially high-impact workloads. A custom model may be justified if a standard model cannot meet the required quality.

### Question 2

Should the organization automatically build a custom model?

**Expected Answer:**  
No. The architecture should first determine whether an existing model can satisfy the requirement. Custom models add data, training, evaluation, deployment, monitoring, and lifecycle complexity.

### Question 3

Why use MCP?

**Expected Answer:**  
MCP provides a structured contract for business context and can help the agent consistently work with entities, relationships, metadata, and business processes.

### Question 4

What should MCP security include?

**Expected Answer:**  
Identity-based access, least privilege, context boundaries, logging, and clear ownership.

### Question 5

Why keep human review for high-impact financial outcomes?

**Expected Answer:**  
The agent can support analysis and recommendations, but high-impact business decisions should remain within the organization's approved governance and human-control processes.

## Key Architectural Decisions

| Requirement | Architectural Decision |
|---|---|
| Specialized AI behavior | Evaluate custom model |
| Model lifecycle | Foundry evaluation, deployment, monitoring |
| Structured business context | MCP |
| Business entities | Finance & Operations context |
| Complex analysis | Appropriate reasoning capability |
| High-impact outcome | Human review |
| Security | Identity + least privilege |
| Governance | Evaluation + monitoring + audit |

## Final Architecture

```text
                    Financial Employee
                           |
                           v
                    Copilot / Agent
                           |
                           v
                   Copilot Studio
                           |
              +------------+------------+
              |                         |
              v                         v
       Microsoft Foundry              MCP
       Custom Model                   Context
              |                         |
              |               +---------+---------+
              |               |         |         |
              |               v         v         v
              |            Customer   Vendor   Finance Data
              |                         |
              +------------+------------+
                           |
                           v
                    Business Context
                           |
                           v
                     Agent Reasoning
                           |
                           v
                    Recommendation
                           |
                           v
                     Human Review
                           |
                           v
                   Approved Outcome
```

## Summary

This case demonstrates the relationship between **custom models, Microsoft Foundry, MCP, structured enterprise context, reasoning, governance, and human control**.

The key architectural principle is:

> Use custom AI only when the business requirement justifies it, and use structured context mechanisms such as MCP when consistent domain information is essential to agent reasoning.
