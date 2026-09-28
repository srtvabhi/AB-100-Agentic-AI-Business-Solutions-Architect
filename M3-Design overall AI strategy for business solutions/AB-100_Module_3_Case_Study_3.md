# Case Study 3 --- Extend Microsoft 365 Copilot or Build a Custom Agent?

## Business Scenario

Contoso's HR team asks for an AI assistant.

Requirements: 1. Answer policy questions from SharePoint. 2. Summarize
HR emails and documents. 3. Draft employee communications. 4. Create an
HR case in an external case-management system. 5. Run a multi-step
approval workflow. 6. Support autonomous follow-up when a case remains
unresolved.

## Architect Analysis

### Requirements 1--3

These align closely with Microsoft 365 productivity and organizational
knowledge.

Potential approach: **Extend Microsoft 365 Copilot.**

### Requirements 4--6

These introduce: - External system integration - Business actions -
Multi-step workflow - Operational autonomy

Potential approach: **Custom agent using Copilot Studio or Microsoft
Foundry**, depending on complexity.

## Architecture

``` text
                 Employee
                    ↓
           Microsoft 365 Copilot
              /                    Productivity       HR Knowledge
          Tasks               ↓
                              SharePoint

                    ↓
             Specialized HR Agent
                    ↓
       ┌────────────┼────────────┐
       ↓            ↓            ↓
 Case System     Approval     Follow-up
```

## Architect Questions

**Q: Why not build everything as a custom agent?**\
Expected answer: It adds unnecessary complexity when existing Microsoft
365 capabilities already satisfy part of the requirement.

**Q: Why not keep everything in Microsoft 365 Copilot?**\
Expected answer: External systems, complex workflows, multi-step
orchestration, or autonomy may exceed the simple extension scenario.

## Key Takeaway

Use the simplest architecture that meets the full requirement, and
introduce customization only where the business need requires it.
