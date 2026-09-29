# AB-100 Module 5 --- Hands-On Lab Guide

## Lab Overview

These three labs use Microsoft platforms deliberately.

| Lab | Module 5 concept | Platform | Skill |
|---|---|---|---|
| Lab 1 --- Build a Prompt-Driven Task Agent | Topics, task agents, prompt actions, business terms | Microsoft Copilot Studio | Design and test an agent |
| Lab 2 --- Build a Grounded Agent | Knowledge, grounding, fallback, Responsible AI | Microsoft Copilot Studio + SharePoint | Design reliable enterprise knowledge |
| Lab 3 --- Connect an Agent to Business Systems | Custom connectors, Dynamics 365 data, agent flows, success criteria | Copilot Studio + Power Platform | Integrate an agent with business actions |

---

# Lab 1 --- Build a Prompt-Driven Task Agent

## Platform

**Microsoft Copilot Studio**

## Objective

Build an agent that:

- Uses business knowledge
- Uses a defined topic
- Collects required information
- Uses a prompt action
- Handles unsupported questions

## Scenario

Contoso Manufacturing uses the X200 Industrial Controller.

Customer-service employees need an agent that can answer product and warranty questions and collect the information required for a warranty request.

---

## Part 1 --- Prepare the Knowledge

Use:

`Lab_1_Knowledge_Product_Manual.md`

`Lab_1_Knowledge_Warranty_Policy.md`

### Product Manual Data

```text
X200 Industrial Controller

Operating Conditions:
- Operating temperature: -10°C to 50°C
- Input voltage: 24V DC
- Network: Ethernet
- Status indicator:
  Green = normal
  Amber = warning
  Red = fault

Common Faults:

F101 - Overtemperature
Check ventilation, ambient temperature, and cooling fan.

F202 - Network unavailable
Check Ethernet cable, switch connection, and network configuration.

Maintenance:
Inspect ventilation monthly and clean the cooling area when required.
```

### Warranty Policy Data

```text
Standard Warranty:
24-month limited warranty from shipment date.

Covered:
- Manufacturing defects
- Component failure under normal operating conditions

Not Covered:
- Physical damage
- Incorrect installation
- Unauthorized modification
- Operation outside specified conditions

Warranty Request must include:
- Product serial number
- Purchase information
- Description of failure
```

---

## Part 2 --- Create the Agent

### Step 1 --- Open Copilot Studio

Open Microsoft Copilot Studio and select the Power Platform environment for the lab.

### Step 2 --- Create the Agent

Create:

```text
Name:
X200 Service Agent
```

### Step 3 --- Add Instructions

Use:

```text
Answer questions about the X200 Industrial Controller.

Use the supplied product and warranty knowledge.

Do not invent product specifications, prices, or warranty rules.

Ask for clarification when the request is ambiguous.
```

---

## Part 3 --- Add Knowledge

### Step 1 --- Add Product Knowledge

Add:

`Lab_1_Knowledge_Product_Manual.md`

as a knowledge source.

### Step 2 --- Add Warranty Knowledge

Add:

`Lab_1_Knowledge_Warranty_Policy.md`

as a knowledge source.

### Step 3 --- Test Product Knowledge

Ask:

```text
What does F101 mean and what should I check first?
```

Expected result:

```text
F101 means Overtemperature.

The agent should recommend checking:
- Ventilation
- Ambient temperature
- Cooling fan
```

### Step 4 --- Test Warranty Knowledge

Ask:

```text
Is physical damage covered by the X200 warranty?
```

Expected result:

```text
No. Physical damage is not covered.
```

---

## Part 4 --- Create a Warranty Request Topic

### Step 1 --- Create the Topic

Create:

```text
Topic:
Warranty Request
```

### Step 2 --- Configure the Conversation

Collect:

```text
Serial Number
Purchase Information
Failure Description
```

### Step 3 --- Test Complete Information

Use:

```text
Serial Number:
X200-ACC-1001

Purchase Information:
Contoso PO 45821

Failure Description:
Controller reports F101 after continuous operation.
```

### Step 4 --- Verify Completion

Return:

```text
The warranty request contains the required information.
```

### Step 5 --- Test Missing Information

Start the topic again.

Provide:

```text
Serial Number:
X200-ACC-1001

Purchase Information:
Contoso PO 45821
```

Do not provide the failure description.

### Step 6 --- Add the Missing-Information Message

Use:

```text
Please provide the missing warranty information before the request can continue.
```

### Step 7 --- Test Again

Provide:

```text
Failure Description:
Controller reports F101 after continuous operation.
```

Verify that the topic can now complete.

---

## Part 5 --- Create a Prompt Action

Use:

`Lab_1_Prompt_Action_Specification.md`

### Prompt Action Data

```text
Goal:
Create a concise customer-service answer using only the supplied X200 business knowledge.

Context:
Use the product manual and warranty policy.

Rules:
1. Do not invent product specifications.
2. If the supplied knowledge does not contain the answer, state that the information is not available.
3. Keep the answer under 120 words.
4. Separate troubleshooting guidance from warranty guidance.

Output Format:
- Answer
- Relevant product information
- Warranty information, if applicable
- Missing information, if applicable
```

### Step 1 --- Create the Prompt Action

Create a prompt action using the Goal, Context, Rules, and Output Format above.

### Step 2 --- Test the Prompt

Use:

```text
Customer reports F202 Network unavailable
and asks whether the warranty applies.
```

### Step 3 --- Review the Result

Verify that:

- F202 troubleshooting is included.
- Warranty information is separate.
- Unsupported warranty conclusions are not invented.

### Step 4 --- Test an Unknown Value

Ask:

```text
What is the replacement cost of the X200?
```

Verify that the agent states that the information is unavailable.

### Architecture

```text
User
 ↓
Copilot Studio Agent
 ↓
Natural Language
 ↓
Topic / Prompt Action
 ↓
Product + Warranty Knowledge
 ↓
Grounded Response
 ↓
User
```

---

# Lab 2 --- Build a Grounded Enterprise Agent

## Platform

**Microsoft Copilot Studio + SharePoint**

## Objective

Build an agent that uses enterprise knowledge and test:

- Retrieval
- Grounding
- Business terminology
- Fallback
- Permission-aware access
- Responsible AI controls

## Scenario

Contoso has product, troubleshooting, warranty, and customer-support information.

The information must be organized so the agent can retrieve the appropriate source for each question.

---

# Part 1 --- Prepare SharePoint Knowledge

Use:

- `Lab_2_Knowledge_Product_Manual.md`
- `Lab_2_Knowledge_Troubleshooting_Guide.md`
- `Lab_2_Knowledge_Warranty_Policy.md`
- `Lab_2_Knowledge_Support_FAQ.md`

### Product Data

```text
X200 Product Manual

F101:
Overtemperature.
Check ventilation, ambient temperature, and cooling fan.

F202:
Network unavailable.
Check Ethernet cable, switch connection, and network configuration.

Operating temperature:
-10°C to 50°C

Input:
24V DC
```

### Troubleshooting Data

```text
F101 - Overtemperature
1. Check that ventilation openings are clear.
2. Check ambient temperature.
3. Check the cooling fan.
4. If the condition continues, create a support case.

F202 - Network unavailable
1. Check the Ethernet cable.
2. Check switch connectivity.
3. Check network configuration.
4. If the condition continues, create a support case.
```

### Warranty Data

```text
Warranty:
24 months from shipment date.

Covered:
- Manufacturing defects
- Component failure under normal operating conditions

Not covered:
- Physical damage
- Incorrect installation
- Unauthorized modification
- Operation outside specified conditions
```

### Support FAQ Data

```text
Q: What information should be collected before opening a case?
A:
- Customer name
- Product
- Serial number
- Error code
- Description of symptoms
- Troubleshooting already performed

Q: When should a high-priority case be escalated?
A:
When the case has significant business impact or requires priority handling.
```

---

## Part 2 --- Organize SharePoint

### Step 1 --- Create the Site

Create or use:

```text
Contoso Customer Support
```

### Step 2 --- Create the Library

Create:

```text
AI Knowledge
```

### Step 3 --- Create Folders

```text
AI Knowledge
│
├── Product
├── Troubleshooting
├── Policies
└── FAQ
```

### Step 4 --- Upload the Files

Place:

```text
Product
└── Lab_2_Knowledge_Product_Manual.md

Troubleshooting
└── Lab_2_Knowledge_Troubleshooting_Guide.md

Policies
└── Lab_2_Knowledge_Warranty_Policy.md

FAQ
└── Lab_2_Knowledge_Support_FAQ.md
```

---

# Part 3 --- Create the Grounded Agent

### Step 1 --- Create the Agent

In Copilot Studio, create:

```text
Name:
Contoso Customer Support Agent
```

### Step 2 --- Add Instructions

Use:

```text
Help customer-service employees find approved product,
troubleshooting, warranty, and support information.

Use the configured enterprise knowledge.

Do not invent information that is not available in the knowledge sources.
```

### Step 3 --- Add SharePoint Knowledge

Add the SharePoint location containing:

```text
AI Knowledge
```

### Step 4 --- Test Product Retrieval

Ask:

```text
What should I check if the X200 reports F101?
```

Expected information:

```text
Ventilation
Ambient temperature
Cooling fan
```

### Step 5 --- Test Warranty Retrieval

Ask:

```text
What is the X200 warranty period?
```

Expected result:

```text
24 months from shipment date.
```

### Step 6 --- Test FAQ Retrieval

Ask:

```text
What information should I collect before opening a support case?
```

Expected information:

```text
Customer name
Product
Serial number
Error code
Symptoms
Troubleshooting already performed
```

---

# Part 4 --- Test Fallback

### Step 1 --- Ask an Unsupported Question

Use:

```text
What will X200 sales volume be next year?
```

### Step 2 --- Review the Result

Verify that the agent does not invent a forecast.

### Step 3 --- Configure Fallback

Configure the fallback response to:

```text
I do not have approved information for that request.
Please provide a supported product, troubleshooting, warranty,
or customer-support question.
```

### Step 4 --- Test Again

Ask:

```text
What will X200 sales volume be next year?
```

Verify the fallback response.

---

# Part 5 --- Test Business Terminology

Use:

`Lab_2_Business_Terms.csv`

### Business Terms

| Term | Definition | Example |
|---|---|---|
| Escalation | Case requiring priority handling due to business impact | High-priority service case |
| Resolution Status | Current state of customer issue | Resolved |
| Warranty Request | Customer request to validate warranty coverage | Serial number submitted |
| Priority | Service handling priority | High |

### Step 1 --- Test a Business Term

Ask:

```text
What does escalation mean in our support process?
```

### Step 2 --- Test Priority

Ask:

```text
What does High priority mean?
```

### Step 3 --- Verify

Verify that the response uses the defined business terminology.

---

# Part 6 --- Validate Responsible AI Controls

Use:

`Lab_2_Responsible_AI_Checklist.md`

### Checklist

```text
[ ] Business data access is limited to the required scope.
[ ] Users have appropriate permissions.
[ ] Sensitive information is not exposed unnecessarily.
[ ] AI output can be reviewed by a human where required.
[ ] Agent actions have defined business rules.
[ ] Fallback behavior exists for unsupported requests.
[ ] Business terminology is consistent.
[ ] Success criteria are measurable.
```

### Step 1 --- Check Data Access

Verify that the agent only uses the configured knowledge.

### Step 2 --- Check Permissions

Verify that SharePoint permissions are configured for the intended users.

### Step 3 --- Check Unsupported Requests

Run the fallback test again.

### Step 4 --- Check Human Review

Identify any business action that requires human approval.

### Architecture

```text
SharePoint
   |
   v
Organized Knowledge
   |
   v
Access Control
   |
   v
Copilot Studio Agent
   |
   v
Retrieval / Grounding
   |
   v
Relevant Context
   |
   v
Generative Response
   |
   v
User
```

---

# Lab 3 --- Connect an Agent to Business Systems

## Platform

**Microsoft Copilot Studio + Power Platform**

## Objective

Build an agent integration that uses:

- Business terms
- Custom connector
- Dynamics / Dataverse business data
- Agent flow
- Business action
- Success criteria

## Scenario

Contoso customer-service employees need an agent that can retrieve customer account information and escalate high-priority cases.

The agent must distinguish between information retrieval and business actions.

---

# Part 1 --- Prepare the Business Data

Use:

`Lab_3_Business_Terms.csv`

### Business Terms

| Term | Definition | Example |
|---|---|---|
| Escalation | Case requiring priority handling due to business impact | High-priority service case |
| Resolution Status | Current state of customer issue | Resolved |
| Warranty Request | Customer request to validate warranty coverage | Serial number submitted |
| Priority | Service handling priority | High |

### Step 1 --- Open Dataverse

Open the Power Platform environment.

Open the relevant Dataverse table or business data area.

### Step 2 --- Identify Fields

Identify or create fields for:

```text
Priority
Resolution Status
Warranty Request
Escalation
```

### Step 3 --- Align Terminology

Use the definitions above for the business fields.

---

# Part 2 --- Configure the Custom Connector

Use:

`Lab_3_Custom_Connector_API_Spec.md`

### Connector Data

```text
Purpose:
Return customer account information.

Endpoint:
GET /accounts/{accountId}

Example Request:
GET /accounts/ACC1001

Example Response:
{
  "accountId": "ACC1001",
  "customerName": "Contoso Manufacturing",
  "serviceTier": "Gold",
  "region": "North America"
}

Authentication:
Microsoft Entra ID OAuth 2.0

Agent Use:
Retrieve account information only when required by the business scenario.
```

### Step 1 --- Open Power Apps

Open Power Apps in the same environment.

### Step 2 --- Create the Connector

Create a custom connector for the account service.

### Step 3 --- Configure the Operation

Configure:

```text
Method:
GET

Path:
/accounts/{accountId}
```

### Step 4 --- Configure Authentication

Configure the connector according to the environment's Microsoft Entra ID OAuth 2.0 configuration.

### Step 5 --- Test the Connector

Use:

```text
Account ID:
ACC1001
```

### Step 6 --- Verify the Response

Verify:

```text
accountId:
ACC1001

customerName:
Contoso Manufacturing

serviceTier:
Gold

region:
North America
```

---

# Part 3 --- Add the Connector to the Agent

### Step 1 --- Open Copilot Studio

Open:

```text
Case Escalation Agent
```

### Step 2 --- Add the Connector

Add the custom connector action as an agent tool.

### Step 3 --- Configure the Tool Description

Use:

```text
Retrieve customer account information when account context is required.
```

### Step 4 --- Test Account Lookup

Ask:

```text
Get the account information for ACC1001.
```

### Step 5 --- Verify

Verify that the response contains:

```text
Contoso Manufacturing
Gold
North America
```

### Step 6 --- Test Specific Information

Ask:

```text
Tell me the service tier for ACC1001.
```

Expected result:

```text
Gold
```

### Step 7 --- Test Unnecessary Tool Use

Ask:

```text
Explain what F101 Overtemperature means.
```

Verify that the account connector is not required for this question.

---

# Part 4 --- Create the Case Escalation Agent Flow

Use:

`Lab_3_Agent_Flow_Requirements.md`

### Flow Requirements

```text
Flow Name:
Case Escalation Flow

Trigger Inputs:
- CaseId
- Priority
- Customer

Rule:
If Priority is High:
    Create an escalation record.

If Priority is not High:
    Return "No escalation required."

Response:
- CaseId
- Escalated
- Message
```

### Step 1 --- Create the Flow

Create an agent flow named:

```text
Case Escalation Flow
```

### Step 2 --- Configure Inputs

Add:

```text
CaseId
Priority
Customer
```

### Step 3 --- Add the Condition

Configure:

```text
Priority = High
```

### Step 4 --- Configure the High-Priority Branch

Add the action required to create or record an escalation.

Return:

```text
Escalated = Yes
```

### Step 5 --- Configure the Other Branch

Return:

```text
Escalated = No
Message = No escalation required.
```

### Step 6 --- Configure the Response

Return:

```text
CaseId
Escalated
Message
```

### Step 7 --- Save and Publish

Save and publish the flow.

---

# Part 5 --- Add the Flow to the Agent

### Step 1 --- Add the Flow

Add:

```text
Case Escalation Flow
```

as an agent tool.

### Step 2 --- Configure the Description

Use:

```text
Escalates high-priority customer cases.
```

### Step 3 --- Test High Priority

Use:

```text
CaseId:
CS1001

Customer:
Contoso Manufacturing

Priority:
High
```

Expected result:

```text
CaseId:
CS1001

Escalated:
Yes
```

### Step 4 --- Test Medium Priority

Use:

```text
CaseId:
CS1002

Customer:
Northwind Logistics

Priority:
Medium
```

Expected result:

```text
CaseId:
CS1002

Escalated:
No

Message:
No escalation required.
```

---

# Part 6 --- Define Success Criteria

Create three measurable criteria.

### Business Value

```text
High-priority cases can be escalated through the agent
without requiring the employee to manually start the escalation process.
```

### Quality

```text
The agent uses the configured business data and does not
invent account or case information.
```

### Adoption

```text
Service representatives can complete account lookup and
case escalation through the agent workflow.
```

### Step 1 --- Record the Criteria

Record the three criteria in the solution documentation.

### Step 2 --- Test the Complete Flow

Run:

```text
User
 ↓
Agent
 ↓
Business Data
 ↓
Connector
 ↓
Agent Flow
 ↓
Business Action
 ↓
Result
```

### Step 3 --- Test Unsupported Data

Ask:

```text
Get account information for ACC9999.
```

Verify that the agent does not invent the account information.

---

# Final Module 5 Lab Architecture

```text
                         BUSINESS REQUIREMENT
                                  |
                                  v
                           AI Agent Design
                                  |
            +---------------------+---------------------+
            |                     |                     |
            v                     v                     v
       Task Agent          Prompt-Driven Agent    Autonomous / Flow
            |                     |                     |
            +---------------------+---------------------+
                                  |
                                  v
                         Knowledge + Grounding
                                  |
             +--------------------+--------------------+
             |                    |                    |
             v                    v                    v
         SharePoint           Dataverse          Dynamics 365
             |                    |                    |
             +--------------------+--------------------+
                                  |
                                  v
                       Connectors + Agent Flows
                                  |
                                  v
                           Business Actions
                                  |
                                  v
                     Responsible AI Controls
                                  |
                                  v
                         Success Criteria
                                  |
                                  v
                          Business Outcome
```

# Final Lab Questions

**Q: Why did Lab 1 use Copilot Studio topics and prompt actions?**

**Expected answer:** To design a prompt-driven/task-oriented agent with controlled conversation logic and reusable instructions.

**Q: Why did Lab 2 use SharePoint?**

**Expected answer:** To provide enterprise knowledge that the agent can retrieve and use for grounded responses.

**Q: Why did Lab 3 use a custom connector and agent flow?**

**Expected answer:** To demonstrate the difference between retrieving information from a business system and executing a business action.

**Q: What is the difference between knowledge and an action?**

**Expected answer:** Knowledge provides information to the agent; an action allows the agent to perform or trigger a business operation.

**Q: What is the main architecture pattern across the three labs?**

**Expected answer:** Business requirement → agent → knowledge/data → tools/actions → controls → measurable business outcome.
