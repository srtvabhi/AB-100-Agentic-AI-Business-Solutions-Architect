# Case Study 2 --- Single Agent or Multi-Agent?

## Business Scenario

Contoso wants an Order Resolution Assistant.

A customer issue can involve: - Customer Service case information -
Sales order information - Finance/payment status - Field Service
technician status

The first design uses one large agent with access to everything.

Security and ownership teams raise concerns: - Finance data has tighter
access. - Field Service owns its own workflow. - Each team releases
changes independently. - Some actions require approval.

## Architect Challenge

Decide whether to keep one agent or introduce specialized agents.

## Option A --- Single Agent

``` text
User
 ↓
One Agent
 ├─ Customer Service
 ├─ Sales
 ├─ Finance
 └─ Field Service
```

Advantages: - Simpler orchestration - Lower coordination overhead -
Easier initial deployment

Risks: - Broad permissions - Larger scope - More difficult ownership -
Greater blast radius

## Option B --- Multi-Agent

``` text
                  Order Resolution Agent
                         │
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
 Customer Service      Finance      Field Service
    Agent              Agent            Agent
          \              |              /
           └─────────────┼─────────────┘
                         ↓
                  Consolidated Result
                         ↓
                       User
```

## Decision Criteria

The architect checks: - Security boundaries - Team ownership -
Independent release cycles - Specialized knowledge - Multi-step
dependencies - Latency tolerance - Cost - Operational capability

## Discussion Questions

**Q: Is multi-agent automatically better?**\
Expected answer: No. It adds coordination and operational complexity.

**Q: What justifies separate agents here?**\
Expected answer: Different security boundaries, ownership, domain
responsibilities, and business actions.

**Q: What should remain centralized?**\
Expected answer: Overall orchestration rules, security standards,
evaluation, observability, and enterprise governance.

## Key Takeaway

Use multi-agent architecture because the business and governance
boundaries require it---not because multiple agents sound more advanced.
