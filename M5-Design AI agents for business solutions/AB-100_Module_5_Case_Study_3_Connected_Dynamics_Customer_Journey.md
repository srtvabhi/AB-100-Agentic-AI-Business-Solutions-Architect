# AB-100 Module 5 — Case Study 3
# Connected Customer Journey Across Dynamics 365 and Power Platform

## Scenario

Northwind Mobility sells and services commercial vehicles.

The customer journey crosses:

- Dynamics 365 Sales
- Dynamics 365 Customer Service
- Dynamics 365 Field Service
- Dynamics 365 Contact Center
- Power Apps
- Dataverse
- SharePoint
- Copilot Studio

The company wants an AI experience that follows the customer across the lifecycle rather than creating separate disconnected assistants.

## Business Process

```text
Lead
 ↓
Opportunity
 ↓
Vehicle Order
 ↓
Delivery
 ↓
Service Request
 ↓
Field Service
 ↓
Renewal
```

Each stage creates information that may be useful to the next stage.

## Business Requirement

Northwind wants an AI solution that can:

1. Summarize a customer's current relationship.
2. Provide sales representatives with relevant customer context.
3. Help customer-service employees understand previous interactions.
4. Help field-service employees understand the case and service history.
5. Retrieve approved knowledge.
6. Recommend next actions.
7. Execute approved actions through Power Platform.
8. Provide contextual AI experiences inside business applications.

## Dynamics 365 Data

```text
Customer
   |
   +-- Sales Opportunities
   |
   +-- Orders
   |
   +-- Customer Service Cases
   |
   +-- Field Service Work Orders
   |
   +-- Service History
```

## Shared Business Context

The organization defines:

```text
Customer
Vehicle
Order
Case
Work Order
Service History
Priority
Resolution Status
```

These terms must be used consistently across the applications and AI experiences.

## Power Apps Requirement

Northwind has a canvas app used by service coordinators.

The app should use AI to:

- Summarize the customer
- Recommend values during form entry
- Validate information
- Guide the user through a service workflow

## Agent Feed Requirement

The organization wants contextual AI information such as:

- Customer summaries
- Recommendations
- Anomalies
- Contextual insights
- Guided actions

## Generative Pages Requirement

Northwind wants business users to describe a required business page using natural language and generate a Dataverse-based page experience where appropriate.

## Agent Integration

The solution should distinguish:

```text
Information
    |
    v
Knowledge / Context

Action
    |
    v
Agent Flow / Connector / Business Process
```

## NLU Requirement

Northwind has three interaction types.

### Type 1

```text
"Create a service case."
```

Predictable command.

### Type 2

```text
"I need to report a problem with my vehicle."
```

Variable language with a bounded business intent.

### Type 3

```text
"Review this customer's history and explain
what we should consider before renewing the contract."
```

Open-ended reasoning and knowledge use.

The architecture must select the appropriate language-processing approach for each requirement.

## Agent Flow

A service coordinator may ask:

```text
Create a high-priority service case for vehicle VH1001.
```

The agent must:

1. Understand the request.
2. Validate required information.
3. Execute the approved business action.
4. Return the result.

## Prompt Action

The organization defines a reusable customer-summary prompt.

```text
Goal:
Create a concise customer summary.

Context:
Use the customer's sales, service, and field-service information.

Rules:
- Use only supplied business information.
- Do not invent missing facts.
- Highlight open issues.
- Identify relevant recent activity.

Output:
Customer Summary
Open Issues
Recent Activity
Suggested Follow-up
```

## Success Criteria

Northwind defines success using:

### Business Value

Employees spend less time gathering information across applications.

### Operational Efficiency

The same customer context can be used across Sales, Customer Service, and Field Service.

### Quality

AI responses use approved data and consistent business terminology.

### User Experience

Users receive relevant context within their workflow.

### Risk and Compliance

Business actions remain controlled and permissions are preserved.

### Scalability

The architecture supports additional Dynamics 365 workloads without creating isolated AI implementations.

## Architecture Challenge

Design the solution using:

- Dynamics 365
- Contact Center
- Copilot Studio
- Dataverse
- SharePoint
- Power Apps
- Agent flows
- Prompt actions
- Connectors
- Appropriate NLU
- Generative Pages
- Agent Feed
- Responsible AI
- Power Platform Well-Architected principles

## Architecture

```text
                    Customer
                       |
                       v
                Shared Dataverse
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
      Sales      Customer Service  Field Service
        |              |              |
        +--------------+--------------+
                       |
                       v
                Contact Center
                       |
                       v
                Copilot Studio
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
     Knowledge      Prompt         Agent Flow
        |            Action             |
        v              |                v
   SharePoint          |          Business Action
        |              |                |
        +--------------+----------------+
                       |
                       v
                 Power Apps
                       |
              +--------+--------+
              |                 |
              v                 v
       Generative Pages     Agent Feed
              |                 |
              +--------+--------+
                       |
                       v
                User Workflow
                       |
                       v
                Business Outcome
```

## NLU Decision

```text
User Interaction
       |
       v
Is the command predictable?
       |
   Yes |-----> Standard NLU
       |
       No
       v
Are intents/entities bounded?
       |
   Yes |-----> Azure CLU
       |
       No
       v
Open-ended reasoning /
knowledge / multi-turn
       |
       v
Generative AI
```

## Power Platform Well-Architected Check

Review:

```text
Reliability
Security
Operational Excellence
Performance Efficiency
Experience Optimization
```

## Architecture Questions

**Q1. Why use shared Dataverse business context?**

**Expected answer:** To maintain consistent customer, order, case, service, and other business information across Dynamics 365 applications and AI experiences.

**Q2. When should standard NLU be used?**

**Expected answer:** For predictable commands and well-defined language patterns.

**Q3. When is generative AI more appropriate?**

**Expected answer:** For open-ended reasoning, knowledge use, summarization, and multi-turn interactions.

**Q4. What is the role of an agent flow?**

**Expected answer:** The agent provides intelligence while the agent flow automates execution of a business process or action.

**Q5. What is the purpose of a prompt action?**

**Expected answer:** To provide a reusable, structured instruction for a recurring AI task.

**Q6. Why use Power Platform Well-Architected principles?**

**Expected answer:** To evaluate reliability, security, operational excellence, performance efficiency, and experience optimization of the intelligent application.

**Q7. What makes the solution scalable?**

**Expected answer:** Shared business context, reusable prompts and actions, governed knowledge, controlled integrations, consistent architecture patterns, and measurable success criteria.

## Key Decision

The solution treats the customer journey as one connected business process and uses AI capabilities inside the appropriate Dynamics 365 and Power Platform experiences.

---

# Case Study 3 Architecture Summary

```text
Customer Journey
       |
       v
Shared Business Context
       |
       v
Dynamics 365 Applications
       |
       v
AI Agent Layer
       |
 +-----+-----+---------+
 |           |         |
Knowledge  Prompts   Actions
 |           |         |
 +-----------+---------+
             |
             v
      Power Platform
             |
       +-----+-----+
       |           |
       v           v
  Power Apps   Agent Feed /
               Generative Pages
       |           |
       +-----+-----+
             |
             v
      User Workflow
             |
             v
      Business Outcome
```
