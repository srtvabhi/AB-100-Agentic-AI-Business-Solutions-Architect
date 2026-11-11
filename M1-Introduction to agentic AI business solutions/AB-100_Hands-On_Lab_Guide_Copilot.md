# Hands-on Lab: Build an AI-Powered Equipment Support Desk

## Lab Overview

In this lab, you will build the **Contoso Equipment Support Desk** using **Microsoft 365 Copilot Agent Builder**.

The agent will help equipment support employees:

- Troubleshoot **Contoso X200** equipment issues
- Find relevant troubleshooting procedures
- Identify when an issue should be escalated
- Answer warranty-related questions
- Prepare information required for a support case
- Avoid generating unsupported answers

The agent will use approved organizational documents stored in **SharePoint** as its knowledge source.

---

## Estimated Duration

**25–30 minutes**

---

## Business Scenario

Contoso Manufacturing operates X200 industrial equipment across multiple manufacturing locations.

Equipment operators regularly contact the Equipment Support Desk with questions such as:

- My X200 is overheating. What should I check?
- When should the issue be escalated?
- Is the equipment still under warranty?
- What information should I collect before opening a support case?

The required information exists, but it is distributed across multiple documents in SharePoint.

Support engineers may have to locate and review several documents before responding.

The goal of this lab is to create an AI-powered Equipment Support Desk that allows employees to describe the problem in natural language and receive answers grounded in approved company information.

---

# Business Pain Points

| Pain Point | Business Impact | Lab Solution |
|---|---|---|
| Information is scattered across documents | Employees spend time searching | Ground the agent with SharePoint knowledge |
| Troubleshooting steps may be missed | Longer equipment downtime | Provide step-by-step troubleshooting guidance |
| Different employees may provide different answers | Inconsistent support experience | Use approved organizational knowledge |
| Employees may not know when to escalate | Delayed problem resolution | Provide documented escalation criteria |
| Warranty information must be accurate | Incorrect commitments to customers | Ground answers in the warranty policy |
| AI could generate unsupported information | Operational and safety risk | Configure the agent not to guess |

---

# Solution Architecture

```text
Equipment Operator
        |
        | "My X200 is overheating"
        v
Microsoft 365 Copilot
        |
        v
Contoso Equipment Support Desk Agent
        |
        v
SharePoint Knowledge
        |
        +-- Product Manual
        +-- Troubleshooting Guide
        +-- Warranty Policy
        +-- Customer Service FAQ
        |
        v
Grounded Support Response
```

---

# Lab Artifacts

Use the following four files:

1. Contoso_X200_Product_Manual.docx
2. Contoso_X200_Troubleshooting_Guide.docx
3. Contoso_Warranty_Policy.docx
4. Contoso_Customer_Service_FAQ.docx

These files will be uploaded to **SharePoint** and configured as knowledge sources for the agent.

---

# Exercise 1: Prepare the SharePoint Knowledge Base

## Step 1: Create the SharePoint Folder

1. Open your training **SharePoint** site.
2. Open the **Documents** library.
3. Select **New > Folder**.
4. Enter the folder name:

**Contoso Equipment Support**

5. Select **Create**.

---

## Step 2: Upload the Lab Artifacts

Open the **Contoso Equipment Support** folder.

Upload:

- Contoso_X200_Product_Manual.docx
- Contoso_X200_Troubleshooting_Guide.docx
- Contoso_Warranty_Policy.docx
- Contoso_Customer_Service_FAQ.docx

Your SharePoint structure should look similar to:

```text
Documents
|
+-- Contoso Equipment Support
    |
    +-- Contoso_X200_Product_Manual.docx
    +-- Contoso_X200_Troubleshooting_Guide.docx
    +-- Contoso_Warranty_Policy.docx
    +-- Contoso_Customer_Service_FAQ.docx
```

### Pain Point Being Solved

Previously, support information could exist across different documents.

SharePoint now becomes the central location containing the **approved equipment-support knowledge** used by the agent.

---

# Exercise 2: Create the Equipment Support Agent

## Step 3: Open Agent Builder

1. Open **Microsoft 365 Copilot**.
2. Navigate to **Agents**.
3. Select **New agent**.
4. Open **Configure**.

---

## Step 4: Configure the Agent Identity

Enter the following information.

### Name

**Contoso Equipment Support Desk**

### Description

```text
Helps equipment support employees troubleshoot Contoso X200 issues, identify escalation requirements, check warranty information, and prepare support cases using approved company knowledge.
```

### Pain Point Being Solved

Support employees now have **one conversational interface** for equipment-support questions instead of manually deciding which document to search.

---

# Exercise 3: Configure the Agent Instructions

## Step 5: Add Instructions

Locate:

**Configure > Instructions**

Enter:

```text
You are the Contoso Equipment Support Desk Agent.

Use the configured Contoso knowledge sources to answer equipment support questions.

For equipment problems, provide clear troubleshooting steps in the correct order.

Clearly explain when an issue should be escalated.

For warranty questions, use the approved warranty policy.

Never recommend bypassing equipment safety controls.

If requested information is not available in the approved knowledge sources, clearly state that the information needs to be verified.

Never guess or invent company policies, prices, procedures, technical specifications, or warranty information.
```

### Why Are These Instructions Important?

The instructions establish the expected behavior of the agent.

The agent should:

- Use approved organizational information
- Provide actionable troubleshooting guidance
- Respect equipment safety requirements
- Recognize escalation situations
- Avoid inventing unavailable information

This turns the agent from a general AI assistant into a **purpose-specific Equipment Support Desk agent**.

---

# Exercise 4: Configure Skills

## Step 6: Review Skills

Locate:

**Skills > Add**

For this lab:

**Do not add additional skills.**

The objective of the lab is to demonstrate a **knowledge-grounded agent**.

The agent does not need to perform external actions.

---

# Exercise 5: Connect SharePoint Knowledge

## Step 7: Add Knowledge

Locate:

**Knowledge > Add knowledge**

Select:

**Work content / Cloud files**

---

## Step 8: Find the SharePoint Content

Search for:

**Contoso Equipment Support**

Locate the SharePoint folder created earlier.

Add the following documents:

- Contoso_X200_Product_Manual.docx
- Contoso_X200_Troubleshooting_Guide.docx
- Contoso_Warranty_Policy.docx
- Contoso_Customer_Service_FAQ.docx

---

## Knowledge Responsibilities

| Knowledge Source | Primary Purpose |
|---|---|
| Product Manual | Operating conditions and equipment safety |
| Troubleshooting Guide | Troubleshooting and escalation |
| Warranty Policy | Warranty questions and coverage |
| Customer Service FAQ | Common support questions and fallback guidance |

### Pain Point Being Solved

Employees no longer need to know **which document contains the answer**.

They describe the business problem, and the agent can retrieve relevant information from the configured SharePoint knowledge.

---

# Exercise 6: Configure Other Agent Builder Options

## Step 9: Web Search

For this lab, keep **Web search out of scope**.

We want learners to clearly see that the agent is using approved organizational information stored in SharePoint.

---

## Step 10: Copilot Connectors

Do not configure a **Copilot connector** for this lab.

The required information already exists in SharePoint.

---

## Step 11: Attachments

Leave **Attachments** empty.

The documents should be connected through SharePoint knowledge rather than uploaded directly as local attachments.

---

# Exercise 7: Configure Suggested Prompts

Add the following Suggested Prompts.

---

## Suggested Prompt 1

**Title:** Troubleshoot overheating

**Message:**

```text
My X200 is overheating. Guide me through the checks I should perform.
```

---

## Suggested Prompt 2

**Title:** Check escalation

**Message:**

```text
The X200 cooling system isn't working. Should the issue be escalated?
```

---

## Suggested Prompt 3

**Title:** Check warranty

**Message:**

```text
The customer purchased the X200 18 months ago. What does the standard warranty policy say?
```

---

## Suggested Prompt 4

**Title:** Prepare support case

**Message:**

```text
What information should I collect before creating an X200 support case?
```

---

# Exercise 8: Test Equipment Troubleshooting

Now test whether the agent can solve actual Equipment Support Desk problems.

## Test Scenario 1: Equipment Overheating

Ask:

```text
My X200 is overheating. What should I do?
```

### Expected Result

The agent should provide guidance around:

1. Checking ventilation openings
2. Confirming that the cooling system is operating
3. Checking the displayed temperature
4. Checking the current machine load
5. Reviewing recent maintenance
6. Allowing the equipment to cool when required
7. Creating a support case if the problem continues

### Pain Point Solved

**Before**

The support engineer manually searches for the troubleshooting guide.

**After**

The employee describes the symptom and receives the relevant troubleshooting procedure.

---

# Exercise 9: Test Escalation Guidance

## Test Scenario 2: Cooling System Failure

Continue the support scenario.

Ask:

```text
The cooling system isn't working and the machine repeatedly reaches the safety threshold. What should I do?
```

### Expected Result

The agent should recommend that the problem be **escalated to the support team**.

It should also avoid recommending that the operator bypass any equipment safety controls.

### Pain Point Solved

Support engineers don't have to memorize every escalation condition.

The agent helps retrieve the documented escalation guidance when needed.

---

# Exercise 10: Test Warranty Knowledge

## Test Scenario 3: Warranty Question

Ask:

```text
The customer purchased the X200 18 months ago. Is it still within the standard warranty period?
```

### Expected Result

The agent should explain that the standard X200 warranty period is:

**24 months from the original purchase date.**

Because the equipment was purchased 18 months ago, it is within the documented standard warranty period.

However, the agent should also explain that final warranty eligibility must follow the applicable warranty review process.

### Pain Point Solved

Employees don't need to answer warranty questions from memory.

The agent retrieves the relevant approved warranty information.

---

# Exercise 11: Prepare a Support Case

## Test Scenario 4: Support Case Preparation

Ask:

```text
What information should I collect before creating an X200 support case?
```

### Expected Result

The agent should identify information such as:

- Customer name
- Product model
- Observed temperature
- Approximate operating duration
- Current machine load
- Recent maintenance activity
- Description of the observed issue

### Pain Point Solved

Incomplete support cases can create unnecessary back-and-forth between support teams.

The agent helps employees collect the required information before escalating the problem.

---

# Exercise 12: Test Hallucination Prevention

This is an important test of the agent's grounding behavior.

## Test Scenario 5: Information Not Available

Ask:

```text
How much will replacing the X200 cooling system cost?
```

### Expected Behavior

The knowledge sources do not contain replacement pricing.

Therefore, the agent should respond with something similar to:

```text
The available Contoso documentation does not provide the replacement cost of the X200 cooling system. Please verify the cost through the appropriate Contoso support process.
```

### The Agent Should NOT Respond With

```text
The cooling system costs $1,000.
```

or any other invented amount.

### Pain Point Solved

```text
Unsupported AI answer
        |
        v
Grounded Agent
        |
        v
Information unavailable
        |
        v
Do not guess
        |
        v
Recommend verification
```

This demonstrates an important principle of enterprise AI:

> A good business agent should know when it **doesn't have enough approved information to answer**.

---

# Exercise 13: End-to-End Support Challenge

Now test the complete solution.

Give the agent the following incident:

```text
Our X200 has been running continuously and is getting hotter than normal.

The cooling system does not appear to be working.

The machine was purchased 18 months ago.

What should we do, could this be covered under warranty, and what information should I collect if I need to escalate?
```

---

## Expected Agent Reasoning

A strong response should combine information from multiple SharePoint knowledge sources.

### 1. Troubleshooting

The agent should recommend checking:

- Ventilation
- Cooling system
- 
