# Case Study 4 --- AI Strategy for a Regulated Global Business

## Business Scenario

Contoso operates in India, the European Union, and the United States.

It wants an AI customer-service solution that: - Uses customer
records. - Summarizes support conversations. - Recommends next
actions. - Uses regional customer data. - Supports human approval for
high-impact actions.

The security and compliance teams require: - Data minimization -
Appropriate access controls - Regional compliance review - Audit
evidence - Human oversight - Retention and deletion rules

## Architect Challenge

Create an AI operating model that allows business teams to use AI while
meeting regional requirements.

## Architecture

``` text
                    AI Strategy
                        ↓
                Use-Case Inventory
                        ↓
              Data Classification
                        ↓
           Regional / Legal Analysis
                        ↓
       ┌────────────────┼────────────────┐
       ↓                ↓                ↓
     India              EU               US
       ↓                ↓                ↓
 Regional Controls + Identity + Data Access
                        ↓
                 AI CoE Governance
                        ↓
             Approved AI Architecture
                        ↓
            Human Oversight + Audit
                        ↓
                  Operations
```

## Architect Checklist

-   Identify jurisdictions.
-   Identify data categories.
-   Identify applicable regulations.
-   Determine data location and transfer requirements.
-   Define access boundaries.
-   Define retention/deletion requirements.
-   Define human approval points.
-   Define evidence and audit requirements.
-   Assign compliance ownership.
-   Review the design before production.

## Discussion Questions

**Q: Can the same architecture be deployed globally without review?**\
Expected answer: Not automatically; regional data and regulatory
requirements must be evaluated.

**Q: Who owns compliance decisions?**\
Expected answer: Business, legal, privacy, security, and compliance
stakeholders with the architect translating requirements into technical
controls.

## Key Takeaway

Compliance is an architecture input from the beginning, not a final
deployment checklist.
