# AB-100 Module 10 — Design ALM Process for AI-Powered Business Solutions

## Module Overview
Application Lifecycle Management (ALM) for AI solutions is broader than traditional application ALM.

For AI solutions, ALM must manage data, knowledge sources, prompts, AI models, agent behavior, connectors, actions, evaluation datasets, security/DLP, environments, telemetry, drift, versioning, and rollback.

The goal is to maintain governed, secure, reproducible, and consistent AI behavior from development through production and retirement.

---

# 1. Introduction

## Concept
AI behavior can change even when application code does not. A dataset, knowledge source, prompt, model, connector, or agent configuration can change the result.

Therefore, ALM must control the entire AI solution.

## Architecture
```text
                 AI Solution
                     |
       +-------------+-------------+
       |             |             |
       v             v             v
     Data          Models        Prompts
       |             |             |
       +-------------+-------------+
                     |
              Agent / Application
                     |
       +-------------+-------------+
       |             |             |
       v             v             v
   Connectors     Actions      Knowledge
                     |
                     v
              ALM Governance
                     |
       +-------------+-------------+
       |             |             |
      DEV          TEST        PRE-PROD
       |             |             |
       +-------------+-------------+
                     |
                     v
                   PROD
                     |
                     v
          Monitor → Improve → Retire
```

## Key Components
| Component | What ALM controls |
|---|---|
| Data | Version, quality, lineage, sensitivity |
| Model | Version, evaluation, deployment |
| Prompt | Version, testing, behavior |
| Agent | Configuration, behavior, dependencies |
| Knowledge | Sources, indexes, versions |
| Connector | Authentication, DLP, version |
| Action | Logic, permissions, failure handling |
| Environment | Separation and access |
| Telemetry | Performance, failures, drift |
| Release | Approval, deployment, rollback |

## Example
A customer-service agent works correctly in Dev. A SharePoint knowledge source changes before production, and the agent gives different answers. The code did not change, but AI behavior did.

Therefore, the knowledge source is also an ALM-managed artifact.

## Key Takeaway
**Everything that can change AI behavior should be considered an ALM-managed artifact.**

## Architecture Questions
1. What AI components can change behavior without code changes?
2. Which components require versioning?
3. Why isolate Dev, Test, and Production?
4. Where should evaluation happen?
5. What evidence is required before production?

---

# 2. Design an ALM Process for Data Used in AI Models and Agents

## Concept
Data is part of the AI application. ALM should cover training/fine-tuning datasets, evaluation/regression datasets, grounding knowledge, prompts, policies/guardrails, telemetry, and feedback.

## Architecture
```text
PLAN & CATALOG
      ↓
INGEST & PREPARE
      ↓
DEVELOP & TEST
      ↓
STAGE & APPROVE
      ↓
DEPLOY / SERVE
      ↓
MONITOR
      ↓
EVOLVE / RETIRE
```

### Environment Architecture
```text
DEV
 |
 | Red / mutable data
 v
TEST
 |
 | Evaluation + Golden datasets
 v
PRE-PROD
 |
 | Approved candidate
 v
PROD
 |
 | Gold / immutable promoted assets
 v
Monitoring + Drift Detection
```

## Key Components
### Data Contract
Define purpose, fields, owners, retention, sensitivity, and data boundaries.

### Data Quality
Check missing values, outliers, imbalance, schema changes, and consistency.

### Data Lineage
```text
Source
  ↓
Transformation
  ↓
Dataset
  ↓
Model / Agent
  ↓
Production Output
```

### Golden Dataset
A stable dataset used for repeatable evaluation and regression.

### Data Residency
Determine where prompts, inputs, outputs, and AI-related processing can occur.

### Drift
```text
Training Data
     ↓
Production Data
     ↓
Distribution Changes
     ↓
Potential AI Quality Change
```

## Promotion Gates
| Gate | Main validation |
|---|---|
| A → B | Ownership, catalog, sensitivity |
| B → C | Data quality and lineage |
| C → D | Evaluation and safety |
| D → E | Compliance and residency |
| E → F | Runtime readiness |

## Example
```text
Raw Data
   ↓
Quality Check
   ↓
Sensitive Data Classification
   ↓
De-identification
   ↓
Versioned Dataset
   ↓
Golden Evaluation Dataset
```

## Key Takeaway
**Data ALM is as important as application ALM because changing data can change AI behavior.**

## Architecture Questions
1. Which datasets should be versioned?
2. What is the difference between red and gold data?
3. Why is lineage important?
4. When should data drift trigger re-evaluation?
5. What evidence is required before promoting a dataset?

---

# 3. Design an ALM Process for Copilot Studio Agents, Connectors, and Actions

## Concept
A Copilot Studio solution includes more than the agent. It can contain connectors, actions, skills, prompt assets, Dataverse components, and environment configuration.

## Architecture
```text
                 COPILOT STUDIO
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
      Agent        Connector        Action
        |              |              |
        |              v              v
        |        External System   Power Automate
        |                              |
        +--------------+---------------+
                       |
                       v
                  Dataverse
                       |
                       v
                 ALM Pipeline
                       |
        +--------------+--------------+
        |              |              |
       DEV            TEST           PROD
   Unmanaged       Managed        Managed
```

## Key Components
### Agent ALM
```text
Design → Build → Test → Regression → Approve → Deploy → Monitor
```

### Connector ALM
```text
Author → Authentication Validation → DLP Validation → Security Approval → Publish
```

### Action ALM
```text
Define Outcome → Build → Test Inputs/Outputs → Test Errors → Promote → Monitor
```

## Environment Rules
| Environment | Purpose |
|---|---|
| DEV | Build and experiment |
| TEST | Regression and validation |
| PROD | Approved managed solution |

Production should not be directly edited.

## Example
A Copilot Studio agent creates a customer service case through a Dataverse connector. A connector-authentication change can break the agent even when the agent itself is unchanged.

Therefore, agent, connector, action, and Dataverse configuration must be tested together.

## Key Takeaway
**An agent release is a solution release, not just a prompt release.**

## Architecture Questions
1. Which Copilot Studio components should move together?
2. Why test connectors separately?
3. Why use managed solutions in Test and Production?
4. How should connector authentication be handled?
5. What should trigger rollback?

---

# 4. Design ALM Processes for Microsoft Foundry Agents

## Concept
Foundry agents require controlled lifecycle management across orchestration, prompts, behavior, actions, data/grounding, security mappings, connectors, and safety policies.

## Architecture
```text
                 FOUNDRY AGENT
                      |
        +-------------+-------------+
        |             |             |
      Logic        Grounding      Actions
        |             |             |
      Prompts       Data         Connectors
        |             |             |
        +-------------+-------------+
                      |
                 Versioned Bundle
                      |
                      v
                    DEV
                      |
                    Gate
                      |
                      v
                    TEST
                      |
                    Gate
                      |
                      v
                    PROD
                      |
                      v
              Telemetry / Feedback
```

## Key Components
**Dev:** design, prompt testing, connector configuration, integration prototypes.

**Test:** regression, scenario validation, integration testing, behavior evaluation, action safety.

**Production:** validated and approved versions under monitoring.

## Versioning
Track:
- Version identifier
- Change description
- Dependencies
- Risk analysis
- Evaluation results
- Rollback option

## Promotion Gates
### Dev → Test
Validate core functionality, safety, data mappings, connectors, actions, and prompt quality.

### Test → Production
Validate regression, data access, policy compliance, performance, cost, human validation, and documentation.

## Key Takeaway
**A Foundry agent should move between environments as a controlled, versioned release.**

## Architecture Questions
1. What components belong to an agent release?
2. What must be checked before Dev → Test?
3. What additional evidence is needed before Test → Prod?
4. How should production secrets differ from development configuration?
5. How should telemetry feed the next release?

---

# 5. Design an ALM Process for Custom AI Models

## Concept
Custom AI models can change because training data, configuration, business requirements, behavior, or production data changes.

## Architecture
```text
Business Requirement
        ↓
Plan & Design
        ↓
Data Preparation
        ↓
Model Development
        ↓
Evaluation
        |
   +----+----+
   |         |
 Fail       Pass
   |         |
Improve     TEST
             ↓
     Performance /
     Governance /
       Cost Gate
             ↓
           PROD
             ↓
       Monitor + Drift
             |
       +-----+-----+
       |           |
    Stable       Drift
       |           |
       v           v
    Operate     Retrain /
                Refine
```

## Key Components
### Model Version
Track model version, training dataset version, configuration, hyperparameters, environment, and evaluation results.

### Golden Dataset
Use a stable evaluation dataset for regression.

### Model Card
Maintain metrics, constraints, and recommended usage boundaries.

### Monitoring
Track accuracy, latency, cost, throughput, task success, safety, user behavior, and drift.

## Example
```text
Detect Drift
    ↓
Investigate Data
    ↓
Create Updated Dataset
    ↓
Retrain / Tune
    ↓
Evaluate
    ↓
Create New Model Version
    ↓
Promote Through Gates
```

## Key Takeaway
**A custom model is not finished when deployed. Its ALM must support monitoring, retraining, versioning, rollback, and retirement.**

## Architecture Questions
1. What should be versioned with a model?
2. Why is a Model Card useful?
3. What is model drift?
4. What should trigger retraining?
5. What evidence is required before a new model version reaches Production?

---

# 6. Design an ALM Process for AI in Dynamics 365 Finance and Supply Chain

## Concept
Finance and Supply Chain AI can interact with important ERP processes such as predictions, scoring, classification, anomaly detection, document understanding, knowledge retrieval, and Copilot assistance.

ALM must protect both AI behavior and business transactions.

## Architecture
```text
        Dynamics 365 Finance
                 |
        +--------+--------+
        |                 |
        v                 v
     ERP Data          AI Model
        |                 |
        v                 v
   Data Contract      Copilot/Prompt
        |                 |
        +--------+--------+
                 |
            AI Workflow
                 |
        +--------+--------+
        |                 |
        v                 v
   Automation         Business Rule
        |                 |
        +--------+--------+
                 |
                 v
          Business Process
                 |
                 v
          Monitoring / Drift
```

## Key Components
- AI models
- Copilot prompts
- Feature engineering pipelines
- Knowledge sources
- Automation/orchestration flows
- Connectors
- Dataverse virtual entities
- APIs

## Environment Architecture
```text
DEV
 |
 | Build models, prompts, integrations
 v
TEST
 |
 | Safe/anonymized production-like data
 | Regression testing
 v
PROD
 |
 | Approved AI capabilities
 v
Monitoring
```

Use environment variables for environment-specific endpoints, model names, and connection strings.

## Example
For AI-assisted purchase-order approval:

```text
AI Recommendation
       ↓
Business Rules
       ↓
Authorization
       ↓
Approval Workflow
       ↓
Transaction
```

The AI should not bypass established business controls.

## Promotion Gates
### DEV → TEST
- Data profiling completed
- Training/prompt logic documented
- Initial quality evaluation passed
- Safety evaluation passed

### TEST → PROD
- Accuracy/relevance/stability thresholds met
- Safety validation passed
- ERP workload performance validated
- Security/compliance completed
- Data residency reviewed
- Deployment package approved

## Key Takeaway
**For ERP AI, ALM must protect both the AI model and the underlying financial or supply-chain business process.**

## Architecture Questions
1. Which Finance/Supply Chain AI assets require versioning?
2. Why should Test use safe or anonymized production-like data?
3. Why are environment variables important?
4. Which ERP operations require stronger guardrails?
5. What should be checked before an AI capability reaches Production?

---

# 7. Design ALM Processes for AI in Dynamics 365 Customer Experience and Service

## Concept
Customer-experience AI includes Copilot, agent behaviors, case summarization, classification, prediction, knowledge retrieval, reply suggestions, next-best actions, and customer interaction workflows.

ALM must control both AI configuration and customer-data flow.

## Architecture
```text
                Customer Interaction
                        |
                        v
               Dynamics 365 Apps
                        |
       +----------------+----------------+
       |                |                |
       v                v                v
Customer Service      Sales        Customer Insights
       |                |                |
       +----------------+----------------+
                        |
                        v
                 AI / Copilot
                        |
        +---------------+---------------+
        |               |               |
        v               v               v
    Knowledge        Prompts        AI Models
        |               |               |
        +---------------+---------------+
                        |
                        v
                  AI Response
                        |
                        v
                 Business Action
                        |
                        v
                  Telemetry
```

## Environment Architecture
```text
DEV
 ↓
TEST
 ↓
PRE-PROD / UAT
 ↓
PROD
```

**DEV:** build prompts, agent workflows, data mappings, orchestration.

**TEST:** validate AI behavior, regression, summarization, classification, and case-resolution suggestions.

**PRE-PROD:** validate business acceptance, performance, safety, compliance, and live-like customer scenarios.

**PROD:** run approved AI with monitoring.

## Key Components
- Copilot prompts
- Agent behaviors
- Knowledge sources
- Semantic indexing
- AI model configuration
- Power Automate flows
- Plugins
- Data contracts
- Customer interaction schemas
- Routing rules
- Context rules
- Environment variables

## Example
A Customer Service Copilot summarizes support cases.

A new prompt is introduced:

```text
Old Prompt
   ↓
Baseline Test Set
   ↓
New Prompt
   ↓
Regression Test
   ↓
Accuracy
Tone
Completeness
Compliance
   ↓
Approve / Reject
```

Useful telemetry includes resolution rate, summarization quality, prediction accuracy, user feedback, throughput, and latency.

## Key Takeaway
**Customer-service AI ALM must protect customer data while maintaining predictable AI behavior across multiple Dynamics 365 applications.**

## Architecture Questions
1. What customer data should be included in Test?
2. Why is Pre-Production useful?
3. Which prompts and agent behaviors need versioning?
4. How should multi-turn conversations be tested?
5. What telemetry should influence the next release?

---

# Module 10 Complete Architecture

```text
                         BUSINESS REQUIREMENTS
                                  |
                                  v
                         AI SOLUTION DESIGN
                                  |
                                  v
                    +-------------+-------------+
                    |             |             |
                    v             v             v
                  DATA          MODELS       AGENTS
                    |             |             |
                    +-------------+-------------+
                                  |
                                  v
                         VERSION + CATALOG
                                  |
                                  v
                              DEV
                                  |
                     Build / Configure / Iterate
                                  |
                                  v
                         QUALITY + SAFETY
                                  |
                                  v
                              TEST
                                  |
               +------------------+------------------+
               |                  |                  |
               v                  v                  v
          AI Evaluation      Integration        Regression
               |                  |                  |
               +------------------+------------------+
                                  |
                                  v
                            PRE-PROD / UAT
                                  |
              +-------------------+-------------------+
              |                   |                   |
              v                   v                   v
          Security            Compliance          Performance
              |                   |                   |
              +-------------------+-------------------+
                                  |
                                  v
                              APPROVAL
                                  |
                                  v
                              PROD
                                  |
                 +----------------+----------------+
                 |                |                |
                 v                v                v
              Monitor          Telemetry         Feedback
                 |                |                |
                 +----------------+----------------+
                                  |
                                  v
                         Drift / Issue Detection
                                  |
                                  v
                           Tune / Retrain
                                  |
                                  v
                            Re-Evaluate
                                  |
                                  v
                         New Version / Release
                                  |
                                  v
                              RETIRE
```

---

# Architecture Decision Model

## Decision 1 — What can change AI behavior?

```text
Data
Knowledge
Prompt
Model
Agent
Connector
Action
Configuration
```

If it can change behavior, include it in ALM.

## Decision 2 — What environments are required?

Minimum:

```text
DEV → TEST → PROD
```

Higher-risk customer-facing workloads:

```text
DEV → TEST → PRE-PROD → PROD
```

## Decision 3 — What must be versioned?

```text
Application
Data
Model
Prompt
Agent
Knowledge
Connector
Action
Configuration
Evaluation Set
```

## Decision 4 — What are the promotion gates?

```text
DEV → TEST
     |
     +-- Data Quality
     +-- Functional Testing
     +-- Safety
     +-- Grounding
     +-- Security

TEST → PRE-PROD
     |
     +-- Regression
     +-- Performance
     +-- Cost
     +-- Compliance

PRE-PROD → PROD
     |
     +-- Business Approval
     +-- Residency
     +-- Monitoring
     +-- Rollback
```

## Decision 5 — How will Production be monitored?

Monitor quality, accuracy, latency, cost, success rate, failure rate, safety events, user feedback, data drift, and model drift.

## Decision 6 — What happens after deployment?

```text
Monitor
   ↓
Detect Problem
   ↓
Investigate
   ↓
Change Data / Prompt / Model / Agent
   ↓
Test
   ↓
Approve
   ↓
Deploy
```

---

# Key Concepts to Remember

1. **AI ALM is broader than traditional ALM**
```text
Code
+ Data
+ Models
+ Prompts
+ Knowledge
+ Agents
+ Connectors
+ Actions
+ Evaluation
+ Telemetry
```

2. **Environment separation matters**
```text
DEV ≠ TEST ≠ PROD
```

3. **Data is an ALM artifact.**

4. **Golden datasets enable regression.**

5. **Version the AI behavior.**

6. **Promotion requires evidence, not only "it works in Dev."**

7. **Production requires monitoring.**

8. **Drift triggers investigation, tuning/retraining, evaluation, and promotion.**

9. **Rollback is part of architecture.**

10. **Business-critical AI needs stronger controls**, especially for financial transactions, purchase approvals, customer data, sensitive information, automated actions, and regulatory workloads.

---

# What You Should Be Able to Design

1. **End-to-end AI ALM**
```text
Dev → Test → Pre-Prod → Prod → Monitor → Retire
```

2. **Data ALM**
```text
Catalog → Prepare → Version → Evaluate → Promote → Monitor
```

3. **Copilot Studio ALM**
```text
Agent + Connector + Action + Dataverse
```

4. **Microsoft Foundry agent lifecycle**
```text
Versioned Agent → Test → Governance → Deploy → Monitor
```

5. **Custom AI model lifecycle**
```text
Data → Model → Evaluation → Model Card → Deploy → Drift → Retrain
```

6. **Dynamics 365 Finance/Supply Chain AI ALM**
```text
ERP Data → AI → Business Rules → Controlled Action
```

7. **Dynamics 365 Customer Experience AI ALM**
```text
Customer Data → Copilot/AI → Business Process → Telemetry
```

8. **Promotion gates and release controls**
```text
Build → Validate → Approve → Deploy → Monitor → Improve
```

9. **Governance controls**
- Security
- DLP
- Data residency
- Sensitivity labeling
- RBAC
- Auditability
- Rollback

10. **Continuous AI lifecycle**
```text
Define
   ↓
Develop
   ↓
Test
   ↓
Approve
   ↓
Deploy
   ↓
Monitor
   ↓
Improve
   ↓
Re-Test
   ↓
Release
```

## Core Architecture Idea

Module 10 is about designing one controlled ALM framework that governs data, models, agents, prompts, connectors, actions, and Dynamics 365 AI capabilities as they move from development to production and through continuous improvement and retirement.
