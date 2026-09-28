# Module 4 — Evaluate Costs and Benefits of AI-Powered Business Solutions

## AB-100 Module 4

**Microsoft Learn module:** Evaluate Costs and Benefits of AI-Powered Business Solutions

> **Important:** The current module includes an additional instructional topic on creating ROI analysis. This guide includes it so the complete module flow is covered.

---

# 1. Introduction

When a business asks for an AI solution, the architect should not immediately start building it.

First ask:

- What business problem are we solving?
- What measurable benefit will we get?
- How much will it cost?
- How long until we get value?
- What will it cost to operate for several years?
- Should we build it ourselves?
- Should we buy an existing capability?
- Can we extend an existing Microsoft capability?
- Can we use different AI models to control cost and performance?


## Architecture

```text
                BUSINESS PROBLEM
                       │
                       ▼
                AI USE CASE
                       │
                       ▼
             ┌──────────────────┐
             │  BUSINESS VALUE   │
             └────────┬─────────┘
                      │
             ┌────────▼─────────┐
             │   ROI + TCO       │
             └────────┬─────────┘
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
       BUILD         BUY        EXTEND
          │           │           │
          └───────────┼───────────┘
                      ▼
              MODEL STRATEGY
                      │
                      ▼
              IMPLEMENTATION
                      │
                      ▼
            MEASURE ACTUAL VALUE
```

The architecture is not successful simply because the AI works.

It must also make economic sense.

## Architecture Questions

- What business KPI improves?
- What is today's baseline?
- What will the solution cost?
- What will it cost after deployment?
- How will we measure actual ROI?

## Key Takeaway

> **AI architecture must be justified by measurable business value, not technology capability alone.**

---

# 2. ROI Criteria for AI-Powered Solutions

**ROI means Return on Investment.**

In simple terms:

> What value did we receive compared with what we spent?

AI value is not limited to direct revenue.

Important ROI categories include:

- Productivity
- Cost savings
- Revenue impact
- Risk reduction
- Strategic and innovation value

### Productivity example

```text
Manual case summary
        │
        ▼
30 minutes
        │
        ▼
AI-assisted summary
        │
        ▼
5 minutes
```

Potential benefit:

```text
25 minutes saved per case
```

### Cost savings

AI might reduce:

- Manual data entry
- Support workload
- Repetitive reviews
- Operational overhead

### Revenue impact

AI might contribute to:

- Faster lead qualification
- Better sales conversion
- Customer retention
- Upselling and cross-selling

### Risk reduction

AI could help reduce:

- Errors
- Compliance problems
- Inconsistent processing
- Operational risk

### Strategic value

Examples include:

- Better customer experience
- New business models
- Innovation
- Competitive differentiation

---

# 3. TCO — Total Cost of Ownership

ROI tells you about **value**.

TCO tells you about **the complete cost of owning and operating the solution**.

Do not look only at the AI license or model cost.

Consider the complete lifecycle:

```text
AI Solution Cost

Development
 ├─ Data preparation
 ├─ Prompt engineering
 ├─ Agent development
 ├─ Testing
 └─ Integration

Deployment
 ├─ Infrastructure
 ├─ Licensing
 ├─ Security
 └─ AI/API usage

Operations
 ├─ Monitoring
 ├─ Evaluation
 ├─ Maintenance
 ├─ Support
 └─ Training

Change Management
 ├─ User training
 ├─ Process redesign
 └─ Adoption

Retirement
 ├─ Migration
 └─ Decommissioning
```

## Architecture — ROI + TCO

```text
                  AI SOLUTION
                      │
        ┌─────────────┴─────────────┐
        ▼                           ▼
     BENEFITS                      COSTS
        │                           │
 ┌──────┼──────┐          ┌─────────┼─────────┐
 ▼      ▼      ▼          ▼         ▼         ▼
Productivity Revenue   Development Deployment Operations
Cost Saving  Risk      Change Mgmt  Retirement
        │                           │
        └─────────────┬─────────────┘
                      ▼
                 ROI ANALYSIS
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
       Payback        NPV      ROI Ratio
```

## Architecture Questions

1. What business outcome are we measuring?
2. What is today's baseline?
3. What benefit will AI create?
4. What costs occur before go-live?
5. What costs continue after go-live?
6. What costs occur when the solution is replaced?

## Key Takeaway

> **Never calculate AI ROI using only license or model cost.**

---

# 4. Create ROI Analysis for a Proposed AI Solution

Start with the business process and establish a baseline.

Example:

```text
1,000 cases/month
30 minutes manual handling/case
```

If AI reduces handling to 20 minutes:

```text
10 minutes saved × 1,000 cases
= 10,000 minutes/month
```

The architect then translates that improvement into business value.

Do not stop at:

> AI saves time.

Instead:

```text
Business Process
       ↓
Baseline
       ↓
Expected AI Improvement
       ↓
Measured Benefit
       ↓
Financial Value
       ↓
TCO
       ↓
ROI
```

## ROI Architecture

```text
                 BUSINESS OUTCOME
                       │
                       ▼
                  KPI / BASELINE
                       │
                       ▼
                AI IMPROVEMENT
                       │
                       ▼
              MEASURED BENEFIT
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Time Saved   Cost Saved   Revenue
          │            │            │
          └────────────┼────────────┘
                       ▼
                  FINANCIAL VALUE
                       │
                       ▼
                      TCO
                       │
                       ▼
             ┌─────────────────┐
             │ ROI / NPV /     │
             │ Payback Period  │
             └─────────────────┘
                       │
                       ▼
              BUSINESS DECISION
```

## Measures to understand

### ROI

```text
ROI =
(Net Benefit / Investment Cost) × 100
```

### Payback period

How long does it take for benefits to recover the investment?

### NPV

What is the value of future cash flows when considered in today's terms?

### Cost-benefit ratio

How much benefit is generated relative to cost?

### Annualized ROI

What is the return when expressed on an annual basis?

---

# 5. Build vs Buy vs Extend


There are three primary approaches:

```text
BUILD
BUY
EXTEND
```

---

## BUILD

You create the AI capability yourself.

```text
Business Application
       │
       ▼
Custom AI Service
       │
       ├── Custom Model
       ├── Custom Agent
       ├── Custom Data
       └── Custom APIs
```

### Build can make sense when

- The business process is unique.
- Deep customization is required.
- Proprietary systems need integration.
- Full control over data, IP, or behavior matters.
- Existing commercial solutions do not satisfy requirements.

### Build costs can include

- Engineering
- Infrastructure
- Data preparation
- Testing
- Security
- Operations
- Maintenance

You own more of the lifecycle.

---

# 6. BUY

Use an existing commercial or prebuilt capability.

```text
Business Process
       │
       ▼
Microsoft / Vendor Product
       │
       ▼
Configured AI Capability
```

### Buy can make sense when

- Time-to-value is important.
- The process is relatively standardized.
- Internal engineering resources are limited.
- Vendor support and updates are important.

### Consider

- Vendor dependency
- Limited customization
- Feature gaps
- Vendor lock-in
- Limited extensibility

---

# 7. EXTEND

Start with an existing platform and customize it.

Example:

```text
Microsoft Copilot
       │
       ├── Enterprise Knowledge
       ├── Custom Prompts
       ├── Connectors
       ├── Actions
       ├── Plugins / Skills
       └── Business Logic
```

You do not build everything from scratch.

You use an existing capability and add what the organization needs.

### Extend can make sense when

- An existing platform already provides most required functionality.
- Organization-specific knowledge is required.
- Custom connectors or actions are required.
- Domain-specific behavior is needed.

---

# 8. Build vs Buy vs Extend Architecture

```text
                       REQUIREMENT
                            │
                            ▼
                 Is existing capability
                      sufficient?
                     /           \
                   YES            NO
                   │               │
                   ▼               ▼
                  BUY       Can existing platform
                            be customized?
                            /           \
                          YES            NO
                          │               │
                          ▼               ▼
                       EXTEND          BUILD
```


Consider:

- Requirements
- Strategic importance
- Vendor solutions
- Extension possibilities
- Custom build requirements
- TCO
- ROI
- Time-to-value
- Risk
- Scalability
- Long-term sustainability

## Build / Buy / Extend Cost Architecture

```text
                 TOTAL COST
                     │
     ┌───────────────┼────────────────┐
     ▼               ▼                ▼
Infrastructure   Development       Data
     │               │                │
     ▼               ▼                ▼
Compute          Integration       Cleansing
Storage          APIs              Grounding
Network          Governance        Indexing
                     │
                     ▼
                Expertise
                     │
                     ▼
                  Operations
```

### Cost areas

| Cost area | What you're asking |
|---|---|
| Infrastructure | What compute, storage, and networking are required? |
| Development | How much engineering and integration is required? |
| Data | How much cleansing, grounding, and indexing is required? |
| Expertise | What skills are required? |
| Operations | What does it cost to monitor and maintain? |

---

# 9. Model Router

A model router helps an application choose an appropriate AI model for each request.

Imagine three models:

```text
Small Model
     ↓
Cheap + Fast
     ↓
Simple tasks

Medium Model
     ↓
Moderate cost/performance
     ↓
Normal business tasks

Large Model
     ↓
Expensive + Powerful
     ↓
Complex reasoning
```

Instead of the application manually choosing a model for every request:

```text
                APPLICATION
                     │
                     ▼
               MODEL ROUTER
              /      |      \
             /       |       \
            ▼        ▼        ▼
          SLM     Medium      LLM
```

The router selects an appropriate model based on the request and requirements.

---

# 10. Why Model Routing?

## Cost optimization

Simple tasks can use less expensive models.

```text
Classification
     ↓
Small Model
     ↓
Lower Cost
```

## Performance

Latency-sensitive workloads can use faster models.

## Specialized workloads

Different models can be used for different domains or tasks.

## Reliability

A backup model can be used when the primary model is unavailable.

## Hybrid strategy

You can combine:

```text
Foundation Models
Fine-tuned Models
Custom Models
SLMs
```

---

# 11. Model Routing Criteria

A router can consider:

```text
Request
  │
  ├── Task type
  │
  ├── Complexity
  │
  ├── Model capability
  │
  ├── Cost
  │
  ├── Latency
  │
  └── Business/domain requirements
       │
       ▼
   MODEL SELECTION
```

Examples:

```text
Classification → SLM
Finance domain → Specialized/Fine-tuned model
Complex reasoning → LLM
```

---

# 12. Model Router Architecture

```text
                    USER
                     │
                     ▼
              BUSINESS APP
                     │
                     ▼
              MODEL ROUTER
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
        SLM       Fine-tuned    LLM
          │          │          │
          └──────────┼──────────┘
                     ▼
                 RESPONSE
                     │
                     ▼
                  USER
```

Add operational monitoring:

```text
                 MODEL ROUTER
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
         SLM       Model B     Model C
          │          │          │
          └──────────┼──────────┘
                     ▼
                 RESPONSE
                     │
                     ▼
                MONITORING
             /      |       \
         Cost    Latency   Quality
```

---

# 13. Routing Rules

## Static / rule-based

```text
IF classification
    → SLM
```

## Weighted routing

```text
Model A → 70%
Model B → 30%
```

Useful for controlled experiments or gradual rollout.

## Fallback

```text
Primary Model
      │
      X
      │
      ▼
Backup Model
```

## Version-based

```text
Stable Model
      │
      └── Production traffic

Experimental Model
      │
      └── Selected/test traffic
```

---

# 14. Model Router — Architect View


> Does dynamic model selection improve the workload's cost, performance, and quality tradeoff without violating business requirements?

Do not judge a router only by cost.

Evaluate:

- Quality
- Cost
- Latency
- Policy and business constraints

## Evaluation architecture

```text
                AI WORKLOAD
                     │
                     ▼
              BASELINE MODEL
                     │
                     │
              Measure:
          ┌──────────┼──────────┐
          ▼          ▼          ▼
        Quality     Cost      Latency
          │          │          │
          └──────────┼──────────┘
                     │
                     ▼
                MODEL ROUTER
                     │
                     ▼
              Compare Results
                     │
                     ▼
             Production Decision
```

### Important principle

**Lower cost alone does not mean better architecture.**

If cost decreases but quality falls below the business requirement, the architecture may not be acceptable.

---

# 15. Putting the Whole Module Together


```text
                 BUSINESS PROCESS
                        │
                        ▼
                  AI USE CASE
                        │
                        ▼
               DEFINE BUSINESS KPI
                        │
                        ▼
                 DEFINE BASELINE
                        │
                        ▼
               IDENTIFY AI BENEFIT
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
           ROI VALUE             TCO
              │                   │
              └─────────┬─────────┘
                        ▼
                 ROI ANALYSIS
                        │
                        ▼
             BUILD / BUY / EXTEND
                        │
                        ▼
                MODEL STRATEGY
                        │
                        ▼
                 MODEL ROUTER
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
            SLM       MODEL       LLM
             │          │          │
             └──────────┼──────────┘
                        ▼
                   AI SOLUTION
                        │
                        ▼
                  REAL USAGE
                        │
                        ▼
                 MEASURE ROI
                        │
                        ▼
                RE-EVALUATE
```

---

# 16. Study Plan

## Hour 1 — ROI and TCO

Topics:

```text
ROI
TCO
Business outcomes
Productivity
Cost savings
Revenue
Risk reduction
Strategic value
```

Understand:

> **ROI = value generated**

> **TCO = complete lifecycle cost**

Build your own business example.

---

## Hour 2 — ROI Analysis

Practice this flow:

```text
Business Outcome
       ↓
Baseline
       ↓
AI Improvement
       ↓
Benefit
       ↓
Financial Value
       ↓
TCO
       ↓
ROI
       ↓
Payback / NPV
```

You should be able to explain this without notes.

---

## Hour 3 — Build vs Buy vs Extend

```text
Unique + strategic + control
             ↓
           BUILD

Standard + fast + vendor capability
             ↓
            BUY

Existing platform + customization
             ↓
           EXTEND
```

Decision criteria:

```text
TCO
ROI
Time-to-value
Risk
Customization
Governance
Scalability
Long-term maintenance
```

---

## Hour 4 — Model Router + Scenarios

Focus on:

```text
Multiple models
      ↓
Model Router
      ↓
Task / Complexity / Cost / Latency
      ↓
Best-suited model
```

### Scenario A

10 million simple classifications.

Decision:

```text
Simple task → smaller/cheaper model
```

### Scenario B

Complex reasoning with high business impact.

Decision:

```text
Complex/high-quality requirement → stronger model
```

### Scenario C

Organization wants one application endpoint but multiple models.

Decision:

```text
Model Router
```

### Scenario D

Organization needs deterministic use of exactly one model.

Consider direct model deployment rather than dynamic routing.

---

# 17. AB-100 Architecture Mental Model

### Core Architecture

```text
                SHOULD WE DO IT?
                       │
                       ▼
              BUSINESS OUTCOME
                       │
                       ▼
                  ROI + TCO
                       │
                       ▼
             HOW SHOULD WE BUILD?
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
        BUILD         BUY         EXTEND
          │            │            │
          └────────────┼────────────┘
                       ▼
                WHICH MODEL?
                       │
                       ▼
                MODEL ROUTER
                       │
             ┌─────────┼─────────┐
             ▼         ▼         ▼
            SLM      SPECIAL     LLM
             │         │          │
             └─────────┼──────────┘
                       ▼
                 MEASURE AGAIN
```

## The four decisions to explain

| AB-100 concept | The question you should ask |
|---|---|
| **ROI** | What measurable business value will AI create? |
| **TCO** | What will the solution cost across its entire lifecycle? |
| **Build / Buy / Extend** | What implementation approach gives the required value with acceptable cost, risk, and time? |
| **Model Router** | How can different requests use appropriate models while balancing quality, cost, latency, and policy? |

## Module Summary

Module 4 is fundamentally about **making AI architecture economically defensible**.

The architect connects:

```text
Business Need
      ↓
Business Value
      ↓
ROI + TCO
      ↓
Implementation Strategy
      ↓
Build / Buy / Extend
      ↓
Model Strategy
      ↓
Model Routing
      ↓
Measure Actual Results
```
