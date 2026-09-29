# Agent Flow Requirements

## Flow Name
Case Escalation Flow

## Trigger
The agent calls the flow with:
- CaseId
- Priority
- Customer

## Rules
- If Priority is High, create an escalation record.
- If Priority is not High, return "No escalation required."
- Return the result to the agent in real time.

## Response
Return:
- CaseId
- Escalated: Yes/No
- Message
