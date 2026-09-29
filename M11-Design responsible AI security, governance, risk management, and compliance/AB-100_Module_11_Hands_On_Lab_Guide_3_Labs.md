# AB-100 Module 11 — Hands-On Lab Guide

## Module: Design Responsible AI, Security, Governance, Risk Management, and Compliance

## Lab Overview

These three labs provide practical architecture exercises for Module 11:

1. **Secure and Govern an AI Agent**
2. **Test Model Security and Prompt-Injection Mitigations**
3. **Validate Data Access, Residency, and AI Auditability**

The labs use sample artifacts so you can practice the architecture decisions without requiring production data.

---

# Lab 1 — Secure and Govern an AI Agent

## Objective

Design security and governance controls for an AI customer-service agent that accesses customer data and performs business actions.

## Scenario

Contoso Industrial Systems wants to deploy a customer-service AI agent.

The agent can:

- Search customer records
- Read product information
- Summarize service cases
- Create service requests
- Perform selected customer-service actions

The organization requires least privilege, appropriate approval for high-impact actions, and auditable agent activity.

## Artifacts

- `Lab1_Agent_Permissions.csv`
- `Lab1_Agent_Tools.csv`
- `Lab1_Governance_Risk_Matrix.csv`
- `Lab1_Security_Governance_Checklist.md`

## Steps

### Step 1 — Review user and agent permissions

Open:

`Lab1_Agent_Permissions.csv`

Identify:

- User role
- Data domain
- Permission
- Risk level
- Whether the permission is required

Mark permissions that appear broader than necessary.

### Step 2 — Review available agent tools

Open:

`Lab1_Agent_Tools.csv`

For every tool, identify:

- What the tool can do
- Whether it reads or changes data
- Whether the action is reversible
- Whether human approval should be considered
- What authorization should be checked

### Step 3 — Classify the agent risk

Open:

`Lab1_Governance_Risk_Matrix.csv`

Consider:

- Data sensitivity
- Business impact
- Autonomy
- Financial impact
- Customer impact
- Regulatory impact

Determine the appropriate governance level for the agent.

### Step 4 — Apply security controls

Open:

`Lab1_Security_Governance_Checklist.md`

Validate:

1. Identity is established.
2. Least privilege is applied.
3. Customer data access is restricted.
4. Knowledge sources are approved.
5. Tools are explicitly allowed.
6. Sensitive actions have stronger controls.
7. Agent ownership is defined.
8. Monitoring is enabled.
9. Audit information is available.
10. Production changes are controlled.

### Step 5 — Design the secured architecture

Use this target pattern:

```text
User
  ↓
Microsoft Entra ID
  ↓
Authorization
  ↓
AI Agent
  ↓
+------------------+------------------+
|                  |                  |
v                  v                  v
Knowledge         Model             Tools
|                                     |
v                                     v
Authorized Data                  Controlled APIs
                                      |
                                      v
                               Business Systems
                                      |
                                      v
                              Approval if Required
                                      |
                                      v
                               Audit + Monitoring
```

### Step 6 — Define high-impact actions

Identify actions that should not execute solely because the model requested them.

For each action, document:

- Required permission
- Business rule
- Approval requirement
- Audit requirement
- Rollback or recovery consideration

### Expected Outcome

You should have a security and governance design that limits the agent to authorized data and actions while applying stronger controls to high-impact operations.

---

# Lab 2 — Test Model Security and Prompt-Injection Mitigations

## Objective

Identify direct and indirect prompt-injection risks and design layered controls for model and tool security.

## Scenario

Fabrikam Financial Services has a research agent that retrieves financial documents and can call approved business tools.

Security testing identifies content that attempts to manipulate the agent.

You must analyze the attacks and determine which controls should stop them.

## Artifacts

- `Lab2_Prompt_Injection_Test_Cases.csv`
- `Lab2_Tool_Call_Test_Cases.csv`
- `Lab2_Model_Security_Controls.md`
- `Lab2_Test_Results.csv`

## Steps

### Step 1 — Review prompt-injection scenarios

Open:

`Lab2_Prompt_Injection_Test_Cases.csv`

Classify each scenario as:

- Direct prompt injection
- Indirect prompt injection
- Normal business request
- Data-quality issue
- Security-sensitive request

### Step 2 — Identify the attack boundary

For each injection scenario, identify where the malicious instruction enters the system:

```text
User
 ↓
Agent
 ↓
Retrieved Content
 ↓
Model
 ↓
Tool
 ↓
Business System
```

Record the boundary where the attack should be detected or contained.

### Step 3 — Review tool-call scenarios

Open:

`Lab2_Tool_Call_Test_Cases.csv`

For each proposed tool call, validate:

- User authorization
- Tool authorization
- Parameters
- Data scope
- Business rules
- Action sensitivity

Remember that a model-generated tool call should not automatically be trusted.

### Step 4 — Apply layered security controls

Open:

`Lab2_Model_Security_Controls.md`

Map each attack to controls such as:

- Input validation
- Instruction/data separation
- Grounding controls
- Tool authorization
- Parameter validation
- Output validation
- Human approval
- Monitoring
- Adversarial testing

### Step 5 — Execute the test set

Use:

`Lab2_Test_Results.csv`

Record:

- Test case
- Expected behavior
- Actual behavior
- Control that should mitigate the issue
- Pass/Fail
- Follow-up action

### Step 6 — Design the protected architecture

Use this pattern:

```text
User Input
    ↓
Input Controls
    ↓
Instruction Boundary
    ↓
AI Agent
    ↓
Grounding Data
    ↓
Model
    ↓
Output Validation
    ↓
Tool Authorization
    ↓
Parameter Validation
    ↓
Business Rules
    ↓
Business System
    ↓
Audit + Monitoring
```

### Step 7 — Define model change validation

Assume the organization changes the model from `Model-A-v1` to `Model-A-v2`.

Before production, validate:

1. Security scenarios.
2. Prompt-injection scenarios.
3. Tool-call scenarios.
4. Responsible AI scenarios.
5. Regression scenarios.
6. Performance requirements.
7. Approval requirements.

### Expected Outcome

You should have a layered defense design where model output does not bypass application authorization, business rules, or tool security.

---

# Lab 3 — Validate Data Access, Residency, and AI Auditability

## Objective

Design an end-to-end control model for grounding-data access, data residency, model/tuning permissions, and audit trails.

## Scenario

Northwind Global Services operates an AI assistant across Europe and North America.

The assistant accesses:

- Employee documents
- Customer documents
- Business records
- AI models
- External APIs
- Telemetry and audit systems

Some data is subject to geographic and access restrictions.

## Artifacts

- `Lab3_Data_Classification.csv`
- `Lab3_Data_Flow_Inventory.csv`
- `Lab3_Access_Control_Matrix.csv`
- `Lab3_Audit_Trail_Requirements.md`

## Steps

### Step 1 — Classify the data

Open:

`Lab3_Data_Classification.csv`

For each data type, identify:

- Classification
- Business owner
- Authorized users
- Geographic requirement
- AI usage allowed
- Additional control required

### Step 2 — Map the data flow

Open:

`Lab3_Data_Flow_Inventory.csv`

Trace the path:

```text
Source
 ↓
Connector
 ↓
Agent
 ↓
Model
 ↓
Tool / API
 ↓
Business System
 ↓
Telemetry / Logs
```

Identify every location where data is stored, processed, or moved.

### Step 3 — Review access controls

Open:

`Lab3_Access_Control_Matrix.csv`

Identify:

- Who can access grounding data
- Which agent can access it
- Who can modify model configuration
- Who can tune the model
- Which permissions are broader than necessary

Apply least privilege.

### Step 4 — Validate residency and movement

For every data flow, determine:

1. Where the data originates.
2. Where it is stored.
3. Where it is processed.
4. Which connector moves it.
5. Whether an external service receives it.
6. Where telemetry is stored.

Flag any flow that crosses an unapproved boundary.

### Step 5 — Design audit requirements

Open:

`Lab3_Audit_Trail_Requirements.md`

Determine what must be recorded for:

- Model changes
- Data changes
- Prompt changes
- Agent changes
- Connector changes
- Configuration changes
- Production releases
- Sensitive actions

### Step 6 — Build the audit chain

Use this pattern:

```text
User
 ↓
Identity
 ↓
Agent Version
 ↓
Prompt / Instructions
 ↓
Knowledge / Data Version
 ↓
Model Version
 ↓
Tool / Connector
 ↓
Business Action
 ↓
Result
 ↓
Telemetry / Audit Record
```

### Step 7 — Design incident investigation

Assume users report that the agent started exposing information from the wrong business domain.

Use the audit and data-flow artifacts to determine:

1. Which user made the request.
2. Which agent version handled it.
3. Which knowledge source was accessed.
4. Which model version was used.
5. Which connector was called.
6. What configuration changed.
7. Whether the behavior was caused by an access-control change.
8. What remediation is required.

### Expected Outcome

You should have an architecture that protects grounding data, controls model-management permissions, validates geographic data movement, and provides enough audit information to investigate AI incidents.

---

# Module 11 Lab Completion Checklist

After completing all three labs, verify that you can:

- Secure an AI agent using identity and least privilege.
- Control agent tools and high-impact actions.
- Classify AI solutions by risk.
- Apply governance based on business impact.
- Identify direct prompt injection.
- Identify indirect prompt injection.
- Design layered prompt and model security.
- Validate model-generated tool calls.
- Protect grounding data.
- Control model and tuning permissions.
- Map AI data movement.
- Validate residency requirements.
- Design AI audit trails.
- Trace model, data, agent, and configuration changes.
- Use monitoring and audit information for incident investigation.
