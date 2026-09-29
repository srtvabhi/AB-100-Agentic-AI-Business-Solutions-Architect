# Module 11 Case Study 1: Secure and Governed Customer Service Agent

## Scenario

Contoso Industrial Systems wants to deploy an AI customer-service agent for employees.

The agent can search customer information, summarize cases, retrieve product information, and create service actions.

Because the agent can access sensitive customer data and perform business actions, the organization needs a security and governance architecture before production.

## Requirements

- Authenticate users through Microsoft Entra ID.
- Apply least-privilege access.
- Restrict customer data based on user permissions.
- Control which knowledge sources the agent can use.
- Limit available tools and actions.
- Require approval for high-impact actions.
- Classify the agent according to business risk.
- Define an accountable business owner.
- Monitor agent activity.
- Maintain audit information.
- Prevent direct production changes without review.

## Systems and Data

- Microsoft Entra ID
- Customer service application
- Customer records
- Product knowledge
- Copilot Studio agent
- Connectors and actions
- Business approval process
- Monitoring and audit capabilities

## Architecture Challenge

The initial design gives the agent broad access to customer records and several business APIs.

The architecture team must redesign the solution so that:

- Users only see authorized information.
- The agent can only perform approved actions.
- Sensitive actions have stronger controls.
- Governance requirements increase with risk.
- Production activity can be monitored and audited.

## Architecture

```text
                    Microsoft Entra ID
                           |
                           v
                    User Identity
                           |
                           v
                  Authorization Layer
                           |
                           v
                    AI Customer Agent
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
      Knowledge        Controlled Tools   Model
          |                |                |
          v                v                v
   Customer/Product     Approved APIs    Guardrails
       Data                 |
          |                 v
          |          Business Systems
          |                 |
          +--------+--------+
                   |
                   v
            High-Impact Action?
                   |
             +-----+-----+
             |           |
            No          Yes
             |           |
             v           v
          Execute    Human Approval
             |           |
             +-----+-----+
                   |
                   v
              Audit + Monitor
```

## Example

A support employee asks:

> "Show me the full financial details for customer C1007."

The agent first evaluates the user's permissions.

If the employee is not authorized to view financial information, the agent must not retrieve or expose that data.

The employee then asks:

> "Cancel the customer's active contract."

Because contract cancellation is a high-impact action, the architecture requires appropriate authorization and human approval before execution.

## Architecture Questions

1. What identity should be used to determine the employee's permissions?
2. Why should the agent use least privilege?
3. Which agent actions should require stronger approval?
4. How should the organization classify this agent?
5. What information should be recorded for audit purposes?

## Expected Answers

1. Use the user's authenticated identity and appropriate authorization controls.
2. Least privilege reduces the amount of data and business functionality available if the agent or account is misused.
3. Financial, destructive, irreversible, compliance-sensitive, or customer-impacting actions should receive stronger controls.
4. Classify the agent using factors such as data sensitivity, business impact, autonomy, financial impact, and regulatory impact.
5. Record important identities, changes, actions, versions, timestamps, and relevant activity needed for investigation and governance.

## Key Architectural Decisions

- Use Microsoft Entra-based identity and authorization.
- Apply least privilege to data and tools.
- Separate read operations from high-impact actions.
- Require stronger approval for sensitive actions.
- Assign an accountable agent owner.
- Monitor agent activity.
- Maintain auditability.
