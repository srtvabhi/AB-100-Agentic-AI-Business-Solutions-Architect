# Case Study 3 — Intelligent Model Routing for a Global AI Platform

## Company

**Northwind Global Services** operates a large internal AI platform used by employees in multiple regions.

The platform supports:

- Document classification
- Customer-service summarization
- Sales content generation
- Complex business analysis
- Internal question answering

The organization currently sends every request to one large language model.

This creates two problems:

1. Simple requests consume an expensive model.
2. Complex requests sometimes require stronger reasoning than smaller models can provide.

---

## Current Architecture

```text
                 USER
                  │
                  ▼
             AI PLATFORM
                  │
                  ▼
             LARGE MODEL
                  │
                  ▼
               RESPONSE
```

The architecture team wants to introduce model routing.

---

## Proposed Architecture

```text
                    USER
                     │
                     ▼
                AI PLATFORM
                     │
                     ▼
                MODEL ROUTER
                     │
       ┌─────────────┼─────────────┐
       ▼             ▼             ▼
     SLM        SPECIALIZED      LARGE
     Model         Model         Model
       │             │             │
       └─────────────┼─────────────┘
                     ▼
                  RESPONSE
                     │
                     ▼
                MONITORING
             /      |       \
          Cost    Latency   Quality
```

---

## Routing Requirements

The router should consider:

- Task type
- Request complexity
- Model capability
- Cost
- Latency
- Business/domain requirements
- Reliability
- Policy constraints

---

## Example Routing

### Scenario 1 — Document Classification

Request:

> Classify this document as Sales, Finance, HR, Customer Service, or Operations.

Routing:

```text
Classification
      │
      ▼
Small / Efficient Model
```

The task is relatively simple and may not require a large model.

---

### Scenario 2 — Customer-Service Summary

Request:

> Summarize a customer case and identify the key troubleshooting actions.

Routing:

```text
Customer-Service Summary
          │
          ▼
Medium / Specialized Model
```

The model needs sufficient quality while controlling cost and latency.

---

### Scenario 3 — Complex Business Analysis

Request:

> Analyze a multi-year financial scenario and explain the impact of several strategic options.

Routing:

```text
Complex Reasoning
       │
       ▼
High-Capability Model
```

Quality and reasoning capability become more important.

---

# Model Router Decision Flow

```text
                  REQUEST
                     │
                     ▼
                TASK TYPE
                     │
                     ▼
                COMPLEXITY
                     │
                     ▼
             MODEL CAPABILITY
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
        COST       LATENCY    QUALITY
          │          │          │
          └──────────┼──────────┘
                     ▼
                MODEL ROUTER
                     │
                     ▼
              SELECT MODEL
```

---

# Fallback Architecture

The organization also wants resilience.

```text
             MODEL ROUTER
                  │
                  ▼
             PRIMARY MODEL
                  │
             ┌────┴────┐
             │         │
          Success    Failure
             │         │
             ▼         ▼
          Response  BACKUP MODEL
                        │
                        ▼
                     Response
```

---

# Model Evaluation

Before production deployment, the architecture team compares the routed architecture with the existing single-model architecture.

Evaluation dimensions:

| Dimension | Measurement |
|---|---|
| Quality | Accuracy and response quality |
| Cost | Cost per request / workload |
| Latency | Response time |
| Reliability | Failure and fallback behavior |
| Policy | Compliance with business constraints |

The goal is not simply to reduce model cost.

For example:

```text
             MODEL ROUTER
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
     Lower       Same       Lower
      Cost      Quality     Latency
       │          │          │
       └──────────┼──────────┘
                  ▼
        ACCEPTABLE TRADE-OFF?
              /        \
            YES         NO
             │           │
             ▼           ▼
         Production   Rework
```

---

# Regional Considerations

Because Northwind operates globally, the architecture team also evaluates:

- Model availability by region
- Data-processing requirements
- Deployment location
- Security requirements
- Policy constraints
- Latency for regional users

The router must only select models that satisfy the workload's eligibility and organizational constraints.

---

# Operational Monitoring

```text
                 MODEL ROUTER
                      │
                      ▼
                MODEL SELECTION
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
        Quality      Cost       Latency
          │           │           │
          └───────────┼───────────┘
                      ▼
                  TELEMETRY
                      │
                      ▼
              CONTINUOUS REVIEW
```

The organization can use this data to determine whether routing is actually improving the workload.

---

## Key Questions

1. Which tasks can use smaller models?
2. Which tasks require higher-capability models?
3. What routing criteria should be applied?
4. How will cost be measured?
5. How will quality be measured?
6. What happens if a selected model is unavailable?
7. What regional constraints apply?
8. How will the routed architecture be compared with the current baseline?

## Module 4 Topics

- Model Router
- Intelligent model selection
- Cost optimization
- Latency
- Quality
- Reliability
- Specialized models
- Small language models
- Regional requirements
- Monitoring and evaluation
