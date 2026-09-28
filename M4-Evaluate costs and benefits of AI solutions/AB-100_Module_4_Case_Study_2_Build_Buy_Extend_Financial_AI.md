# Case Study 2 — Financial Document AI: Build, Buy, or Extend

## Company

**Fabrikam Financial Services** is a multinational financial-services organization with 18,000 employees.

The company processes:

- Customer applications
- Financial documents
- Compliance documents
- Internal policies
- Risk-analysis documents

The organization wants an AI solution that helps employees review and summarize financial documents.

---

## Business Requirement

The solution should:

1. Extract important information from documents.
2. Summarize documents.
3. Identify relevant policy information.
4. Provide references to approved enterprise knowledge.
5. Integrate with existing business applications.
6. Respect existing identity and access controls.

The solution must support regional data and compliance requirements.

---

## Three Possible Approaches

The architecture team identifies three options.

### Option A — Build

Create a custom AI solution.

```text
Business Applications
        │
        ▼
   Custom AI Platform
        │
   ┌────┼─────┐
   ▼    ▼     ▼
 Model Data  APIs
   │    │     │
   └────┼─────┘
        ▼
   Custom Experience
```

Potential advantages:

- Maximum customization
- Greater control
- Deep integration
- Ability to implement specialized business logic

Potential costs:

- Engineering
- Data preparation
- Infrastructure
- Testing
- Security
- Operations
- Maintenance
- AI expertise

---

### Option B — Buy

Use an existing commercial AI/document capability.

```text
Employees
    │
    ▼
Vendor AI Solution
    │
    ▼
Document Processing
    │
    ▼
Business Output
```

Potential advantages:

- Faster implementation
- Existing capabilities
- Vendor support
- Reduced initial development

Potential considerations:

- Vendor dependency
- Limited customization
- Integration constraints
- Feature gaps
- Long-term licensing costs

---

### Option C — Extend

Use an existing Microsoft capability and add organization-specific functionality.

```text
Existing Microsoft Capability
             │
      ┌──────┼─────────┐
      ▼      ▼         ▼
 Knowledge Connectors Actions
      │      │         │
      └──────┼─────────┘
             ▼
       Business Logic
             │
             ▼
       Financial AI
       Experience
```

Potential advantages:

- Reuse existing platform capabilities
- Faster time-to-value
- Enterprise identity integration
- Add organization-specific knowledge
- Add custom actions and connectors

Potential considerations:

- Platform limitations
- Extension complexity
- Licensing
- Integration requirements

---

## Evaluation Criteria

The architecture team creates a comparison using:

| Criterion | Build | Buy | Extend |
|---|---|---|---|
| Initial development | High | Low | Medium |
| Customization | High | Low/Medium | High |
| Time-to-value | Low | High | Medium/High |
| Integration control | High | Medium | High |
| Internal expertise | High | Low | Medium |
| Long-term maintenance | High | Vendor dependent | Shared |
| Vendor dependency | Lower | Higher | Medium |
| Strategic differentiation | High | Low/Medium | Medium/High |

These values are an architectural assessment for the scenario and should be validated with actual product, licensing, and operational data.

---

## TCO Analysis

The team considers:

```text
              TOTAL COST
                  │
     ┌────────────┼─────────────┐
     ▼            ▼             ▼
Infrastructure Development     Data
     │            │             │
     └────────────┼─────────────┘
                  ▼
              Expertise
                  │
                  ▼
              Operations
                  │
                  ▼
             Change Management
                  │
                  ▼
              Retirement
```

The architect must evaluate both initial and ongoing costs.

---

## Architecture Decision Process

```text
                REQUIREMENTS
                     │
                     ▼
             STRATEGIC IMPORTANCE
                     │
                     ▼
            EXISTING SOLUTIONS?
                 /        \
               YES         NO
                │           │
                ▼           ▼
             EXTEND       BUILD
                │
                ▼
              BUY
          where suitable
```

The decision should not be based on development cost alone.

Consider:

- ROI
- TCO
- Time-to-value
- Risk
- Customization
- Scalability
- Governance
- Security
- Long-term sustainability

---

## Key Questions

1. Is the capability strategically important?
2. Does an existing product meet most requirements?
3. Can the existing platform be extended?
4. What customization is truly required?
5. What is the five-year TCO?
6. What internal skills are required?
7. What vendor dependencies are introduced?
8. Which option provides the required business value with acceptable cost and risk?

## Module 4 Topics

- Build vs Buy vs Extend
- ROI
- TCO
- Time-to-value
- Risk
- Customization
- Scalability
- Long-term sustainability
