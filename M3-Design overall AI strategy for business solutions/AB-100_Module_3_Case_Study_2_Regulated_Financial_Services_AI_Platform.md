# Case Study 2 — Regulated Financial Services AI Platform

## Business Background

Fabrikam Financial Services is a multinational financial-services organization with 18,000 employees across several countries.

Business leaders want to introduce AI across:

- Customer operations
- Risk analysis
- Internal policy support
- Compliance operations
- Financial analysis

The organization already uses Microsoft 365 and Microsoft cloud services extensively.

The security and compliance teams have placed strong restrictions on AI.

## Business Goals

The organization wants to:

1. Help employees find internal policy information faster.
2. Improve analysis of large business datasets.
3. Automate selected internal processes.
4. Reduce repetitive knowledge-work tasks.
5. Create reusable AI capabilities across business units.

The company does not want every department to independently create uncontrolled AI solutions.

## Existing AI Requests

### Request 1 — Policy Assistant

Employees want to ask:

> What is the approved process for handling this type of customer request?

The answer must come from approved internal policies.

### Request 2 — Risk Analysis

Risk analysts want to ask:

> Which customer segments show unusual changes in risk indicators?

The system should analyze business data and identify patterns.

It should support the analyst rather than make the final risk decision.

### Request 3 — Internal Document Assistant

Employees want to summarize:

- Reports
- Emails
- Meeting notes
- Business documents

This requirement is primarily Microsoft 365 productivity.

### Request 4 — Specialized Classification

The organization has a high-volume internal process that classifies documents into a small number of business categories.

The existing large language model is more expensive than required for this workload.

The company is investigating whether a customized small language model could be appropriate.

## Data Environment

The company has:

- SharePoint
- OneDrive
- Dataverse
- Dynamics 365
- Enterprise databases
- Azure data services
- Internal APIs

The data is subject to different permissions.

Some data may only be accessed by:

- Risk analysts
- Compliance employees
- Regional teams
- Specific business units

## Security Requirements

The security team requires:

- Identity-based access
- Role-based authorization
- Least-privilege access
- Data classification
- Auditability
- Secure connectors
- Controlled agent actions
- Separation of sensitive workloads

The company does not want an AI agent to bypass existing permissions.

## Regional Requirements

Fabrikam operates in multiple jurisdictions.

The compliance team requires the architecture team to determine:

- Where business data is stored.
- Where AI processing occurs.
- Whether data can cross regional boundaries.
- Which privacy requirements apply.
- Which industry requirements apply.
- What retention and audit requirements apply.

## AI Platform Strategy

```text
                     Enterprise AI Strategy
                              |
          +-------------------+-------------------+
          |                   |                   |
          v                   v                   v
    M365 Copilot       Copilot Studio        Custom AI
          |                   |                   |
          v                   v                   v
 Productivity         Business Agents       Specialized
    Tasks              + Knowledge           Workloads
                              |
                              v
                     Enterprise Data
                              |
                              v
                     Security Controls
                              |
                              v
                     Compliance Controls
```

## Prompt Library

The organization wants a central prompt library for:

- Policy analysis
- Customer communication
- Risk analysis
- Document summarization
- Business reporting

Each prompt should have:

- Purpose
- Intended user
- Role/instruction
- Required context
- Constraints
- Expected output
- Validation guidance

The AI CoE will manage the library.

## AI Center of Excellence

The organization establishes an AI CoE responsible for:

- AI strategy
- Governance
- Architecture standards
- Responsible AI
- Prompt standards
- Reusable assets
- Training
- AI solution reviews
- Adoption measurement

Business teams remain responsible for their business outcomes.

## Custom Model Decision

The classification workload is being evaluated.

```text
Classification Requirement
          |
          v
Can Existing Model Handle It?
       /                YES            NO
      |              |
      v              v
Use Existing      Evaluate
Model             Fine-Tuning
                      |
                      v
               Evaluate SLM
                      |
                      v
             Custom Model Only
             If Justified
```

The team will evaluate:

- Accuracy
- Latency
- Cost
- Data availability
- Domain specialization
- Operational complexity
- Security
- Governance

## User Roles

The AI program includes:

- Executive sponsor
- Business owners
- Solution architects
- AI CoE
- Security team
- Compliance team
- Data owners
- AI engineering team
- Business users

## User Training

### Policy User

Focuses on:

- Finding policy information
- Asking precise questions
- Validating answers
- Understanding source limitations

### Risk Analyst

Focuses on:

- Data-analysis prompts
- Asking analytical questions
- Interpreting trends
- Validating AI results
- Maintaining human decision authority

### General Employee

Focuses on:

- Microsoft 365 Copilot
- Summarization
- Drafting
- Responsible use
- Data protection

## Architect Challenge

Design the enterprise AI strategy.

Consider:

1. Which requirements should use Microsoft 365 Copilot?
2. Which should use Copilot Studio?
3. Where might a customized SLM be useful?
4. How should the organization manage prompt reuse?
5. How should regional regulations influence architecture?
6. What should the AI CoE own?
7. How should data permissions be enforced?
8. When should custom models be considered?
9. How should users be trained by persona?
10. Which workloads should remain human-decision processes?

## Expected Architecture Direction

```text
                    Business AI Strategy
                            |
             +--------------+--------------+
             |              |              |
             v              v              v
       M365 Copilot   Copilot Studio   Specialized AI
             |              |              |
             +--------------+--------------+
                            |
                            v
                    Governed Data Sources
                            |
                            v
                  Identity + Authorization
                            |
                            v
                 Rules + AI Guardrails
                            |
             +--------------+--------------+
             |                             |
             v                             v
        Large Models                 SLM / Custom
             |                             |
             +--------------+--------------+
                            |
                            v
                    Prompt Library
                            |
                            v
                  AI CoE Governance
                            |
                            v
                 Compliance Assessment
                            |
                            v
                    User Adoption
```

---
