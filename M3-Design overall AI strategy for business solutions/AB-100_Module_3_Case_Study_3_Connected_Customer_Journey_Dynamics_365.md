# Case Study 3 — Connected Customer Journey Across Dynamics 365

## Business Background

Northwind Mobility is a global company that sells and services commercial vehicles.

Its customer journey crosses multiple business functions.

The company uses:

- Dynamics 365 Sales
- Dynamics 365 Customer Service
- Dynamics 365 Field Service
- Dynamics 365 Finance
- Microsoft 365
- SharePoint

The company wants to introduce AI into the customer lifecycle.

## Current Customer Journey

```text
Lead
 |
 v
Sales Opportunity
 |
 v
Vehicle Purchase
 |
 v
Invoice / Finance
 |
 v
Customer Service
 |
 v
Service Request
 |
 v
Field Service
 |
 v
Service Completion
```

Information is distributed across applications.

Employees often need to move between systems to understand the complete customer context.

## Business Goals

Northwind wants to:

1. Give employees a consistent customer view.
2. Reduce time spent searching across applications.
3. Improve service response.
4. Improve coordination between Sales, Customer Service, Finance, and Field Service.
5. Help employees prepare customer interactions.
6. Provide AI-assisted recommendations without removing human accountability.

## AI Use Cases

### Sales

Sales employees want AI to:

- Summarize customer history.
- Prepare meeting information.
- Identify relevant previous interactions.
- Draft follow-up communications.

### Customer Service

Support employees want AI to:

- Summarize customer issues.
- Find previous service cases.
- Retrieve troubleshooting information.
- Draft responses.
- Create or update service cases.

### Finance

Finance employees want AI assistance with:

- Customer account information.
- Invoice-related context.
- Financial process information.

Financial actions must remain controlled by approved business processes.

### Field Service

Field technicians want AI to:

- Understand customer service history.
- Review previous issues.
- Find relevant technical documentation.
- Prepare for service visits.

## Cross-Application Architecture

```text
                         Customer
                            |
                            v
                  Shared Business Context
                            |
       +--------------------+--------------------+
       |                    |                    |
       v                    v                    v
Dynamics 365 Sales   Customer Service       Finance
       |                    |                    |
       +--------------------+--------------------+
                            |
                            v
                     Field Service
                            |
                            v
                     AI Assistance
```

The architecture must ensure that each user only receives information they are authorized to access.

## Agent Strategy

The architecture team considers:

### Microsoft 365 Copilot

For:

- Email drafting
- Document summarization
- Meeting preparation

### Copilot Studio

For:

- Customer-service assistance
- Knowledge retrieval
- Business actions
- Workflow support

### Multi-Agent Architecture

```text
                    Customer Orchestrator
                           |
        +------------------+------------------+
        |                  |                  |
        v                  v                  v
    Sales Agent      Service Agent      Field Agent
        |                  |                  |
        v                  v                  v
     Sales            Customer Service    Field Service
```

The architecture team must determine whether separate agents provide enough value to justify the additional orchestration and operational complexity.

## Knowledge Architecture

```text
                   AI Agent
                      |
                      v
               Knowledge Search
                      |
        +-------------+-------------+
        |             |             |
        v             v             v
   SharePoint     Dataverse     Business Data
        |             |             |
        +-------------+-------------+
                      |
                      v
               Relevant Context
                      |
                      v
                  AI Response
```

Knowledge sources include:

- Product documentation
- Service procedures
- Customer-service policies
- Warranty information
- Field-service documentation

## Rules and Constraints

### AI Can

- Retrieve authorized information.
- Summarize customer history.
- Draft responses.
- Recommend possible next steps.
- Create approved records when explicitly requested.
- Retrieve technical documentation.

### AI Cannot Independently

- Approve financial adjustments.
- Change customer credit limits.
- Delete customer records.
- Make final compliance decisions.
- Expose information outside the user's permissions.

## Multi-Agent Decision

The architecture team identifies possible reasons for specialized agents:

### Different Business Domains

Sales, Service, and Field Service have different responsibilities.

### Different Tools

Each domain uses different business systems.

### Different Ownership

Different teams own the processes.

### Different Permissions

Some information may only be accessible to specific roles.

However, a multi-agent design also introduces:

- More orchestration
- More testing
- More monitoring
- More security configuration
- More operational complexity

The architect must determine whether the business requirement actually requires the additional complexity.

## Prompt Library

Northwind wants reusable prompts for common business activities.

### Sales Prompt

```text
Summarize the customer's recent interactions.

Identify:
- Current opportunity
- Recent issues
- Important customer requests
- Recommended follow-up areas

Use only the supplied business information.
```

### Service Prompt

```text
Summarize the customer's current service issue.

Identify:
- Product
- Reported problem
- Previous related cases
- Relevant approved troubleshooting information

Do not invent troubleshooting steps.
```

### Field Service Prompt

```text
Prepare a service-visit summary.

Include:
- Customer
- Equipment
- Previous service history
- Current reported issue
- Relevant technical documentation

Separate known information from suggestions.
```

## User Adoption

### Sales Users

Learn:

- Customer-summary prompts
- Meeting preparation
- Follow-up drafting
- Validation of AI-generated information

### Customer Service Users

Learn:

- Knowledge retrieval
- Case summarization
- Response drafting
- Approved actions

### Field Technicians

Learn:

- Technical knowledge retrieval
- Service-history prompts
- Safety-related validation
- Responsible use of AI recommendations

### Managers

Learn:

- AI adoption measurement
- Review of business outcomes
- Responsible AI expectations
- Escalation procedures

## AI Center of Excellence

The AI CoE provides:

- Architecture standards
- Agent design standards
- Prompt standards
- Responsible AI guidance
- Security and governance patterns
- Reusable components
- Training materials
- Adoption measurement

Business teams continue to own their specific processes and outcomes.

## Regional Considerations

Northwind operates in several regions.

The architecture team must evaluate:

- Customer-data location
- Processing location
- Data residency
- Cross-border transfer
- Privacy requirements
- Retention
- Industry requirements

The solution cannot assume that one architecture automatically satisfies every region.

## Architect Challenge

Design the AI architecture for Northwind's connected customer journey.

Consider:

1. Which use cases are suitable for Microsoft 365 Copilot?
2. Which require Copilot Studio?
3. Should the company use one agent or multiple specialized agents?
4. What knowledge sources should be connected?
5. How should permissions be enforced?
6. Which actions require human approval?
7. How should multiple Dynamics 365 applications share business context?
8. Where should prompt libraries be used?
9. What should the AI CoE standardize?
10. How should regional requirements affect the design?
11. How should user training differ by persona?

## Expected Architecture Direction

```text
                         Business Outcome
                                |
                                v
                     Connected Customer Journey
                                |
                                v
                         AI Use Cases
                                |
              +-----------------+-----------------+
              |                 |                 |
              v                 v                 v
        M365 Copilot      Copilot Studio    Multi-Agent
              |                 |                 |
              +-----------------+-----------------+
                                |
                                v
                     Shared Business Context
                                |
             +------------------+------------------+
             |                  |                  |
             v                  v                  v
           Sales             Service            Finance
             |                  |                  |
             +------------------+------------------+
                                |
                                v
                         Field Service
                                |
                                v
                     Knowledge + Enterprise Data
                                |
                                v
                       Rules + Permissions
                                |
                                v
                    Security + Compliance
                                |
                                v
                           AI CoE
                                |
                                v
                       User Training
                                |
                                v
                       Business Adoption
```

---
