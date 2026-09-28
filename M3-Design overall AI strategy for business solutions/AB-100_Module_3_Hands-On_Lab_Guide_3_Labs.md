# AB-100 Module 3 — Hands-On Lab Guide

## Lab 1 — Microsoft 365 Copilot: Prebuilt Capabilities and Prompt Library

### Platform

Microsoft 365 Copilot / Copilot Chat

### Topics Covered

- Topic 5 — Prebuilt Microsoft 365 Copilot agents
- Topic 10 — Prompt library
- Topic 12 — Prompt engineering
- Topic 13 — Business user roles
- Topic 17 — User prompt training

### Prerequisites

- Microsoft 365 Copilot access
- A sample customer-service document or email
- Microsoft 365 Copilot Prompt Gallery access

### Steps

1. Open Microsoft 365 Copilot or Copilot Chat.
2. Open the Prompt Gallery.
3. Find a prompt related to summarization, analysis, or business communication.
4. Save the prompt to your prompts.
5. Open the prompt and review:
   - Role
   - Task
   - Context
   - Expected output
6. Create a new customer-service prompt:

```text
You are a customer-service analyst.

Review the supplied customer communication.

Identify:
- Customer issue
- Product
- Symptoms
- Important customer history
- Recommended next step

Do not invent information.
Clearly separate known information from suggestions.
```

7. Run the prompt against the sample customer communication.
8. Review the response.
9. Modify the prompt by adding an output format:

```text
Return the result using:
1. Customer Issue
2. Product
3. Symptoms
4. Relevant History
5. Recommended Next Step
```

10. Run the prompt again.
11. Compare the first and second results.
12. Save the improved prompt.
13. Share the prompt with a team or add it to the team's approved prompt collection if your environment supports team prompt sharing.
14. Run a second prompt for a manager:

```text
You are a customer-service manager.

Review the supplied support information.

Identify:
- Main customer issue
- Recurring pattern
- Business risk
- Information that requires human validation

Do not make the final business decision.
```

15. Review whether the prompt is appropriate for a manager persona.
16. Record the final prompt and the user persona it is intended for.

### Expected Result

You have:

- Used a prebuilt Microsoft 365 Copilot capability.
- Created and improved a reusable prompt.
- Used different prompts for different business roles.
- Practiced explicit instructions, context, constraints, and output format.

---

# Lab 2 — Copilot Studio: Enterprise Knowledge, Rules, and Business Action

### Platform

Microsoft Copilot Studio

### Topics Covered

- Topic 3 — Strategy for building AI agents
- Topic 6 — Rules and constraints
- Topic 7 — Knowledge sources
- Topic 8 — Extend or build custom agents
- Topic 10 — Prompt library
- Topic 12 — Prompt engineering
- Topic 13 — Business user roles
- Topic 17 — User adoption

### Prerequisites

- Microsoft Copilot Studio access
- SharePoint site access
- A SharePoint document library
- Sample business documents

### Step 1 — Prepare SharePoint

1. Open SharePoint.
2. Create or open a site named:

```text
Contoso Customer Support
```

3. Create an `AI Knowledge` document library.
4. Add folders:

```text
Product
Troubleshooting
Policies
FAQ
```

5. Upload approved sample documents.
6. Create a SharePoint list named:

```text
Support Cases
```

7. Add columns:

```text
Title
Customer
Product
Issue
Priority
Status
```

8. Create one or two sample records.

---

### Step 2 — Create the Agent

1. Open Microsoft Copilot Studio.
2. Create a new agent.
3. Name it:

```text
Contoso Customer Support Agent
```

4. Add instructions:

```text
You are a customer-support assistant.

Use approved company knowledge to answer customer-support questions.

Do not invent policies, warranty terms, troubleshooting procedures, or customer information.

If required information is not available, state that the information is not available.

Do not make final financial, legal, or compliance decisions.

Only perform business actions when the user explicitly requests the action.
```

5. Save the agent.

---

### Step 3 — Add SharePoint Knowledge

1. Open the agent.
2. Go to the Knowledge area.
3. Select **Add knowledge**.
4. Select **SharePoint**.
5. Enter the URL for the `AI Knowledge` site or appropriate folder.
6. Add a clear description:

```text
Approved Contoso customer-support documentation including
product information, troubleshooting procedures, policies,
and frequently asked questions.
```

7. Add the source to the agent.
8. Save the configuration.

---

### Step 4 — Test Knowledge Retrieval

Run these questions:

```text
What is the warranty period?
```

```text
What should I check if an X200 is overheating?
```

```text
What information is required before creating a support case?
```

```text
What are the warranty exclusions?
```

9. Confirm that the answers are based on the approved SharePoint content.
10. Ask an unrelated question:

```text
What were Contoso's total sales last year?
```

11. Confirm that the agent does not invent an answer when the information is outside its configured knowledge.

---

### Step 5 — Add a Business Tool

1. Open the agent's Tools area.
2. Select **Add a tool**.
3. Add a SharePoint-based action or agent flow that can create a record in the `Support Cases` list.
4. Configure the required inputs:

```text
Customer
Product
Issue
Priority
Status
```

5. Set the default status to:

```text
New
```

6. Add clear tool instructions:

```text
Use this action only when the user explicitly asks to create a support case.

Do not create a case automatically from a general question.
```

7. Add the tool to the agent.
8. Test the tool.

---

### Step 6 — Create a Support Case

Enter:

```text
Create a high-priority support case for Fabrikam.

Product: X200
Issue: The device is overheating.
```

9. Verify the SharePoint list.
10. Confirm:

```text
Customer = Fabrikam
Product = X200
Issue = The device is overheating
Priority = High
Status = New
```

---

### Step 7 — Test the Security Boundary

1. Use an account that has access to the SharePoint knowledge.
2. Ask a question about the approved documents.
3. Confirm the answer is returned.
4. Test with an account that does not have permission to the relevant SharePoint content, if your lab environment supports multiple test accounts.
5. Confirm that unauthorized content is not returned.

---

### Expected Result

You have:

- Built a business-specific Copilot Studio agent.
- Connected enterprise knowledge.
- Applied agent instructions and boundaries.
- Tested out-of-scope questions.
- Added a business action.
- Required explicit user intent before an action.
- Tested permission-aware knowledge access.

---

# Lab 3 — Microsoft Foundry: Model Selection, Prompt Testing, and SLM Evaluation

### Platform

Microsoft Foundry

### Topics Covered

- Topic 3 — Strategy for building AI agents
- Topic 9 — Custom AI models
- Topic 11 — Customized small language models
- Topic 12 — Prompt engineering
- Topic 14 — Regional and local AI data regulation

### Prerequisites

- Azure subscription
- Microsoft Foundry access
- Permission to create or use a Foundry project
- Access to the Foundry model catalog

### Scenario

Contoso has a document-classification workload.

The workload receives short internal documents and classifies them into:

```text
Customer Service
Sales
Finance
Human Resources
Operations
```

The business wants:

- Low latency
- Predictable output
- Low operating cost
- Consistent classification
- Regional deployment options

The architecture team wants to determine whether an existing model or an SLM should be used.

---

### Step 1 — Open the Model Catalog

1. Open Microsoft Foundry.
2. Open the Model Catalog.
3. Search for small language models.
4. Filter models by:
   - Model type
   - Region
   - Supported task
   - Deployment option
5. Open the model card for at least two candidate models.
6. Record:

```text
Model
Provider
Model type
Supported input
Supported output
Region availability
Deployment option
```

---

### Step 2 — Compare Model Options

Create a simple comparison:

| Requirement | Model A | Model B |
|---|---|---|
| Classification capability | | |
| Latency | | |
| Cost considerations | | |
| Region availability | | |
| Deployment option | | |
| Tool calling if required | | |
| Input size | | |
| Output format | | |

7. Identify which model is more appropriate for the classification requirement.
8. Do not select a model based only on model size.

---

### Step 3 — Test a Prompt

1. Open the model playground.
2. Use a system instruction:

```text
You classify internal business documents.

Choose exactly one category:

Customer Service
Sales
Finance
Human Resources
Operations

Return only the category name.

Do not provide explanations.
```

3. Test:

```text
The customer reports that an X200 device is overheating
and requests troubleshooting support.
```

4. Expected classification:

```text
Customer Service
```

5. Test:

```text
The account executive is preparing a proposal for a
new commercial vehicle customer.
```

6. Expected classification:

```text
Sales
```

7. Test:

```text
The monthly invoice reconciliation process is complete.
```

8. Expected classification:

```text
Finance
```

---

### Step 4 — Test Prompt Variations

Test the same input with a weaker prompt:

```text
Classify this document.
```

Then test the structured prompt again.

9. Compare:

- Accuracy
- Output consistency
- Extra text
- Ability to follow the required format

10. Keep the prompt that produces the most consistent result.

---

### Step 5 — Evaluate SLM Suitability

Use the following decision checklist:

```text
Existing model meets requirement?
        |
        +---- YES ---> Use existing model
        |
        +---- NO ----> Evaluate customization
                           |
                           v
                    Fine-tuning required?
                           |
                           +---- YES ---> Evaluate fine-tuning
                           |
                           +---- NO ----> Evaluate SLM
```

11. Record whether an SLM is appropriate for this workload.
12. Record the reason based on:

```text
Accuracy
Latency
Cost
Domain specificity
Data availability
Operational complexity
Regional availability
Security requirements
```

---

### Step 6 — Check Regional Deployment

1. Open the candidate model's deployment information.
2. Check whether the required Azure region is supported.
3. Record the available deployment options.
4. Record any regional limitation that could affect the architecture.
5. Confirm that the selected design satisfies the organization's data and regulatory requirements.

---

### Expected Result

You have:

- Compared models in Microsoft Foundry.
- Tested a structured prompt.
- Compared prompt quality.
- Evaluated an SLM use case.
- Considered model, cost, latency, region, and operational requirements.
- Documented a model-selection decision.

---

# Lab Completion Checklist

## Lab 1

- [ ] Microsoft 365 Copilot used
- [ ] Prompt Gallery used
- [ ] Reusable prompt created
- [ ] Prompt improved
- [ ] Different user personas considered

## Lab 2

- [ ] Copilot Studio agent created
- [ ] SharePoint knowledge connected
- [ ] Knowledge questions tested
- [ ] Out-of-scope question tested
- [ ] Agent rules configured
- [ ] SharePoint action/tool added
- [ ] Support case created
- [ ] Permission boundary tested

## Lab 3

- [ ] Microsoft Foundry model catalog opened
- [ ] Models compared
- [ ] Small language model considered
- [ ] Prompt tested
- [ ] Prompt variation tested
- [ ] Model-selection decision documented
- [ ] Regional deployment checked
