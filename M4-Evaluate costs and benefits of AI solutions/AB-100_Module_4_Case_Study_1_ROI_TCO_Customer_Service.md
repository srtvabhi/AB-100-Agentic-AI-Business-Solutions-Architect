# Case Study 1 — AI Customer Service Assistant: ROI and TCO

## Company

**Contoso Industrial Systems** is a global manufacturer with 2,500 customer-service employees.

The company uses:

- Microsoft 365
- Dynamics 365 Customer Service
- SharePoint
- Teams
- An ERP system
- A centralized support knowledge base

Customer-service representatives handle approximately **120,000 support cases per month**.

## Business Problem

Representatives spend significant time:

- Searching product documentation
- Reviewing previous cases
- Summarizing customer conversations
- Preparing troubleshooting responses
- Preparing escalation information

The business wants an AI-powered customer-service assistant.

The proposed solution should:

1. Retrieve approved product information.
2. Summarize customer conversations.
3. Find relevant historical cases.
4. Suggest troubleshooting steps.
5. Draft customer responses.
6. Help prepare escalations.

The AI must not:

- Approve refunds.
- Change financial records.
- Delete customer information.
- Make final legal or compliance decisions.

---

## Current Baseline

The current process produces the following baseline:

| Metric | Current State |
|---|---:|
| Monthly cases | 120,000 |
| Average manual handling time | 24 minutes/case |
| Average search/research time | 8 minutes/case |
| Customer-service employees | 2,500 |
| Escalation preparation | Manual |

The business expects AI to reduce average handling time from **24 minutes to 17 minutes**.

---

## Proposed AI Solution

The architecture is:

```text
                 CUSTOMER CASE
                       │
                       ▼
             Dynamics 365 Customer Service
                       │
                       ▼
              AI CUSTOMER ASSISTANT
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      SharePoint    Historical    Product
      Knowledge       Cases       Information
          │            │            │
          └────────────┼────────────┘
                       ▼
                AI-GENERATED HELP
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Summary    Troubleshooting  Draft Reply
                       │
                       ▼
                HUMAN REVIEW
                       │
                       ▼
                  CUSTOMER
```

---

## ROI Analysis

Potential time saving:

```text
24 minutes - 17 minutes
= 7 minutes saved per case
```

Monthly time saving:

```text
7 × 120,000
= 840,000 minutes/month
```

That is:

```text
840,000 / 60
= 14,000 hours/month
```

The business must translate those hours into an appropriate financial value using its own labor-cost assumptions.

---

## TCO Considerations

The architect identifies the following lifecycle costs:

### Development

- Agent configuration
- Integration
- Prompt engineering
- Testing
- Security design
- Data preparation

### Deployment

- Microsoft licensing
- AI/model usage
- Environment configuration
- Identity and access configuration

### Operations

- Monitoring
- Evaluation
- Knowledge maintenance
- Support
- Model/prompt updates

### Change Management

- User training
- Process changes
- Adoption activities

### Retirement

- Migration
- Decommissioning
- Data retention requirements

---

## Architecture Decision

The business should not approve the solution only because the AI demonstrates good responses.

The architecture decision should compare:

```text
Expected Business Benefit
          │
          ▼
       ROI Value
          │
          ▼
        versus
          │
          ▼
        TCO
          │
          ▼
   Business Decision
```

The solution should also establish measurable KPIs such as:

- Average handling time
- Search time
- Cases handled per employee
- Escalation preparation time
- Customer satisfaction
- Response quality

---

## Key Questions

1. What is the baseline before AI deployment?
2. Which benefits are measurable?
3. Which benefits translate into financial value?
4. What costs exist across the complete lifecycle?
5. How will actual ROI be measured after deployment?
6. What assumptions should be validated before approving the investment?

## Module 4 Topics

- ROI criteria
- Total Cost of Ownership
- ROI analysis
- Business outcomes
- Productivity improvement
- Cost savings
- Measurement and validation
