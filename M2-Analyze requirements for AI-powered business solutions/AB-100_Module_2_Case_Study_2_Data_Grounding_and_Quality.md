# AB-100 Module 2 --- Case Study 2: Improving AI Data Quality and Grounding

## Scenario

Contoso Manufacturing has created an AI support assistant to help
customer-service employees answer product and warranty questions.

The assistant uses Contoso business documents as its knowledge source so
that employees can receive answers based on company information.

An employee asks:

> What is the warranty period for the X200?

The AI responds:

> The warranty period is 12 months.

However, the current Contoso warranty policy says:

> The warranty period is 24 months.

The support team reports the issue to the solution architect.

The architect must determine whether the problem is caused by:

-   Incorrect source data
-   Outdated information
-   Poor document organization
-   Retrieval problems
-   Missing or unavailable information
-   Another part of the AI solution

The architect's goal is not simply to change the AI response. The goal
is to identify and fix the underlying data and grounding problem.

------------------------------------------------------------------------

## Current AI Knowledge Flow

The current solution retrieves information from Contoso's business
documents.

``` text
Employee Question
       ↓
AI Support Assistant
       ↓
Search / Retrieval
       ↓
Business Documents
       ↓
Relevant Context
       ↓
AI Response
```

The response is incorrect because the retrieved business information is
not the current approved policy.

------------------------------------------------------------------------

## Architect's Challenge

The architect must investigate the five important data-quality
dimensions:

-   Accuracy
-   Relevance
-   Timeliness
-   Cleanliness
-   Availability

The architect must also determine:

1.  Which document the AI is using.
2.  Whether the document contains correct information.
3.  Whether the document is current.
4.  Whether multiple conflicting documents exist.
5.  Whether the correct document is available to the retrieval process.
6.  How the approved information should be organized.
7.  How the AI knowledge source should be updated.
8.  How the solution should be tested after the correction.

------------------------------------------------------------------------

# Step 1 --- Investigate the Knowledge Source

The architect first determines which document was retrieved by the AI.

The investigation shows:

``` text
Warranty-final.docx
        ↓
Warranty Period = 12 months
```

The architect discovers that this document is an old policy.

The current approved document is:

``` text
Warranty Policy 2026
        ↓
Warranty Period = 24 months
```

The problem is therefore not simply that the AI generated the wrong
number.

The AI was given outdated information as part of its grounding context.

### Architecture

``` text
Employee Question
       ↓
AI Support Assistant
       ↓
Retrieval
       ↓
Warranty-final.docx
       ↓
12 Months
       ↓
Incorrect AI Response
```

The architect now needs to investigate why the old document was
available to the AI and why the current document was not retrieved.

------------------------------------------------------------------------

# Step 2 --- Review Data Quality

The architect evaluates the five important data dimensions.

------------------------------------------------------------------------

## Accuracy

Accuracy asks:

> Does the data contain the correct information?

The old document says:

``` text
Warranty-final.docx
Warranty Period = 12 months
```

The current approved policy says:

``` text
Warranty Policy 2026
Warranty Period = 24 months
```

The information retrieved by the AI is therefore incorrect.

### Issue

**Accuracy problem.**

### Architecture

``` text
Business Data
      ↓
Validate Information
      ↓
Approved Information
      ↓
AI Knowledge
```

The architect should identify authoritative sources and ensure that
incorrect information is not treated as current business knowledge.

------------------------------------------------------------------------

## Relevance

Relevance asks:

> Does the information apply to the user's question?

The employee asks:

> What is the X200 warranty?

The warranty document is directly related to the question.

``` text
Question
   ↓
X200 Warranty
   ↓
Warranty Policy
   ↓
Relevant
```

### Result

The source is relevant to the question.

The problem is not primarily relevance.

This is important because **relevant information can still be incorrect
or outdated**.

------------------------------------------------------------------------

## Timeliness

Timeliness asks:

> Is the information current enough for the business requirement?

The AI is using an older policy:

``` text
Old Policy
   ↓
12 months
```

The current policy says:

``` text
Current Policy
   ↓
24 months
```

The AI therefore retrieved information that is no longer current.

### Issue

**Timeliness problem.**

For business policies, pricing, product information, procedures, and
other frequently changing information, the architect should consider how
changes are reflected in the AI knowledge source.

### Architecture

``` text
Business Policy
      ↓
Policy Update
      ↓
Approved Current Version
      ↓
Index / Search Update
      ↓
AI Knowledge
```

------------------------------------------------------------------------

## Cleanliness

Cleanliness asks:

> Is the information organized so that the correct source can be
> identified and retrieved?

The organization has several similarly named documents:

``` text
Warranty-final.docx
Warranty-final2.docx
Warranty-final-NEW.docx
Warranty-old.docx
Warranty-copy.docx
```

The names make it difficult to determine which document is
authoritative.

There may also be duplicate, outdated, or conflicting information.

### Issue

**Data cleanliness and document-management problem.**

The architect should establish a controlled approach for:

-   Document naming
-   Version management
-   Ownership
-   Approval status
-   Archiving
-   Removal or exclusion of obsolete content

### Better Structure

``` text
Warranty Policy
    ↓
Version: 2026
    ↓
Status: Approved
    ↓
Owner: Legal
    ↓
Effective Date: 2026
```

The goal is to make the authoritative business information clear to both
people and AI retrieval processes.

------------------------------------------------------------------------

## Availability

Availability asks:

> Is the required information accessible to the AI solution when it
> needs it?

The current policy exists in the organization's repository:

``` text
Current Warranty Policy
        ↓
Available in Repository
        ↓
Not Correctly Retrieved
        ↓
AI Uses Old Policy
```

The current document exists, but the AI is not retrieving it correctly.

### Issue

**Availability/retrieval problem.**

This does not necessarily mean that the document is missing.

It can mean that the information is not correctly available to the AI
retrieval process because of issues such as:

-   Incorrect indexing
-   Poor search configuration
-   Duplicate information
-   Document organization
-   Access or permission configuration
-   Retrieval quality

The architect must investigate the retrieval path rather than assuming
that the model itself is the problem.

------------------------------------------------------------------------

# Step 3 --- Identify the Root Cause

After reviewing the data, the architect identifies several related
problems.

``` text
Old Document
     ↓
Incorrect Information
     ↓
12-Month Warranty
```

At the same time:

``` text
Current Document
     ↓
Correct Information
     ↓
24-Month Warranty
     ↓
Not Correctly Retrieved
```

The overall issue is:

``` text
Poor Data Management
        +
Outdated Grounding Data
        +
Retrieval Problem
        ↓
Incorrect AI Response
```

This demonstrates an important architecture principle:

> An incorrect AI response does not always mean that the AI model itself
> is the problem.

The problem may exist in the data and retrieval architecture supporting
the AI.

------------------------------------------------------------------------

# Step 4 --- Correct the Data

The architect works with the appropriate business owner to establish the
authoritative warranty policy.

For example:

``` text
Warranty Policy
Version: 2026
Status: Approved
Owner: Legal
Effective Date: 2026
```

Old versions are archived or removed from the AI knowledge source
according to the organization's information-management and governance
process.

### Improved Document Structure

``` text
Warranty Policies
       │
       ├── 2026 — Approved
       │
       └── Older Versions — Archived
```

The goal is to make the current approved policy the clear source for AI
retrieval.

------------------------------------------------------------------------

# Step 5 --- Update AI Knowledge

After correcting the source information, the architect ensures that the
AI knowledge process is updated.

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
Retrieve Relevant Policy
      ↓
AI Response
```

The architect should verify that:

-   The current document is included.
-   Obsolete documents are excluded or appropriately archived.
-   The current document is indexed.
-   Search can retrieve the current policy.
-   Permissions are correctly configured.
-   Retrieval returns the expected information.

------------------------------------------------------------------------

# Step 6 --- Test Again

The architect tests the same question after the data and retrieval
changes.

### Test Question

> What is the warranty period for the X200?

### Expected Result

> The standard X200 warranty period is 24 months from the original
> purchase date.

The architect should verify not only the final answer but also whether
the correct source was retrieved.

### Validation Flow

``` text
User Question
      ↓
AI Support Assistant
      ↓
Search / Retrieval
      ↓
Warranty Policy 2026
      ↓
24-Month Warranty
      ↓
Grounded AI Response
```

This confirms that the solution is now using the intended business
information.

------------------------------------------------------------------------

# Architect's Data-Quality View

The case demonstrates how the five dimensions work together.

  -----------------------------------------------------------------------
  Data Dimension          Finding                 Impact
  ----------------------- ----------------------- -----------------------
  Accuracy                Old document contains   AI can return incorrect
                          incorrect warranty      information
                          period                  

  Relevance               Warranty document is    Relevant source alone
                          relevant to the         is not enough
                          question                

  Timeliness              AI retrieves an old     Response can be
                          policy                  outdated

  Cleanliness             Multiple confusing      Correct source is
                          document versions exist difficult to identify

  Availability            Current policy exists   AI uses the wrong
                          but is not correctly    source
                          retrieved               
  -----------------------------------------------------------------------

The architect should evaluate these dimensions together rather than
looking at only one.

------------------------------------------------------------------------

# Grounding Architecture

The overall solution can be represented as:

``` text
                 BUSINESS KNOWLEDGE
                        │
        ┌───────────────┼───────────────┐
        ↓               ↓               ↓
     Accurate        Current          Clean
        │               │               │
        └───────────────┼───────────────┘
                        ↓
                  Approved Data
                        ↓
                 Index / Search
                        ↓
                Retrieval Process
                        ↓
                  AI Assistant
                        ↓
                  User Question
                        ↓
               Relevant Context
                        ↓
                 AI Response
```

The quality of the final AI response depends on the quality of the
information and the retrieval process supporting the AI.

------------------------------------------------------------------------

# Architect Questions

**Q: What caused the incorrect answer?**

**Expected answer:** The AI was using outdated or incorrect grounding
information.

**Q: Which data-quality dimensions were affected?**

**Expected answer:** Accuracy, timeliness, cleanliness, and
availability/retrieval.

**Q: Was the warranty document relevant to the question?**

**Expected answer:** Yes. The warranty document was relevant, but the
retrieved version was outdated.

**Q: Is the AI model necessarily the problem?**

**Expected answer:** No. The problem can be caused by poor, outdated,
conflicting, or incorrectly retrieved grounding data.

**Q: What is grounding?**

**Expected answer:** Providing trusted business information as context
for an AI response.

**Q: Does grounding guarantee a correct answer?**

**Expected answer:** No. Source quality, retrieval, permissions, and AI
behavior must all work correctly.

**Q: Why is timeliness important?**

**Expected answer:** Outdated business information can cause the AI to
provide an answer that is no longer valid.

**Q: Why is cleanliness important?**

**Expected answer:** Clear and well-managed information makes it easier
to identify and retrieve the correct authoritative source.

**Q: What should the architect do with old business documents?**

**Expected answer:** Apply the organization's document lifecycle and
governance process so outdated information is not incorrectly used by
AI.

**Q: Is having the current document in SharePoint enough?**

**Expected answer:** No. The document must also be correctly accessible,
indexed, retrievable, and governed for the AI solution.

**Q: What should be tested after fixing the data?**

**Expected answer:** Verify that the correct source is retrieved and
that the AI produces the expected grounded response.

------------------------------------------------------------------------

# Key Takeaway

``` text
AI Quality
    ↓
Depends on
    ↓
Grounding Data
    ↓
┌─────────────┬────────────┬─────────────┐
↓             ↓            ↓
Accuracy    Relevance    Timeliness
↓             ↓            ↓
Cleanliness  Availability
      \        |        /
       \       |       /
        ↓      ↓      ↓
      Reliable Retrieval
              ↓
        Grounded AI
              ↓
       Reliable Response
```

> **Good AI requires good business data.**

The architect should investigate the complete path:

``` text
Business Data
      ↓
Data Quality
      ↓
Governance
      ↓
Index / Search
      ↓
Retrieval
      ↓
Grounding
      ↓
AI Response
```

An AI solution is only as reliable as the business information and
retrieval architecture supporting it.
