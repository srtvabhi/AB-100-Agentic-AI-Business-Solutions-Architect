# AB-100 Module 7 — Case Study 3
# Power Platform AI and Finance & Operations Interoperability

## Scenario

Northwind Distribution operates a large finance and procurement organization.

The company uses:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Power Apps
- Power Automate
- Copilot Studio
- SharePoint
- Microsoft 365

The company wants an AI-assisted supplier compliance process.

The process requires information from Finance and Operations, approved supplier documents, and automated workflow.

## Business Requirements

The solution must:

1. Help procurement users review supplier compliance.
2. Retrieve vendor information from Finance and Operations.
3. Retrieve approved supplier certificates from SharePoint.
4. Identify missing or expired documentation.
5. Extract information from supplier documents when required.
6. Create a follow-up task automatically.
7. Notify the procurement owner.
8. Avoid automatically approving or rejecting suppliers.
9. Preserve access permissions.
10. Maintain an auditable workflow.

## Existing Data

### Dynamics 365 Finance and Supply Chain

```text
Vendor
Vendor Status
Payment Terms
Purchase History
Procurement Information
```

### SharePoint

```text
Supplier Certificates
Compliance Documents
Supplier Procedures
Procurement Policies
```

### Power Platform

```text
Power Apps
Power Automate
AI Builder
Copilot Studio
```

## Architecture Challenge

The architect must decide:

- which capability should perform document extraction;
- where supplier knowledge should live;
- how an agent should access F&O information;
- how Power Automate should orchestrate the process;
- when AI Builder is appropriate;
- how to prevent autonomous approval decisions.

## Capability Selection

| Requirement | Capability |
|---|---|
| Supplier conversation | Copilot Studio |
| Supplier business data | Dynamics 365 F&O |
| Document extraction | AI Builder |
| Workflow | Power Automate |
| Supplier knowledge | SharePoint |
| User interface | Power Apps |
| Notifications | Power Automate / Microsoft 365 |

## Architecture

```text
                    Procurement User
                           |
                           v
                       Power App
                           |
                           v
                    Copilot Studio
                           |
             +-------------+-------------+
             |             |             |
             v             v             v
        Dynamics 365   SharePoint      AI Builder
        Finance/SCM    Certificates    Document Data
             |             |             |
             +-------------+-------------+
                           |
                           v
                    Agent Reasoning
                           |
                           v
                  Compliance Assessment
                           |
                           v
                   Power Automate
                           |
              +------------+------------+
              |                         |
              v                         v
        Create Follow-up            Notify Owner
              |                         |
              +------------+------------+
                           |
                           v
                     Human Review
                           |
                           v
                   Business Decision
```

## Example

A procurement user opens a supplier record and asks:

```text
Is the supplier's compliance documentation current?
```

The solution performs:

1. Retrieve supplier identity and status from F&O.
2. Locate the supplier certificate in SharePoint.
3. Use AI Builder when structured information must be extracted from a document.
4. Compare the document information with business requirements.
5. Identify missing or expired information.
6. Create a follow-up task through Power Automate.
7. Notify the procurement owner.
8. Leave the final supplier decision to the authorized business process.

## Document Processing

A supplier submits a certificate.

```text
Supplier Document
       |
       v
   AI Builder
       |
       +--> Supplier Name
       +--> Certificate Type
       +--> Issue Date
       +--> Expiration Date
       |
       v
Structured Result
       |
       v
Validation
       |
       v
Power Automate
```

AI Builder is used for the focused document extraction requirement rather than creating a general-purpose agent for document parsing.

## F&O Interoperability

The agent can retrieve information from Finance and Operations through approved integration capabilities.

```text
Agent
  |
  v
F&O Business Context
  |
  +--> Vendor
  +--> Status
  +--> Payment Terms
  +--> Procurement Information
```

If information or an action is outside F&O, the solution uses the appropriate knowledge source, connector, plugin, or workflow rather than duplicating the business system.

## Governance

The architecture includes:

- F&O security roles
- Microsoft 365 identity
- SharePoint permissions
- Power Platform DLP
- environment governance
- audit logging
- human review
- controlled workflow actions

## Architecture Questions

### Question 1

Why use AI Builder for the supplier certificate?

**Expected Answer:** AI Builder is appropriate because the requirement is focused document extraction. A full conversational agent is not required just to extract structured fields.

### Question 2

Why use Copilot Studio?

**Expected Answer:** Copilot Studio provides the conversational agent experience and can orchestrate knowledge, business data, and actions.

### Question 3

Why use Power Automate?

**Expected Answer:** Power Automate provides the controlled workflow layer for creating tasks, sending notifications, and coordinating business actions.

### Question 4

Should the agent approve the supplier automatically?

**Expected Answer:** No. The requirement explicitly keeps the final supplier decision within the authorized business process and human governance.

### Question 5

Where should supplier certificates be maintained?

**Expected Answer:** Approved supplier certificates can be maintained in a governed SharePoint environment with appropriate permissions and lifecycle management.

### Question 6

What should happen when the certificate is expired?

**Expected Answer:** The solution should identify the exception, create the appropriate follow-up task, notify the responsible owner, and allow the authorized business process to determine the final outcome.

## Key Architectural Decisions

| Requirement | Architectural Decision |
|---|---|
| User experience | Power Apps + Copilot Studio |
| F&O business data | Dynamics 365 Finance / Supply Chain |
| Supplier documents | SharePoint |
| Document extraction | AI Builder |
| Workflow | Power Automate |
| Notifications | Power Automate / Microsoft 365 |
| Final decision | Authorized business process |
| Security | Existing identity and permissions |
| Governance | DLP + audit + human review |

## Final Architecture

```text
User
 |
 v
Power Apps
 |
 v
Copilot Studio
 |
 +--> Dynamics 365 F&O
 |
 +--> SharePoint
 |
 +--> AI Builder
 |
 v
Grounded Compliance Context
 |
 v
Power Automate
 |
 +--> Task
 +--> Notification
 |
 v
Human / Authorized Business Process
 |
 v
Supplier Compliance Outcome
```
