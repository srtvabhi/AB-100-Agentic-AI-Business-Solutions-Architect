# AB-100 Module 7 — Case Study 1
# Finance and Supply Chain AI Orchestration

## Scenario

Contoso Manufacturing operates a global procurement and supply-chain organization.

The company uses:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Microsoft 365
- SharePoint
- Power Automate
- Copilot capabilities in Dynamics 365

Procurement users currently spend significant time moving between purchase orders, supplier records, inventory information, policies, and approval workflows.

Contoso wants to introduce AI assistance without replacing the existing Finance and Supply Chain business processes.

## Business Requirements

The solution must:

1. Help procurement users understand purchase-order status.
2. Summarize supplier and purchase-order information.
3. Retrieve approved procurement procedures.
4. Explain supply-chain exceptions using available business context.
5. Provide suggestions for next steps.
6. Trigger approved workflow actions when required.
7. Preserve existing security roles and permissions.
8. Keep business actions auditable.
9. Avoid allowing the AI to make unrestricted purchasing decisions.

## Available Systems

| System | Purpose | Integration |
|---|---|---|
| Dynamics 365 Finance | Purchase orders, vendors, financial data | Business application |
| Dynamics 365 Supply Chain | Inventory, supply, procurement context | Business application |
| SharePoint | Procurement procedures and policies | Knowledge |
| Power Automate | Notifications and approved workflows | Action |
| Microsoft 365 | Collaboration and user experience | Productivity |

## Business Context

A procurement user may ask:

```text
Why is PO-10482 delayed?

What supplier information is available?

What procurement procedure applies?

What should I do next?
```

The answer may require information from more than one business system.

## Architecture Challenge

The architect must determine:

- when to use embedded Dynamics 365 AI;
- when an external agent experience is appropriate;
- where enterprise knowledge should be maintained;
- how Power Automate should be used;
- how actions should be controlled;
- how existing Finance and Supply Chain security is preserved.

## Architecture

```text
                         Procurement User
                                |
                                v
                  Dynamics 365 / Microsoft 365
                                |
                                v
                       AI / Copilot Experience
                                |
              +-----------------+------------------+
              |                 |                  |
              v                 v                  v
        Dynamics 365        SharePoint        Power Automate
        Finance + SCM       Knowledge          Workflows
              |                 |                  |
              +-----------------+------------------+
                                |
                                v
                         Grounded Context
                                |
                                v
                         AI Recommendation
                                |
                         +------+------+
                         |             |
                         v             v
                    Read Result     Approved Action
                         |             |
                         |             v
                         |       Business Workflow
                         |             |
                         +------+------+
                                |
                                v
                           Audit / Review
```

## Example

A procurement manager asks why a purchase order is delayed.

The agent can:

1. Read the purchase order.
2. Retrieve supplier information.
3. Check workflow status.
4. Review supply-chain context.
5. Retrieve the relevant procurement procedure.
6. Provide a grounded explanation.
7. Suggest a next step.
8. Invoke an approved workflow only when permitted.

## Architecture Questions

### Question 1

When should AI be embedded directly in Dynamics 365?

**Expected Answer:** Use embedded AI when the intelligence belongs directly inside an existing Finance or Supply Chain workflow and the user is already working with the relevant business context.

### Question 2

When would an external agent be more appropriate?

**Expected Answer:** Use an external agent when the scenario crosses multiple applications or requires broader orchestration across Dynamics 365, Microsoft 365, and Power Platform.

### Question 3

Where should procurement procedures be maintained?

**Expected Answer:** Use a governed knowledge source such as SharePoint for approved procurement procedures and policies.

### Question 4

Should the AI directly change a purchase order without controls?

**Expected Answer:** No. Business actions should use approved workflows, permissions, validation, and appropriate human review.

### Question 5

What is the system of record?

**Expected Answer:** Dynamics 365 Finance and Supply Chain remain the authoritative business systems for the relevant financial and supply-chain records.

## Key Architectural Decisions

| Requirement | Architectural Decision |
|---|---|
| Purchase-order data | Dynamics 365 Finance |
| Supply-chain context | Dynamics 365 Supply Chain |
| Procedures | SharePoint |
| Workflow actions | Power Automate |
| User experience | Dynamics 365 / Microsoft 365 |
| Business changes | Controlled workflow |
| Security | Existing business-system permissions |
| Audit | Business workflow and platform telemetry |

## Final Architecture

```text
User
 |
 v
AI / Copilot Experience
 |
 +--> Dynamics 365 Finance
 |
 +--> Dynamics 365 Supply Chain
 |
 +--> SharePoint Knowledge
 |
 +--> Power Automate
 |
 v
Grounded Recommendation
 |
 v
Human / Approved Workflow
 |
 v
Business Outcome
```
