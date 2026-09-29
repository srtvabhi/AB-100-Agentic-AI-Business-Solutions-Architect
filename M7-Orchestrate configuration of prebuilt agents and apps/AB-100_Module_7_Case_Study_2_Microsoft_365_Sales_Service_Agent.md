# AB-100 Module 7 — Case Study 2
# Microsoft 365 Agent for Sales and Customer Service

## Scenario

Fabrikam Technology sells enterprise software and provides 24/7 customer support.

The organization uses:

- Microsoft 365
- Dynamics 365 Sales
- Dynamics 365 Customer Service
- SharePoint
- Microsoft Teams
- Power Automate

Sales representatives and service representatives spend time searching email, meetings, CRM records, cases, and knowledge articles.

Fabrikam wants a Microsoft 365-centered AI experience that can support both sales and service users while preserving CRM security.

## Business Requirements

The solution must:

1. Summarize customer activity for sellers.
2. Retrieve account, contact, and opportunity context.
3. Summarize customer cases for service representatives.
4. Retrieve approved product and troubleshooting information.
5. Draft responses using available business context.
6. Allow users to review AI-generated content before customer communication.
7. Create approved CRM updates through governed actions.
8. Support Teams-based collaboration.
9. Preserve existing CRM and Microsoft 365 permissions.
10. Provide fallback behavior when information is unavailable.

## Data Environment

```text
Microsoft 365
|
+-- Email
+-- Meetings
+-- Teams
+-- Documents
|
Dynamics 365 Sales
|
+-- Accounts
+-- Contacts
+-- Opportunities
+-- Activities
|
Dynamics 365 Customer Service
|
+-- Cases
+-- Customer History
+-- Service Activities
|
SharePoint
|
+-- Product Documentation
+-- Troubleshooting
+-- Service Policies
```

## Business Scenarios

### Sales Scenario

A seller asks:

```text
Summarize the latest activity for Contoso
and identify the next action for opportunity OP-2045.
```

The agent needs Microsoft 365 and CRM context.

### Service Scenario

A service representative asks:

```text
Summarize case CS-7821 and
suggest a response based on approved troubleshooting guidance.
```

The agent needs case context plus governed knowledge.

## Architecture Challenge

The architect must design:

- a Microsoft 365 agent experience;
- CRM grounding;
- SharePoint knowledge;
- Teams collaboration;
- Power Automate actions;
- human review;
- security and DLP controls.

## Architecture

```text
                         User
                          |
            +-------------+-------------+
            |                           |
            v                           v
       Microsoft 365                Teams
          Copilot                    Agent
            |                           |
            +-------------+-------------+
                          |
                          v
                  Microsoft 365 Agent
                          |
          +---------------+----------------+
          |               |                |
          v               v                v
   Dynamics 365       SharePoint      Power Automate
      Sales /          Knowledge         Actions
     Service               |                |
          |                |                |
          +----------------+----------------+
                           |
                           v
                    Grounded Context
                           |
                           v
                    Generated Output
                           |
                           v
                    Human Review
                           |
                           v
                  Approved CRM Action
```

## Example

A seller receives an inbound customer email.

The solution can:

1. Summarize the email.
2. Find the related CRM opportunity.
3. Retrieve account and contact context.
4. Draft response or proposal content.
5. Let the seller review it.
6. Update the CRM after approval.

## Architecture Questions

### Question 1

Why should CRM data remain in Dynamics 365?

**Expected Answer:** Dynamics 365 remains the system of record for accounts, opportunities, cases, and other CRM information. The agent should retrieve the information rather than create an uncontrolled duplicate data store.

### Question 2

Why use SharePoint for product and troubleshooting knowledge?

**Expected Answer:** SharePoint can act as a governed enterprise knowledge source for approved documents and procedures, provided the correct permissions and content lifecycle are maintained.

### Question 3

Should the agent automatically send every generated customer response?

**Expected Answer:** Not under this scenario. Customer-facing communication should include human review where required by the business process.

### Question 4

Why use Power Automate?

**Expected Answer:** Power Automate provides a controlled workflow and action layer for approved operations such as CRM updates, notifications, and escalations.

### Question 5

What happens if the agent cannot find the required knowledge?

**Expected Answer:** The solution should use defined fallback behavior rather than inventing an unsupported answer. The user can be directed to the appropriate human or business process.

## Key Architectural Decisions

| Requirement | Architectural Decision |
|---|---|
| Seller experience | Microsoft 365 Copilot / Agent |
| CRM data | Dynamics 365 Sales |
| Service data | Dynamics 365 Customer Service |
| Knowledge | SharePoint |
| Collaboration | Teams |
| Workflow actions | Power Automate |
| Customer communication | Human review where required |
| Security | Existing Microsoft 365 and CRM permissions |
| Governance | DLP, labels, audit, telemetry |

## Final Architecture

```text
Microsoft 365 / Teams
        |
        v
Microsoft 365 Agent
        |
  +-----+-----+---------+
  |           |         |
  v           v         v
Sales       Service   SharePoint
CRM         CRM       Knowledge
  |           |         |
  +-----------+---------+
              |
              v
        Grounded Output
              |
              v
         Human Review
              |
              v
        Power Automate
              |
              v
        Business System
```
