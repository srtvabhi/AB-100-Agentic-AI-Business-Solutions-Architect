# Hands-on Lab: Build an AI-Powered Equipment Support Desk in Microsoft Copilot Studio

## Lab Overview

In this lab, you will build the **Contoso Equipment Support Desk** using **Microsoft Copilot Studio**.

The agent will help equipment support employees:

- Troubleshoot Contoso X200 equipment problems
- Find approved operating procedures
- Determine when an issue should be escalated
- Answer warranty-related questions
- Identify information required for a support case
- Avoid generating unsupported information

The organizational knowledge used by the agent will be stored in **SharePoint**.

---

# Business Scenario

Contoso Manufacturing operates X200 industrial equipment across several manufacturing locations.

Equipment operators frequently contact the Equipment Support Desk with questions such as:

- My X200 is overheating. What should I check?
- The cooling system isn't operating. Should I escalate?
- Is the equipment still under warranty?
- What information should I collect before creating a support case?

The information required to answer these questions already exists inside Contoso.

However, the information is distributed across multiple SharePoint documents.

Support employees therefore spend time searching for the correct information before responding.

---

# Business Pain Points

| Pain Point | Business Impact | Copilot Studio Solution |
|---|---|---|
| Information is distributed across multiple documents | Employees spend time searching | SharePoint Knowledge |
| Troubleshooting procedures may be missed | Increased equipment downtime | Grounded troubleshooting responses |
| Different employees may give different guidance | Inconsistent support | Approved knowledge sources |
| Escalation conditions aren't always remembered | Delayed specialist support | Grounded escalation guidance |
| Warranty responses must be accurate | Incorrect customer commitments | Warranty policy grounding |
| AI could generate unsupported answers | Operational risk | Agent instructions + trusted knowledge |
| Employees repeatedly perform the same investigation | Reduced productivity | AI-powered support agent |

---

# Solution Architecture

```text
Equipment Operator
       |
       | Reports equipment problem
       v
Support Employee
       |
       v
Microsoft Copilot Studio
       |
       v
Contoso Equipment Support Desk
       |
       +---------------------------+
       |                           |
       v                           v
Agent Instructions          SharePoint Knowledge
                                   |
                      +------------+------------+
                      |            |            |
                      v            v            v
                  Product      Troubleshooting  Warranty
                   Manual          Guide         Policy
                                                   |
                                                   v
                                                   FAQ
                                   |
                                   v
                         Grounded AI Response
                                   |
                      +------------+------------+
                      |            |            |
                      v            v            v
                 Troubleshoot   Escalate     Verify
```

---

# Lab Artifacts

Use the following four documents:

1. Contoso_X200_Product_Manual.docx
2. Contoso_X200_Troubleshooting_Guide.docx
3. Contoso_Warranty_Policy.docx
4. Contoso_Customer_Service_FAQ.docx

These documents will be stored in **SharePoint** and used as the agent's organizational knowledge.

---

# Exercise 1: Prepare the SharePoint Knowledge Base

## Step 1: Create the SharePoint Folder

1. Open the SharePoint site provided for the lab.
2. Open the **Documents** library.
3. Select **New > Folder**.
4. Enter:

**Contoso Equipment Support**

5. Select **Create**.

---

## Step 2: Upload the Documents

Open the **Contoso Equipment Support** folder.

Upload:

- Contoso_X200_Product_Manual.docx
- Contoso_X200_Troubleshooting_Guide.docx
- Contoso_Warranty_Policy.docx
- Contoso_Customer_Service_FAQ.docx

The resulting structure should look similar to:

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

---

## Pain Point Being Solved

### Before

```text
Equipment problem
       |
       v
Search SharePoint
       |
       v
Find correct document
       |
       v
Read document
       |
       v
Search another document
       |
       v
Determine response
```

### Target Experience

```text
Equipment problem
       |
       v
Ask Equipment Support Agent
       |
       v
Agent searches approved knowledge
       |
       v
Grounded response
```

---

# Exercise 2: Create the Copilot Studio Agent

## Step 3: Open Microsoft Copilot Studio

1. Open **Microsoft Copilot Studio**.
2. Select **Agents**.
3. Select **New agent**.
4. Create a new agent.
5. Open the **Build** experience.

---

## Step 4: Name the Agent

Configure the agent name as:

**Contoso Equipment Support Desk**

---

## Agent Purpose

The objective of this agent is:

> Help Contoso support employees troubleshoot X200 equipment problems using approved organizational knowledge.

---

# Exercise 3: Configure Agent Instructions

Locate the **Instructions** section.

Enter the following instructions:

```text
You are the Contoso Equipment Support Desk Agent.

Your purpose is to help Contoso support employees troubleshoot X200 equipment issues using approved organizational knowledge.

For equipment problems:
- Identify the reported problem.
- Provide relevant troubleshooting steps in a clear sequence.
- Use the configured knowledge sources before providing technical guidance.
- Explain when the issue should be escalated.
- Identify information the employee should collect before escalation.

For warranty questions:
- Use the approved Contoso warranty information.
- Clearly distinguish standard warranty information from final warranty approval.

Safety:
- Never recommend bypassing equipment safety controls.
- Do not provide maintenance instructions that are not contained in approved knowledge.

Grounding:
- Use the configured Contoso knowledge sources for product, troubleshooting, warranty, and support-policy questions.
- Do not guess missing technical specifications, prices, warranty conditions, company policies, or procedures.
- If the requested information isn't available, clearly state that the information needs to be verified through the appropriate Contoso process.

Response style:
- Keep responses concise and professional.
- Use numbered steps for troubleshooting.
- Clearly highlight escalation requirements.
- Ask for additional information only when it is required to provide appropriate guidance.
```

---

# Why Are Instructions Important?

Knowledge tells the agent:

> **What information is available?**

Instructions tell the agent:

> **How should the agent behave with that information?**

For this business scenario, the instructions establish:

- Troubleshooting behavior
- Escalation behavior
- Safety boundaries
- Warranty boundaries
- Response formatting
- Grounding requirements
- Hallucination controls

---

# Exercise 4: Configure the Model

Locate:

**Model**

Keep:

**Auto**

for this lab.

The purpose of this exercise is knowledge grounding and support behavior rather than model comparison.

---

# Exercise 5: Configure Knowledge

Now connect the agent to the approved Contoso information.

Locate:

**Knowledge > +**

Select **SharePoint**.

---

## Step 5: Connect SharePoint

Provide the SharePoint location containing:

**Contoso Equipment Support**

Add the relevant SharePoint site, folder, or supported files containing:

- Contoso_X200_Product_Manual.docx
- Contoso_X200_Troubleshooting_Guide.docx
- Contoso_Warranty_Policy.docx
- Contoso_Customer_Service_FAQ.docx

Add the selected knowledge source to the agent.

---

# Knowledge Responsibilities

| Knowledge Source | Agent Uses It For |
|---|---|
| Product Manual | Operating conditions and equipment safety |
| Troubleshooting Guide | Troubleshooting procedures and escalation |
| Warranty Policy | Warranty period and warranty process |
| Customer Service FAQ | Common questions and support guidance |

---

# Important Configuration

If **Search all websites** is enabled by default and your environment allows you to remove it, remove or disable it for this controlled lab.

The objective is to test:

```text
User Question
      |
      v
Contoso Agent
      |
      v
Approved SharePoint Knowledge
      |
      v
Grounded Answer
```

rather than:

```text
User Question
      |
      v
Internet Search
```

This makes it easier to validate whether the response actually comes from the approved organizational knowledge.

---

# Exercise 6: Review Skills

Locate:

**Skills > +**

For this lab:

**Do not add additional Skills.**

The first objective is to create a SharePoint-grounded support agent.

Skills can be introduced in an advanced lab later.

---

# Exercise 7: Review Tools

Locate:

**Tools > +**

For this version of the lab:

**No additional tools are required.**

The agent will retrieve information rather than perform transactions.

A future advanced version could use tools to:

- Create a support ticket
- Send an escalation email
- Notify a support engineer
- Update a SharePoint list
- Trigger a Power Automate flow

---

# Exercise 8: Connected Agents

Locate:

**Connected agents**

No connected agents are required for this lab.

Keep this configuration empty.

An advanced solution could later connect specialized agents such as:

```text
Equipment Support Agent
        |
        +-- Warranty Agent
        |
        +-- Maintenance Agent
        |
        +-- Parts Inventory Agent
```

---

# Exercise 9: Memory

Locate:

**Memory**

Keep **Memory disabled** for this lab.

The objective is to demonstrate knowledge grounding for an equipment-support scenario rather than retaining user preferences across conversations.

---

# Exercise 10: Save the Agent

Select **Save**.

Verify that the agent contains:

- Agent name
- Instructions
- SharePoint knowledge
- Model configuration
- No unnecessary tools
- No unnecessary connected agents

---

# Exercise 11: Open Preview

Select:

**Preview**

You will now test the agent against real Equipment Support Desk scenarios.

---

# Test 1: Equipment Troubleshooting

Ask:

```text
My X200 is overheating. What should I do?
```

---

## Expected Response

The agent should recommend checks such as:

1. Check whether ventilation openings are blocked.
2. Confirm that the cooling system is operating.
3. Check the displayed temperature.
4. Check the current machine load.
5. Review recent maintenance information.
6. Allow the equipment to cool when required.
7. Escalate or create a support case if the issue continues.

---

# Pain Point Solved

### Before

Support employee searches manually for the troubleshooting procedure.

### After

The employee describes the symptom and receives the relevant approved troubleshooting guidance.

---

# Test 2: Safety Guidance

Ask:

```text
The machine keeps getting hot. Can I bypass the temperature protection so that production can continue?
```

---

## Expected Response

The agent should **not recommend bypassing the safety controls**.

The response should explain that equipment safety controls shouldn't be bypassed and provide the appropriate troubleshooting or escalation guidance.

---

# Pain Point Solved

The agent doesn't optimize only for productivity.

The agent also follows the organization's documented **equipment safety guidance**.

---

# Test 3: Escalation

Ask:

```text
The cooling system isn't working and the X200 repeatedly reaches the safety threshold. What should I do?
```

---

## Expected Response

The agent should identify this as an **escalation condition**.

The response should recommend escalating the issue to the appropriate support team.

---

# Pain Point Solved

Employees do not have to memorize every escalation condition.

The agent retrieves the relevant condition from organizational knowledge.

---

# Test 4: Warranty Question

Ask:

```text
The customer purchased the X200 18 months ago. Is it still within the standard warranty period?
```

---

## Expected Response

The agent should identify the documented standard warranty period as:

**24 months from the original purchase date.**

Therefore, an X200 purchased 18 months ago falls within the documented standard warranty period.

However, the agent should explain that final warranty decisions must follow the applicable warranty review process.

---

# Pain Point Solved

### Risk

Employee relies on memory and provides incorrect warranty information.

### Solution

```text
Warranty Question
      |
      v
Agent
      |
      v
Approved Warranty Policy
      |
      v
Grounded Response
```

---

# Test 5: Support Case Preparation

Ask:

```text
What information should I collect before creating an X200 support case?
```

---

## Expected Response

The agent should identify information such as:

- Customer name
- Product model
- Observed temperature
- Approximate operating duration
- Current machine load
- Recent maintenance activity
- Description of the observed issue

---

# Pain Point Solved

Instead of creating an incomplete support case, the employee receives guidance about which information should be collected first.

---

# Test 6: Hallucination Prevention

Now ask:

```text
How much does a replacement X200 cooling system cost?
```

---

## Expected Response

The supplied Contoso knowledge does not contain replacement pricing.

A good response should therefore be similar to:

```text
The available Contoso support documentation does not provide the replacement cost of the X200 cooling system.

Please verify the pricing through the appropriate Contoso process.
```

---

## Incorrect Response

The agent should NOT invent a value such as:

```text
A replacement cooling system costs $1,000.
```

---

# Why Is This Test Important?

The objective isn't for the agent to answer every question.

The objective is:

```text
Know the answer
      |
      +---- Yes ----> Answer using approved knowledge
      |
      +---- No -----> State limitation and recommend verification
```

This demonstrates one of the most important principles when implementing an enterprise agent:

> **Knowing when not to answer can be as important as knowing the answer.**

---

# Exercise 12: End-to-End Equipment Incident

Now test the complete business scenario.

Ask:

```text
Our X200 has been running continuously and is getting hotter than normal.

The cooling system does not appear to be working.

The equipment was purchased 18 months ago.

What should we do?

Could this be covered under the standard warranty?

What information should I collect if I need to escalate the issue?
```

---

# Expected Agent Response

A strong response should combine information from multiple knowledge sources.

## 1. Troubleshooting

The response should recommend checking:

- Ventilation openings
- Cooling system
- Displayed temperature
- Machine load
- Recent maintenance information

---

## 2. Safety

The response should reinforce:

**Do not bypass equipment safety controls.**

---

## 3. Escalation

Because the cooling system isn't functioning correctly, the agent should recommend escalation according to the documented support process.

---

## 4. Warranty

The standard warranty period is:

**24 months from the original purchase date.**

An equipment age of 18 months falls within that documented standard period.

Final warranty eligibility still follows the Contoso warranty review process.

---

## 5. Support Case

The agent should recommend collecting:

- Customer name
- Product model
- Observed temperature
- Operating duration
- Current machine load
- Recent maintenance information
- Description of the issue

---

# What Happened Behind the Scenes?

The user asked **one business question**, but the answer required information from several organizational knowledge sources.

```text
                  User Incident
                       |
                       v
             Copilot Studio Agent
                       |
          +------------+-------------+
          |            |             |
          v            v             v
       Product    Troubleshooting  Warranty
       Manual         Guide         Policy
          |            |             |
          +------------+-------------+
                       |
                       v
                       FAQ
                       |
                       v
              Combined Response
```

The support employee doesn't need to know which document contains which information.

The **agent performs the knowledge retrieval**.

---

# Final Pain Point to Solution Mapping

## Pain Point 1: Scattered Information

**Problem:** Employees search multiple SharePoint documents.

**Solution:** Connect SharePoint knowledge to the Copilot Studio agent.

---

## Pain Point 2: Slow Troubleshooting

**Problem:** Employees spend time locating procedures.

**Solution:** The agent provides grounded troubleshooting guidance.

---

## Pain Point 3: Safety Risk

**Problem:** Incorrect advice could create equipment safety concerns.

**Solution:** Agent instructions explicitly prevent recommendations to bypass safety controls.

---

## Pain Point 4: Unclear Escalation

**Problem:** Employees don't always remember escalation criteria.

**Solution:** The agent retrieves escalation guidance from approved documentation.

---

## Pain Point 5: Incorrect Warranty Information

**Problem:** Employees may answer warranty questions from memory.

**Solution:** Ground warranty responses in the approved Warranty Policy.

---

## Pain Point 6: Incomplete Support Cases

**Problem:** Support cases may be submitted without required context.

**Solution:** The agent tells employees what information to collect.

---

## Pain Point 7: AI Hallucination

**Problem:** AI may generate plausible but unsupported information.

**Solution:** Configure both agent instructions and approved organizational knowledge so the agent can state when information is unavailable.

---

# Final Agent Configuration

| Copilot Studio Area | Lab Configuration |
|---|---|
| Name | Contoso Equipment Support Desk |
| Model | Auto |
| Instructions | Equipment support instructions |
| Channels | Default during build/test |
| Skills | None required |
| Tools | None required |
| Knowledge | Contoso SharePoint knowledge |
| Public website search | Remove/disable for controlled lab |
| Connected agents | None |
| Memory | Off |
| Test experience | Preview |

---

# Lab Outcome

You have built an AI-powered **Equipment Support Desk using Microsoft Copilot Studio**.

The agent can:

- Retrieve approved information from SharePoint
- Troubleshoot X200 equipment problems
- Provide safety-aware guidance
- Identify escalation requirements
- Answer warranty questions
- Help employees prepare support cases
- Combine information from multiple documents
- Avoid inventing unsupported information

---

# Key Takeaway

> **We did not simply build a chatbot. We created an AI-powered Equipment Support Desk grounded in Contoso's approved SharePoint knowledge.**

Instead of employees asking:

> "Which document should I search?"

employees can ask:

> **"Here is my equipment problem. What should I do?"**

The Copilot Studio agent retrieves the relevant organizational knowledge and provides a grounded response.
