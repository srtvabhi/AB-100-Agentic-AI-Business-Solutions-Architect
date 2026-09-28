# Case Study 1 --- Enterprise AI Adoption Strategy

## Business Scenario

Contoso Manufacturing wants to move from isolated AI experiments to an
enterprise AI program.

Different departments have started small pilots: - Customer Service uses
AI for case summaries. - Sales uses Copilot for proposal drafting. -
Operations wants an agent for troubleshooting. - Finance wants
AI-assisted analysis. - IT is concerned about duplicated solutions,
inconsistent governance, and unclear ownership.

The executive sponsor asks the solution architect to create one adoption
strategy.

## Current Situation

The organization has: - Microsoft 365 - SharePoint - Dynamics 365
Customer Service and Sales - Azure - Several disconnected AI pilots - No
common AI intake process - No common agent governance model

## Architect Challenge

Design an enterprise approach that moves AI workloads from ideas to
production without blocking useful experimentation.

## Architecture

``` text
Business Strategy
      ↓
AI Use-Case Inventory
      ↓
Prioritize by Value + Feasibility
      ↓
AI Technology Decision
      ↓
AI Ready Foundation
      ↓
Govern + Secure
      ↓
Standard Build Process
      ↓
Operate + Monitor
      ↓
Measure Business Outcomes
```

## CAF / Agent Lifecycle Mapping

  Enterprise stage   Architect concern
  ------------------ -----------------------------------------
  Strategy           Outcomes, use cases, platform direction
  Plan               Skills, PoC, readiness
  Ready              Landing zones, data, connectivity
  Govern             Policies, roles, approvals
  Secure             Identity, data, platform protection
  Build              Standard agent patterns and evaluation
  Manage             Monitoring, cost, incidents, lifecycle

## Architect Decision

The architect proposes: 1. An AI use-case inventory. 2. A platform
decision tree. 3. An AI governance charter. 4. Standard
development/evaluation gates. 5. An AI asset inventory. 6. An AI CoE. 7.
Operational telemetry and cost reporting.

## Discussion Questions

**Q: Why not let every department choose its own AI platform?**\
Expected answer: Independent choices can create duplicated capabilities,
inconsistent security, fragmented governance, and higher operational
complexity.

**Q: Where should experimentation occur?**\
Expected answer: In controlled environments with clear data, security,
and Responsible AI boundaries.

**Q: What is the architect's role?**\
Expected answer: Translate business strategy into a governed technology
and operating model.

## Key Takeaway

Enterprise AI strategy is an operating model, not just a list of AI
products.
