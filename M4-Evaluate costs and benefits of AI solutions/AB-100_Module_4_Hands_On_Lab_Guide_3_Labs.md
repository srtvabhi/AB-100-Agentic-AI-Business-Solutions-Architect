# AB-100 Module 4 — Hands-On Lab Guide

This guide contains three hands-on labs covering:

1. ROI and Total Cost of Ownership
2. Build vs Buy vs Extend
3. Intelligent Model Routing

Each lab includes the scenario data directly in the guide so you can inspect the information before using the supporting artifact.

---

# Lab 1 — Calculate ROI and TCO

**Platform:** Microsoft Excel

## Scenario

Contoso Industrial Systems wants an AI customer-service assistant.

The current support operation handles **120,000 cases per month**. The business expects AI to reduce average handling time from **24 minutes to 17 minutes per case**.

Your task is to calculate the expected benefit, TCO, and ROI, then test how the result changes when the AI improvement changes.

## Step 1 — Open the ROI/TCO workbook

Open:

`Lab_1_ROI_TCO/Lab_1_ROI_TCO_Calculator.xlsx`

The workbook contains two sheets:

- `Assumptions`
- `ROI_TCO`

The `Assumptions` sheet contains the values used by the calculations.

### Data to explore

| Assumption | Value | Reason |
|---|---:|---|
| Cases per month | 120,000 | Current workload |
| Current minutes per case | 24 | Baseline |
| Target minutes per case | 17 | Expected AI improvement |
| Labor cost per hour | $45 | Illustrative value |
| Implementation cost | $250,000 | Illustrative project cost |
| Annual platform/model cost | $180,000 | Illustrative annual cost |
| Annual operations cost | $120,000 | Monitoring, maintenance, support |
| Annual training/change cost | $60,000 | Adoption and training |

Review these values before changing anything.

**Expected result:** You should understand which numbers describe the current business process, which describe the expected AI benefit, and which represent solution costs.

---

## Step 2 — Review the baseline

Open the `ROI_TCO` sheet.

Find:

- Monthly cases
- Current handling time
- Target handling time

The workbook calculates the difference between current and target handling time.

The baseline is:

```text
120,000 cases/month
24 minutes/case
```

The target is:

```text
17 minutes/case
```

**Expected result:** You should see that the expected improvement is **7 minutes per case**.

---

## Step 3 — Review minutes saved

Locate `Minutes saved per case`.

The calculation is:

```text
24 - 17 = 7 minutes
```

This represents the expected time reduction for one case.

**Expected result:** The workbook should show **7 minutes saved per case**.

---

## Step 4 — Review monthly productivity improvement

Locate `Monthly minutes saved`.

The calculation is:

```text
120,000 × 7
= 840,000 minutes/month
```

Then review `Monthly hours saved`.

```text
840,000 / 60
= 14,000 hours/month
```

**Expected result:** You should see **840,000 minutes** or **14,000 hours** of potential monthly productivity improvement.

---

## Step 5 — Review the financial benefit

The workbook uses the illustrative labor cost of **$45/hour**.

Review:

`Monthly productivity value`

The calculation is:

```text
14,000 × $45
= $630,000/month
```

The workbook then annualizes this value.

**Expected result:** The example produces a significant annual benefit, but remember that the $45/hour value is illustrative and should be replaced with an approved organizational assumption for a real business case.

---

## Step 6 — Review TCO

Review these values:

| Cost | Example |
|---|---:|
| Implementation | $250,000 |
| Annual platform/model | $180,000 |
| Annual operations | $120,000 |
| Annual training/change | $60,000 |

The workbook calculates:

```text
Year 1 TCO =
Implementation
+ Platform/model
+ Operations
+ Training/change
```

**Expected result:** Year 1 TCO should include both the initial implementation cost and the first-year ongoing costs.

---

## Step 7 — Review Year 1 ROI

Locate:

- Annual benefit
- Year 1 TCO
- Year 1 net benefit
- Year 1 ROI

The workbook uses:

```text
ROI =
(Net Benefit / Investment Cost) × 100
```

The workbook displays the ROI as a ratio. Convert it to a percentage when interpreting the result.

**Expected result:** You should be able to explain what is driving the ROI instead of treating the ROI number as a standalone answer.

---

## Step 8 — Change the target handling time

Change:

```text
Target handling time
17 → 19 minutes
```

Observe the calculated:

- Minutes saved per case
- Monthly hours saved
- Annual benefit
- ROI

**Expected result:** Because the expected AI improvement is smaller, the calculated benefit and ROI should decrease.

---

## Step 9 — Test a stronger improvement

Change:

```text
Target handling time
19 → 15 minutes
```

Observe the same calculated values.

**Expected result:** A larger reduction in handling time produces a larger calculated benefit and changes the ROI accordingly.

---

## Step 10 — Explore the financial assumptions

Change the labor cost from:

```text
$45/hour
```

to another reasonable test value.

Observe the effect on annual benefit and ROI.

Then restore the value or record the scenario you want to retain.

**Expected result:** You should see that ROI depends not only on AI performance, but also on the financial assumptions used to translate productivity into business value.

---

## Step 11 — Complete the ROI analysis record

Open:

`Lab_1_ROI_TCO/Lab_1_ROI_Analysis_Template.md`

Record:

- Business outcome
- Baseline
- Target
- Benefit drivers
- TCO categories
- ROI
- Payback period
- NPV
- Cost-benefit ratio
- Validation assumptions

**Expected result:** You should have a business-oriented ROI record that connects operational improvement to financial value.

---

# Lab 2 — Evaluate Build, Buy, or Extend

**Platform:** Microsoft Excel

## Scenario

Fabrikam Financial Services wants an AI capability for financial documents.

The solution needs to:

- Extract information from documents
- Summarize documents
- Use approved enterprise knowledge
- Integrate with business applications
- Respect identity and security controls
- Support regional requirements

You will compare:

```text
BUILD
BUY
EXTEND
```

---

## Step 1 — Open the scenario

Open:

`Lab_2_Build_Buy_Extend/Lab_2_Build_Buy_Extend_Scenario.md`

Review the requirements before scoring the options.

**Expected result:** You should understand what the business needs before evaluating the implementation approach.

---

## Step 2 — Review the decision criteria

Open:

`Lab_2_Build_Buy_Extend/Lab_2_Build_Buy_Extend_Decision_Matrix.csv`

The starting data is:

| Criterion | Weight | Build | Buy | Extend |
|---|---:|---:|---:|---:|
| Time-to-value | 20 | 2 | 5 | 4 |
| Customization | 20 | 5 | 2 | 4 |
| Integration control | 15 | 5 | 3 | 5 |
| Initial cost efficiency | 10 | 2 | 5 | 4 |
| Long-term maintenance | 10 | 2 | 5 | 4 |
| Vendor dependency | 10 | 5 | 2 | 3 |
| Strategic differentiation | 10 | 5 | 2 | 4 |
| Scalability | 5 | 4 | 4 | 4 |

Scores use:

```text
1 = poor fit
2 = weak fit
3 = acceptable
4 = strong fit
5 = very strong fit
```

**Expected result:** You should see that each approach has strengths and weaknesses. No option is automatically correct for every requirement.

---

## Step 3 — Open the matrix in Excel

Open the CSV in Microsoft Excel.

Add three columns:

```text
Build Weighted
Buy Weighted
Extend Weighted
```

**Expected result:** The matrix becomes a weighted decision model rather than a simple feature comparison.

---

## Step 4 — Calculate the Build weighted score

For each row, calculate:

```text
Weight × Build Score
```

For example:

```text
Time-to-value:
20 × 2 = 40
```

Repeat the calculation for every criterion.

**Expected result:** Each criterion now contributes a weighted value to the Build option.

---

## Step 5 — Calculate Buy and Extend weighted scores

Repeat the same calculation:

```text
Weight × Buy Score
Weight × Extend Score
```

For every criterion.

**Expected result:** You should have three weighted-score columns that can be compared using the same business criteria.

---

## Step 6 — Calculate total scores

Add the weighted values for each approach.

Calculate:

```text
Total Build Score
Total Buy Score
Total Extend Score
```

**Expected result:** You will have an initial quantitative comparison of the three approaches.

Do not treat the highest number as the complete architecture decision. The weights and scores are assumptions that must be validated.

---

## Step 7 — Test the importance of time-to-value

Change the `Time-to-value` weight from:

```text
20 → 30
```

Reduce another weight by 10 so the total weighting remains consistent.

Recalculate the totals.

**Expected result:** The ranking of the options may change when the business gives more importance to rapid delivery.

---

## Step 8 — Test the importance of customization

Increase the `Customization` weight.

Reduce another weight by the same amount.

Recalculate the totals.

**Expected result:** An organization that values specialized behavior more heavily may produce a different architectural preference.

---

## Step 9 — Review Build

Review the Build option using these areas:

```text
Customization
Integration control
Strategic differentiation
Engineering effort
Infrastructure
Data
Operations
Maintenance
```

**Expected result:** Build provides significant control and customization but creates greater responsibility for development and lifecycle operations.

---

## Step 10 — Review Buy

Review:

```text
Time-to-value
Vendor capability
Vendor dependency
Customization limits
Licensing
Integration
Long-term cost
```

**Expected result:** Buy can reduce development effort and speed implementation, but the organization accepts greater dependency on the selected vendor and its capabilities.

---

## Step 11 — Review Extend

Review:

```text
Existing platform
Enterprise identity
Knowledge
Connectors
Actions
Business logic
Customization
Platform limitations
```

**Expected result:** Extend can reuse an existing platform while adding organization-specific capabilities.

---

## Step 12 — Complete the architecture decision record

Open:

`Lab_2_Build_Buy_Extend/Lab_2_Architecture_Decision_Record.md`

Complete:

- Business requirement
- Strategic importance
- Build assessment
- Buy assessment
- Extend assessment
- TCO considerations
- ROI considerations
- Time-to-value
- Security and governance
- Integration
- Scalability
- Selected approach
- Decision rationale
- Risks
- Assumptions

**Expected result:** You should have an architecture decision that combines the numerical comparison with business and technical considerations.

---

# Lab 3 — Test Intelligent Model Routing

**Platform:** Microsoft Foundry

## Scenario

Northwind Global Services operates an internal AI platform.

It handles:

- Document classification
- Customer-service summarization
- Sales content
- Complex business analysis
- Internal question answering

The current architecture sends every request to one large model.

The organization wants to test model routing so that different requests can use different models based on workload requirements.

---

## Step 1 — Open the test data

Open:

`Lab_3_Model_Router/Lab_3_Model_Router_Test_Prompts.csv`

The test set contains these workloads:

| ID | Category | Test |
|---|---|---|
| P001 | Classification | Classify a business document |
| P002 | Classification | Classify an X200 customer-support document |
| P003 | Summarization | Summarize a support case |
| P004 | Simple Q&A | Identify information needed for a support case |
| P005 | Complex reasoning | Analyze a three-year financial scenario |
| P006 | Complex reasoning | Evaluate a multi-step business process |
| P007 | Long context | Extract policy requirements |
| P008 | Agent/tool use | Determine whether a support case should be created |

**Expected result:** You should recognize that these requests have different complexity and quality requirements. This is the reason to evaluate intelligent routing.

---

## Step 2 — Open Microsoft Foundry

Sign in to Microsoft Foundry.

Open the **Model Catalog**.

Search for:

```text
model-router
```

Open the model-router capability.

**Expected result:** You should find the model-router capability and its supported configuration options.

---

## Step 3 — Create the model-router deployment

Create a model-router deployment.

Use:

```text
Routing mode: Balanced
```

Keep the default supported model pool unless your environment requires a restricted set.

**Expected result:** The router is configured to select an appropriate underlying model rather than forcing every request to one fixed model.

---

## Step 4 — Open the playground

Open the playground for the model-router deployment.

Keep the configuration consistent while testing the prompt set.

**Expected result:** You have a controlled environment for comparing routing behavior across the same requests.

---

## Step 5 — Test P001

Run:

```text
P001
Classify this document as Customer Service, Sales, Finance, HR,
or Operations. Return only the category.
```

Record:

- Selected underlying model
- Response quality
- Latency
- Estimated cost
- Policy compliance

**Expected result:** The request should be treated as a relatively simple classification workload. Record the actual model selected rather than assuming which model will be used.

---

## Step 6 — Test P002

Run:

```text
Classify this document as Customer Service, Sales, Finance, HR,
or Operations. Return only the category.

Document:
X200 overheating warning reported by a customer.
```

Record the same measurements.

**Expected result:** You can compare two classification requests and observe whether routing behavior changes based on request characteristics.

---

## Step 7 — Test P003 and P004

Run:

```text
P003 — Customer-service summarization
```

and:

```text
P004 — Simple support-case information question
```

Record the selected model, quality, latency, and cost.

**Expected result:** You should begin to see how different business tasks can produce different routing behavior.

---

## Step 8 — Test P005 and P006

Run the complex-reasoning prompts.

P005:

```text
Analyze the following three-year financial scenario,
compare two strategic options, identify assumptions,
and explain the business impact.
```

P006:

```text
Evaluate a multi-step business process redesign involving
cost, risk, compliance, and customer experience.
Provide a structured recommendation with assumptions.
```

Record the same measurements.

**Expected result:** These workloads have greater reasoning requirements than simple classification. Record which underlying model the router actually selects.

---

## Step 9 — Test P007 and P008

Run:

```text
P007 — Long-context policy analysis
P008 — Agent/tool-use decision
```

Record the same measurements.

**Expected result:** You now have results covering classification, summarization, simple Q&A, complex reasoning, long context, and agent/tool scenarios.

---

## Step 10 — Complete the evaluation table

Open:

`Lab_3_Model_Router/Lab_3_Model_Router_Evaluation_Template.csv`

The table contains:

| Field | What to record |
|---|---|
| PromptID | Test prompt ID |
| RoutingMode | Balanced, Cost, or Quality |
| SelectedModel | Actual underlying model |
| QualityScore | Your evaluation score |
| LatencyMs | Observed latency |
| EstimatedCost | Observed/estimated request cost |
| PolicyCompliant | Yes/No |
| Pass | Meets workload requirement |
| Notes | Important observations |

**Expected result:** You have a repeatable record of routing behavior instead of relying on individual observations.

---

## Step 11 — Test Cost routing

Change the model-router configuration to:

```text
Routing mode: Cost
```

Run P001 through P008 again.

Record the same fields.

**Expected result:** The router may favor cost efficiency while still selecting an eligible model for each request. Record the actual behavior.

---

## Step 12 — Test Quality routing

Change the routing mode to:

```text
Routing mode: Quality
```

Run P001 through P008 again.

Record the results.

**Expected result:** You can compare how a quality-oriented routing strategy behaves against Balanced and Cost routing.

---

## Step 13 — Compare routing modes

Compare:

```text
Balanced
Cost
Quality
```

Use these dimensions:

```text
Quality
Cost
Latency
Policy compliance
Selected model
```

**Expected result:** You should be able to identify the trade-offs instead of selecting a routing mode based on cost alone.

---

## Step 14 — Check the quality threshold

Define a minimum acceptable quality threshold for the workload.

Review each test result.

Mark `Pass` only when the result satisfies the required quality and policy conditions.

**Expected result:** A cheaper response should not be considered successful if it fails the business quality requirement.

---

## Step 15 — Review routing telemetry

Open the monitoring/telemetry view for the model-router deployment.

Review:

- Routing distribution
- Underlying model usage
- Request volume
- Latency
- Cost information

**Expected result:** You should see operational evidence of which models are actually receiving traffic.

---

## Step 16 — Evaluate the architecture

Open:

`Lab_3_Model_Router/Lab_3_Model_Router_Test_Procedure.md`

Use the collected results to answer:

- Does routing reduce cost?
- Does quality remain acceptable?
- Does latency improve or worsen?
- Are policy requirements satisfied?
- Are the selected models appropriate for the workloads?
- Does routing provide enough value compared with a fixed-model architecture?

**Expected result:** You should have an evidence-based assessment of whether model routing is appropriate for this workload.

---

# Lab Completion Checklist

## Lab 1 — ROI/TCO

- [ ] Baseline reviewed
- [ ] AI improvement calculated
- [ ] Productivity value calculated
- [ ] TCO reviewed
- [ ] ROI reviewed
- [ ] Scenario sensitivity tested
- [ ] ROI analysis record completed

## Lab 2 — Build/Buy/Extend

- [ ] Requirements reviewed
- [ ] Decision matrix completed
- [ ] Weighted scores calculated
- [ ] Time-to-value sensitivity tested
- [ ] Customization sensitivity tested
- [ ] Build assessed
- [ ] Buy assessed
- [ ] Extend assessed
- [ ] Architecture decision record completed

## Lab 3 — Model Router

- [ ] Test prompts reviewed
- [ ] Model Router deployed
- [ ] Balanced routing tested
- [ ] Cost routing tested
- [ ] Quality routing tested
- [ ] Model selection recorded
- [ ] Quality recorded
- [ ] Latency recorded
- [ ] Cost recorded
- [ ] Policy compliance checked
- [ ] Routing telemetry reviewed
- [ ] Architecture evaluation completed
