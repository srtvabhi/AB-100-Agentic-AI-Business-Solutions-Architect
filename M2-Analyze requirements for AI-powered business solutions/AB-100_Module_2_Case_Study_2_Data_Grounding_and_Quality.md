# AB-100 Module 2 --- Case Study 2: Data Grounding and Quality

## Scenario

Contoso has created an AI support assistant.

Employees ask:

> What is the warranty period for the X200?

The AI responds:

> The warranty period is 12 months.

However, the current Contoso warranty policy says:

> The warranty period is 24 months.

The architect must determine why the AI provided the wrong answer.

------------------------------------------------------------------------

## Step 1 --- Investigate the Knowledge Source

The architect discovers that the AI is using:

``` text
Warranty-final.docx
        ↓
Warranty Period = 12 months
```

The document is an old policy.

The current document is:

``` text
Warranty Policy 2026
        ↓
Warranty Period = 24 months
```

------------------------------------------------------------------------

## Step 2 --- Review Data Quality

The architect evaluates the five important data dimensions.

### Accuracy

The old document contains incorrect information.

``` text
Old:
12 months

Current:
24 months
```

**Issue:** Accuracy problem.

------------------------------------------------------------------------

### Relevance

The warranty document is relevant to the user's question.

``` text
Question:
What is the X200 warranty?

Warranty Policy:
Relevant
```

**Result:** Relevance is acceptable.

------------------------------------------------------------------------

### Timeliness

The AI is using an outdated policy.

``` text
Old Policy
   ↓
12 months

Current Policy
   ↓
24 months
```

**Issue:** Timeliness problem.

------------------------------------------------------------------------

### Cleanliness

The organization has several documents:

``` text
Warranty-final.docx
Warranty-final2.docx
Warranty-final-NEW.docx
Warranty-old.docx
Warranty-copy.docx
```

The architect cannot easily determine which document is authoritative.

**Issue:** Data cleanliness and document management problem.

------------------------------------------------------------------------

### Availability

The current policy exists but is not being retrieved by the AI.

``` text
Current Policy
      ↓
Available in repository
      ↓
Not correctly retrieved
      ↓
AI uses old policy
```

**Issue:** Data availability/retrieval problem.

------------------------------------------------------------------------

## Step 3 --- Correct the Data

The architect creates a controlled knowledge structure.

``` text
Warranty Policy
Version: 2026
Status: Approved
Owner: Legal
Effective Date: 2026
```

Old versions are archived or removed from the AI knowledge source
according to the organization's information-management process.

------------------------------------------------------------------------

## Step 4 --- Update AI Knowledge

``` text
Approved Policy
      ↓
Clean / Organize
      ↓
Index / Search
      ↓
AI Knowledge
      ↓
User Question
      ↓
Relevant Policy
      ↓
AI Response
```

------------------------------------------------------------------------

## Step 5 --- Test Again

Ask:

> What is the warranty period for the X200?

Expected result:

> The standard X200 warranty period is 24 months from the original
> purchase date.

------------------------------------------------------------------------

## Architect Questions

**Q: What caused the incorrect answer?**

**Expected answer:** The AI was using outdated or incorrect grounding
information.

**Q: Which data-quality dimensions were affected?**

**Expected answer:** Accuracy, timeliness, cleanliness, and
retrieval/availability.

**Q: Is the AI model necessarily the problem?**

**Expected answer:** No. The problem can be caused by poor or outdated
grounding data.

**Q: What is grounding?**

**Expected answer:** Providing trusted business information as context
for the AI response.

**Q: Does grounding guarantee a correct answer?**

**Expected answer:** No. The source data, retrieval process,
permissions, and AI behavior must all work correctly.

**Q: What should the architect do with old business documents?**

**Expected answer:** Apply the organization's document lifecycle and
governance process so outdated information is not incorrectly used by
AI.

------------------------------------------------------------------------

## Key Takeaway

``` text
AI Quality
    ↓
Depends on
    ↓
Grounding Data
    ↓
Accuracy
Relevance
Timeliness
Cleanliness
Availability
    ↓
Reliable AI Response
```

> **Good AI requires good business data.**
