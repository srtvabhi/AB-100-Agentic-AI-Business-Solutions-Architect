# Case Study 1 — Global Customer Service AI Transformation

## Business Background

Contoso Industrial Systems is a global manufacturer of industrial equipment. The company sells equipment in North America, Europe, and Asia-Pacific.

Its customer service organization has approximately 2,500 employees. Support teams work with customers through Microsoft Teams, Outlook, Dynamics 365 Customer Service, and SharePoint.

The company wants to improve customer service using AI.

The executive team has identified three business goals:

1. Reduce the time support employees spend searching for customer and product information.
2. Improve the quality and consistency of customer responses.
3. Reduce the time required to prepare a support case for escalation.

The company does not want AI to make uncontrolled decisions on behalf of support employees.

## Current Business Process

```text
Customer Email / Conversation
          |
          v
Identify Customer
          |
          v
Find Product Information
          |
          v
Search Troubleshooting Documentation
          |
          v
Review Customer History
          |
          v
Understand Previous Cases
          |
          v
Prepare Response
          |
          v
Create / Update Support Case
          |
          v
Escalate if Required
```

The process is slow because information is spread across several systems.

## Existing Business Data

### SharePoint

Contains:

- Product manuals
- Troubleshooting guides
- Warranty policies
- Service procedures
- Internal support documentation

### Dynamics 365 Customer Service

Contains:

- Customer records
- Support cases
- Case history
- Case status
- Service information

### Dynamics 365 Sales

Contains:

- Customer account information
- Sales history
- Account ownership
- Product purchases

### ERP System

Contains:

- Orders
- Invoices
- Product information
- Financial information

## Proposed AI Capabilities

The business wants an AI solution that can:

- Summarize customer conversations.
- Retrieve relevant product documentation.
- Find previous support cases.
- Suggest troubleshooting steps.
- Draft a response for an employee to review.
- Create a support case when explicitly requested.
- Help employees understand customer history.
- Provide information from approved company knowledge.

The AI should not:

- Automatically approve refunds.
- Change customer financial information.
- Delete customer records.
- Make final legal or compliance decisions.
- Access information that the employee is not authorized to see.

## Agent Strategy Question

The architecture team is considering:

### Microsoft 365 Copilot

For:

- Email summarization
- Drafting responses
- General productivity
- Document assistance

### Copilot Studio

For:

- Business-specific agents
- Enterprise knowledge
- Business actions
- Connectors and integrations

### More Customized Agent Architecture

For:

- Complex orchestration
- Multiple specialized agents
- Advanced integration
- Custom business logic

The architecture team must determine which requirements can use existing Microsoft 365 capabilities and which require a business-specific agent.

## Proposed Business Workflow

A support employee receives a customer message about an overheating X200 industrial device.

```text
Customer Message
       |
       v
Support Employee
       |
       v
AI Assistance
       |
       +----------------------+
       |                      |
       v                      v
Customer Context        Product Knowledge
       |                      |
       +----------+-----------+
                  |
                  v
          Relevant Information
                  |
                  v
            AI Analysis
                  |
        +---------+---------+
        |                   |
        v                   v
   Draft Response      Suggested Action
        |                   |
        +---------+---------+
                  |
                  v
           Human Review
                  |
                  v
        Create / Update Case
```

## Knowledge Requirements

The company wants the agent to use approved sources.

```text
User Question
      |
      v
Copilot Studio Agent
      |
      v
Knowledge Retrieval
      |
      +---- SharePoint Product Manual
      |
      +---- SharePoint Troubleshooting Guide
      |
      +---- SharePoint Warranty Policy
      |
      +---- Dynamics 365 Customer Information
      |
      v
Relevant Context
      |
      v
AI Response
```

The agent must respect existing user permissions.

## Rules and Constraints

### Allowed

- Read authorized customer information.
- Read authorized support documentation.
- Summarize conversations.
- Suggest troubleshooting steps.
- Draft customer responses.
- Create a support case when explicitly requested.
- Retrieve relevant case history.

### Restricted

- Financial changes require an authorized business process.
- Refund approval requires a human decision.
- Customer deletion is not permitted through the agent.
- Confidential information must remain protected.
- AI-generated information must not be presented as confirmed policy unless supported by an approved source.

## Multi-Agent Consideration

As the solution grows, the company considers:

```text
                    Support Orchestrator
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
   Knowledge Agent   Customer Agent   Case Agent
          |                |                |
          v                v                v
     SharePoint       Dynamics 365      Dynamics 365
```

The architecture team must determine whether the additional orchestration and operational complexity is justified.

## Regional Requirements

Contoso operates in multiple regions.

Customer information may be subject to different:

- Privacy requirements
- Data residency requirements
- Access requirements
- Retention requirements
- Regulatory requirements

The architecture must account for these requirements before production deployment.

## Business Roles

The AI program includes:

- Executive sponsor — owns business transformation and funding.
- Business owner — owns customer-service outcomes and KPIs.
- Solution architect — owns solution architecture and technology decisions.
- Security and compliance team — defines security and regulatory requirements.
- AI Center of Excellence — provides enterprise AI standards and reusable practices.
- Support employees — use the AI capabilities in their daily workflow.

## User Adoption

### Support Employee

Needs training on:

- Asking the agent for customer information
- Finding product information
- Creating useful prompts
- Reviewing generated responses
- Validating AI-generated information

### Support Manager

Needs training on:

- Reviewing AI-assisted processes
- Understanding performance indicators
- Monitoring adoption
- Identifying process improvements

## Architect Challenge

Design the overall AI strategy for Contoso's customer-service transformation.

Consider:

1. Which capabilities should use Microsoft 365 Copilot?
2. Which capabilities require Copilot Studio?
3. Is a custom or multi-agent architecture justified?
4. What knowledge sources should be connected?
5. What rules and constraints should apply?
6. How should regional data requirements influence the design?
7. What roles should own the AI solution?
8. What should the AI Center of Excellence provide?
9. How should user prompt training be designed?
10. How should the solution connect multiple Dynamics 365 applications?

## Expected Architecture Direction

```text
Business Outcome
      |
      v
Customer Service AI Use Cases
      |
      v
Use Existing M365 Copilot Where It Fits
      |
      v
Copilot Studio for Business-Specific Agent Needs
      |
      v
Enterprise Knowledge + Dynamics 365 Data
      |
      v
Rules + Permissions + Guardrails
      |
      v
Human Review for High-Impact Actions
      |
      v
Governance + Compliance
      |
      v
User Training + Adoption
      |
      v
Measured Customer-Service Outcome
```

---
