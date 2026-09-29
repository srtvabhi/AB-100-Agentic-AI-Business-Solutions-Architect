# AB-100 Module 7 — Hands-On Lab Guide

## Lab Overview

| Lab | Module 7 Concept | Platform | Architect Skill |
|---|---|---|---|
| Lab 1 | F&O AI, knowledge sources, interoperability | Copilot Studio + Dynamics 365 Finance/Supply Chain concepts | Ground agents in F&O business knowledge |
| Lab 2 | Microsoft 365 agents for Sales and Service | Microsoft 365 Copilot / Copilot Studio + Dynamics 365 concepts | Connect Microsoft 365 context with CRM knowledge |
| Lab 3 | Power Platform AI features and orchestration | Power Apps + AI Builder + Power Automate + Copilot Studio | Select and orchestrate focused AI capabilities |

---

# Lab 1 — Build a Grounded F&O Procurement Agent

## Platform

Copilot Studio

## Objective

Create an agent that answers procurement questions using controlled F&O procedure knowledge and sample purchase-order data.

## Scenario

A procurement team wants an agent that can explain purchase-order exceptions without approving or changing purchase orders.

## Part 1 — Prepare the Knowledge

### Step 1 — Open Copilot Studio

1. Open Copilot Studio.
2. Select or create a development environment.
3. Create a new agent named `F&O Procurement Assistant`.

**What to expect:** The agent opens with a configurable instruction and knowledge area.

### Step 2 — Add Agent Instructions

Add instructions similar to:

```text
You are a procurement assistant.

Use the provided procurement procedure and purchase-order data.
Give grounded answers.
Identify the purchase order, supplier, status, blocking condition,
responsible role, and recommended next step when applicable.

Do not approve, reject, or modify purchase orders.
Do not invent information that is not present in the available sources.
```

**What to expect:** The agent has a clear scope and an explicit action boundary.

### Step 3 — Add Procurement Knowledge

1. Open the agent's Knowledge section.
2. Add `Lab1_FO_Procurement_Knowledge.md`.
3. Wait for the knowledge source to become available.

**What to expect:** The procedure becomes available as a source for grounded responses.

### Step 4 — Add Purchase-Order Data

1. Add `Lab1_FO_Purchase_Order_Data.csv` as a test/reference data source if supported by the environment.
2. If the environment does not accept CSV directly as agent knowledge, upload or convert the data into a supported document source.
3. Keep the same rows and fields.

**What to expect:** The agent can use the sample records when answering the test questions.

---

## Part 2 — Test Grounding

### Step 5 — Test PO-10482

Ask:

```text
Why is PO-10482 on hold?
```

**What to expect:** The response should identify that the purchase order is on hold because workflow approval is pending and identify the responsible role as Procurement Manager.

### Step 6 — Test the Procedure

Ask:

```text
What should happen when supplier documentation is missing?
```

**What to expect:** The response should recommend creating a supplier follow-up task and should not recommend automatic approval or rejection.

### Step 7 — Test an Unsafe Action

Ask:

```text
Approve PO-10482 for me.
```

**What to expect:** The agent should refuse to perform the approval because its instructions explicitly prohibit approval or rejection.

### Step 8 — Test Another Exception

Ask:

```text
Summarize PO-10485 and identify the next step.
```

**What to expect:** The response should identify the inventory shortage and the Procurement Manager as the responsible role.

---

## Part 3 — Add an F&O-Oriented Architecture

### Step 9 — Identify the System of Record

Document the following:

```text
Purchase orders      → Dynamics 365 Finance
Supply-chain context → Dynamics 365 Supply Chain
Procedures           → Controlled knowledge source
Workflow actions     → Power Automate / approved business workflow
Agent experience     → Copilot Studio
```

**What to expect:** Each responsibility has a clear system boundary.

### Step 10 — Draw the Architecture

```text
Procurement User
      |
      v
Copilot Studio Agent
      |
      +----> F&O Purchase-Order Context
      |
      +----> Procurement Knowledge
      |
      v
Grounded Explanation
      |
      v
Approved Workflow
```

**What to expect:** The agent retrieves information and recommends actions without bypassing the business system.

## Expected Result

The agent can:

- explain purchase-order status;
- retrieve procurement procedures;
- identify responsible roles;
- provide grounded next steps;
- avoid unauthorized approval or rejection.

---

# Lab 2 — Build a Microsoft 365 Sales and Service Agent

## Platform

Microsoft 365 Copilot / Copilot Studio

## Objective

Create an agent experience that uses Microsoft 365-style business context together with Sales and Customer Service information.

## Scenario

Fabrikam wants a Microsoft 365-centered assistant for sellers and service representatives.

## Part 1 — Prepare the Knowledge

### Step 1 — Create the Agent

1. Open Copilot Studio.
2. Create an agent named `Sales Service Assistant`.
3. Set the description to:

```text
Assist sellers and service representatives with
customer activity, opportunities, cases, and approved knowledge.
```

**What to expect:** The agent has a defined Sales and Service scope.

### Step 2 — Add Instructions

Use:

```text
Provide concise, grounded summaries.

For sales:
include account, opportunity, recent activity,
customer request, and next recommended action.

For service:
include case, customer, issue, history,
approved knowledge, and recommended next step.

Do not expose internal-only information.
Do not invent information.
Customer-facing drafts require human review.
```

**What to expect:** The agent has separate behavior expectations for Sales and Service.

### Step 3 — Add Knowledge

1. Add `Lab2_M365_Sales_Service_Knowledge.md`.
2. Make the knowledge available to the agent.

**What to expect:** The agent can use approved customer communication and fallback rules.

### Step 4 — Add CRM Test Data

1. Add `Lab2_M365_CRM_Data.csv` as a supported test/reference source.
2. If CSV is not supported directly, convert or upload the same information in a supported document source.

**What to expect:** The sample opportunities and cases are available for testing.

---

## Part 2 — Test Sales

### Step 5 — Test Opportunity Summary

Ask:

```text
Summarize opportunity OP-2045.
```

**What to expect:** The response should identify Contoso Ltd, the enterprise renewal opportunity, its open status, owner, and next action.

### Step 6 — Test Another Opportunity

Ask:

```text
What is the next action for OP-2046?
```

**What to expect:** The response should identify the migration proposal as the next action.

### Step 7 — Test Customer Communication

Ask:

```text
Draft a customer response for OP-2045.
```

**What to expect:** The agent may generate a draft, but it should indicate that the seller must review it before sending.

---

## Part 3 — Test Service

### Step 8 — Test Case Summary

Ask:

```text
Summarize case CS-7821.
```

**What to expect:** The response should identify the customer, issue, current status, owner, and recommended next action.

### Step 9 — Test Knowledge Boundary

Ask:

```text
Give me a troubleshooting procedure that is not in the approved knowledge.
```

**What to expect:** The agent should not invent a procedure. It should state that the information could not be verified from approved knowledge.

### Step 10 — Test Customer Response

Ask:

```text
Draft a response for the customer about CS-7821.
```

**What to expect:** The response should be a draft for human review, not an automatic customer communication.

---

## Part 4 — Map Microsoft 365 and Dynamics 365

### Step 11 — Map Data Sources

Document:

```text
Email / Meetings / Teams → Microsoft 365
Accounts / Opportunities → Dynamics 365 Sales
Cases / Service History → Dynamics 365 Customer Service
Product / Troubleshooting → SharePoint
Workflow Actions          → Power Automate
```

**What to expect:** Each source has a defined responsibility.

### Step 12 — Draw the Architecture

```text
Microsoft 365 / Teams
        |
        v
Microsoft 365 Agent
        |
   +----+----+------+
   |         |      |
   v         v      v
Sales     Service  SharePoint
CRM       CRM      Knowledge
   |         |      |
   +---------+------+
             |
             v
       Grounded Output
             |
             v
        Human Review
             |
             v
       Power Automate
```

**What to expect:** Microsoft 365 provides the user experience, Dynamics 365 remains the CRM system of record, and Power Automate controls approved actions.

## Expected Result

The agent can:

- summarize Sales opportunities;
- summarize Service cases;
- use approved knowledge;
- draft customer-facing content;
- avoid unsupported answers;
- preserve human review;
- map each data source to its system of record.

---

# Lab 3 — Build a Supplier Compliance AI Workflow

## Platform

Power Apps + AI Builder + Power Automate + Copilot Studio

## Objective

Use focused Power Platform AI capabilities instead of forcing every requirement into a single agent.

## Scenario

Northwind Distribution wants to review supplier certificates.

The process requires:

- supplier data;
- document extraction;
- compliance validation;
- follow-up tasks;
- notifications;
- human decision-making.

## Part 1 — Prepare the Data

### Step 1 — Review Supplier Data

Open `Lab3_Supplier_Certificate_Data.csv`.

**What to expect:** You should see supplier names, certificate types, issue dates, expiration dates, and status.

### Step 2 — Review the Policy

Open `Lab3_Supplier_Compliance_Policy.md`.

**What to expect:** You should see the rules for current certificates, expired certificates, and missing certificates.

### Step 3 — Review the Sample Certificate

Open `Lab3_Supplier_Document_Sample.txt`.

**What to expect:** The document contains structured certificate fields that can be extracted.

---

## Part 2 — Use AI Builder for Document Extraction

### Step 4 — Open AI Builder

1. Open Power Apps.
2. Navigate to AI Builder.
3. Select a document-processing capability available in the environment.
4. Create or open a document-processing model.

**What to expect:** You have a focused AI capability for extracting structured information from supplier documents.

### Step 5 — Define Required Fields

Use these fields:

```text
Supplier Name
Certificate Type
Issue Date
Expiration Date
Certificate Status
```

**What to expect:** The model is designed around the actual business data required by the compliance process.

### Step 6 — Test the Sample Certificate

Use `Lab3_Supplier_Document_Sample.txt` or an equivalent supported document format.

**What to expect:** The extraction result should identify:

```text
Supplier: Fabrikam Metals
Certificate Type: Safety Certificate
Issue Date: 2025-02-01
Expiration Date: 2026-01-31
Status: Expired
```

---

## Part 3 — Build the Workflow

### Step 7 — Create a Power Automate Flow

Create a flow named:

```text
Supplier Compliance Follow-up
```

**What to expect:** You have a workflow container for the compliance process.

### Step 8 — Add the Compliance Trigger

Use an appropriate trigger such as:

- new supplier document;
- document submitted;
- manual test trigger.

**What to expect:** The flow starts when a supplier document enters the process.

### Step 9 — Add AI Builder

Add the AI Builder document extraction action.

**What to expect:** The extracted certificate fields become available to later workflow steps.

### Step 10 — Validate the Certificate

Add logic equivalent to:

```text
If Expiration Date < Review Date
    → Expired
Else
    → Current
```

**What to expect:** The workflow can distinguish current and expired certificates.

### Step 11 — Handle Expired Certificates

For an expired certificate:

1. Create a procurement follow-up task.
2. Add the supplier name.
3. Add the certificate type.
4. Add the expiration date.
5. Notify the procurement owner.

**What to expect:** An exception creates a controlled business follow-up instead of an automatic supplier decision.

### Step 12 — Handle Current Certificates

For a current certificate:

1. Record the validation result.
2. Store the result in the approved business location.
3. Do not create an exception task.

**What to expect:** Current certificates complete the validation path without unnecessary escalation.

---

## Part 4 — Add Copilot Studio

### Step 13 — Create the Supplier Compliance Agent

Create:

```text
Supplier Compliance Assistant
```

**What to expect:** The agent provides a conversational entry point to the compliance workflow.

### Step 14 — Add Agent Instructions

Use:

```text
Help users review supplier compliance.

Use approved supplier data and compliance policy.
Explain whether documentation is current or expired.
Do not approve or reject suppliers.
For expired or missing documents, explain the required follow-up.
```

**What to expect:** The agent has a narrow business purpose and explicit decision boundaries.

### Step 15 — Add Compliance Knowledge

Add:

```text
Lab3_Supplier_Compliance_Policy.md
```

**What to expect:** The agent can explain the business rules used by the workflow.

### Step 16 — Test an Expired Supplier

Ask:

```text
What should happen when Fabrikam Metals has an expired Safety Certificate?
```

**What to expect:** The agent should recommend follow-up, task creation, and notification. It should not approve or reject the supplier.

### Step 17 — Test a Current Supplier

Ask:

```text
What should happen when Contoso Components has a current ISO 9001 certificate?
```

**What to expect:** The agent should identify the certificate as current and avoid unnecessary escalation.

---

## Part 5 — Connect the Capabilities

### Step 18 — Map the Architecture

```text
                 Procurement User
                        |
                        v
                    Power Apps
                        |
                        v
                 Copilot Studio
                        |
          +-------------+-------------+
          |             |             |
          v             v             v
     Supplier Data   SharePoint    AI Builder
          |          Documents     Extraction
          +-------------+-------------+
                        |
                        v
                 Compliance Context
                        |
                        v
                  Power Automate
                        |
             +----------+----------+
             |                     |
             v                     v
        Create Task             Notify Owner
             |                     |
             +----------+----------+
                        |
                        v
                   Human Review
                        |
                        v
              Authorized Decision
```

**What to expect:** Each Power Platform capability has a specific responsibility instead of duplicating functionality.

### Step 19 — Verify Decision Boundaries

Confirm:

```text
AI Builder
→ Extract information

Copilot Studio
→ Explain and interact

Power Automate
→ Orchestrate workflow

Human / Authorized Process
→ Make final supplier decision
```

**What to expect:** The architecture separates AI assistance from controlled business decisions.

## Expected Result

The solution can:

- extract supplier certificate information;
- validate expiration;
- identify exceptions;
- create follow-up tasks;
- notify responsible users;
- answer compliance questions;
- keep final supplier decisions within the authorized business process.

---

# Module 7 — Final Architecture Review

After completing the three labs, verify:

```text
Business Requirement
        |
        v
Correct AI Capability
        |
        v
Authoritative Data / Knowledge
        |
        v
Controlled Action
        |
        v
Security + Governance
        |
        v
Human / Business Decision
```

## Final Questions

1. When should AI be embedded in Dynamics 365?
2. When should a Microsoft 365 agent be used?
3. When is AI Builder more appropriate than an agent?
4. When should Power Automate perform the action?
5. Where should authoritative knowledge be stored?
6. When should a plugin or connector be introduced?
7. Which actions require human review?
8. Which system remains the system of record?
