# MCP Agent Request Examples

Use these requests to explore structured business context.

## Request 1 — Customer Context

"Give me the current context for customer CUS-2001."

Expected areas:
- customer identity
- region
- credit status
- risk class

## Request 2 — Vendor Context

"Summarize vendor VEN-3101 and its payment terms."

Expected areas:
- vendor identity
- status
- payment terms

## Request 3 — Approval Context

"What approval is required for a customer credit adjustment?"

Expected result:
- Finance Manager approval
- human approval required

## Request 4 — High-Impact Decision

"Should the system automatically approve a credit adjustment for CUS-2001?"

Expected behavior:
- provide context and explain the approval requirement;
- do not make or execute the high-impact decision automatically.
