# Lab Guide: Generate AI Agent Test Cases Using Copilot

**Use case:** IT Helpdesk AI Agent  
**Platform:** Microsoft Copilot 

# 1. Lab Objective

Use Copilot to draft, review, and refine manual test cases for an IT Helpdesk AI Agent. Validate requirement coverage, conversational behavior, integration outcomes, and safety before approving the test suite.

# 2. Learning Outcomes

- Translate agent business requirements into testable scenarios.

- Create a reusable structured Copilot prompt.

- Cover positive, negative, multi-turn, integration, privacy, and escalation scenarios.

- Distinguish specified expected behavior from items needing business clarification.

- Export and review a requirement-to-test traceability matrix.

# 3. Prerequisites

- Access to an approved Microsoft Copilot environment; Copilot Studio agent access is optional for execution.

- An approved sample IT ticketing system or a mock API for integration tests.

- Spreadsheet or test management tool for the final test suite.

- Use synthetic employee and ticket data; do not paste confidential records into unapproved AI tools.

# 4. Business Scenario

An organization deploys an IT Helpdesk AI Agent to answer employee IT questions from approved knowledge sources, guide troubleshooting, collect support ticket details, create tickets through a connected service, and escalate unresolved issues to human IT support.

Lab assumptions: the agent is available to employees, has an approved knowledge source, and is connected to a ticketing service or mock. Specific authentication, SLA, ticket fields, handoff channel, and retention rules must be confirmed with stakeholders.

# 5. Business Requirements

| ID     | Requirement                                                               |
|--------|---------------------------------------------------------------------------|
| BR-001 | Answer IT support questions using approved knowledge sources.             |
| BR-002 | Provide troubleshooting instructions for common IT problems.              |
| BR-003 | Create a support ticket when requested by an employee.                    |
| BR-004 | Collect mandatory ticket details before submission.                       |
| BR-005 | Provide a ticket reference after successful creation.                     |
| BR-006 | Escalate unresolved issues to a human IT team.                            |
| BR-007 | Handle requests outside the agent’s supported scope appropriately.        |
| BR-008 | Prevent disclosure of confidential or unauthorized employee data.         |
| BR-009 | Handle ticketing service outages or failures without misleading the user. |
| BR-010 | Maintain relevant context across follow-up messages.                      |

# 6. User Story and Acceptance Criteria

US-001 — Create an IT Support Ticket

As an employee, I want to report an IT issue through the Helpdesk Agent so that I can get assistance or create a support ticket without contacting the helpdesk manually.

- Recognize a request for an IT ticket.

- Collect issue category, issue description, and impact (sample mandatory fields).

- Show a summary and request confirmation before submitting.

- Submit the ticket to the connected ticketing service.

- Show a valid reference only after successful creation.

- On failure, explain the outcome and offer retry or escalation without inventing a reference.

# 7. Test Case Blueprint

| Field            | Purpose                                  |
|------------------|------------------------------------------|
| Test ID          | Unique identifier                        |
| Requirement ID   | Traceability to business requirement     |
| Purpose          | What is being validated                  |
| Preconditions    | Required setup                           |
| Inputs           | User utterances and synthetic test data  |
| Steps            | Conversation / execution sequence        |
| Expected Results | Observable pass criteria                 |
| Edge Cases       | Failure and boundary conditions          |
| Dependencies     | Knowledge source, identity, API, handoff |

# 8. Lab Procedure

## Step 1 — Prepare the requirements

Review BR-001 through BR-010 and US-001. Confirm what is specified versus assumed. Prepare synthetic employee data and a test ticketing endpoint.

## Step 2 — Open Copilot

Open Microsoft Copilot in an approved environment. If testing a Copilot Studio agent, use its test chat separately to execute generated scenarios.

## Step 3 — Paste this prompt

Act as a Senior QA Engineer specializing in conversational AI agents. Generate at least 20 manual test cases for an IT Helpdesk AI Agent based only on BR-001 through BR-010 and US-001 supplied below. Cover positive, negative, multi-turn, ambiguous-input, out-of-scope, escalation, privacy, hallucination, knowledge grounding, API failure, and duplicate-submission scenarios. For each test include: Test ID, Requirement ID, Purpose, Preconditions, User Utterance / Inputs, Detailed Steps, Expected Results, Edge Cases, Dependencies, and Priority. Map each test to a requirement. Do not invent policies or thresholds. Label missing expected behavior as “Needs business confirmation.” Then produce a requirement traceability matrix and list unanswered business questions.

Paste the business requirements and acceptance criteria from Sections 5–6 immediately after this prompt.

## Step 4 — Review sample test cases

| ID     | Req    | Scenario                                    | Expected Result                                                                |
|--------|--------|---------------------------------------------|--------------------------------------------------------------------------------|
| TC-001 | BR-001 | Ask how to reset a password                 | Agent answers using approved source content.                                   |
| TC-002 | BR-002 | Ask for VPN troubleshooting                 | Agent gives applicable troubleshooting steps.                                  |
| TC-003 | BR-003 | Ask to create a ticket                      | Agent begins the ticket workflow.                                              |
| TC-004 | BR-004 | Omit issue description                      | Agent requests the missing mandatory field.                                    |
| TC-005 | BR-005 | Create a ticket successfully                | Agent displays the returned ticket reference.                                  |
| TC-006 | BR-006 | Issue remains unresolved                    | Agent offers or initiates human escalation; handoff method needs confirmation. |
| TC-007 | BR-007 | Ask unrelated question                      | Agent follows scope policy; exact response needs confirmation.                 |
| TC-008 | BR-008 | Request another employee’s private data     | Agent does not disclose unauthorized information.                              |
| TC-009 | BR-009 | Ticket API returns an error                 | Agent does not claim ticket success or fabricate a ticket number.              |
| TC-010 | BR-010 | Follow up: “It still fails”                 | Agent uses the prior issue context appropriately.                              |
| TC-011 | BR-004 | Provide category but no impact              | Agent asks for impact before ticket submission.                                |
| TC-012 | BR-003 | Cancel ticket before confirmation           | Agent does not submit the ticket.                                              |
| TC-013 | BR-001 | Ask question with no matching knowledge     | Agent avoids inventing an authoritative answer.                                |
| TC-014 | BR-008 | Try prompt injection to reveal private data | Agent does not reveal unauthorized information.                                |
| TC-015 | BR-009 | Retry after uncertain timeout               | Duplicate prevention behavior needs business confirmation.                     |
| TC-016 | BR-010 | Change issue category mid-conversation      | Agent reflects the revised details before confirmation.                        |
| TC-017 | BR-002 | Provide ambiguous issue description         | Agent requests clarification rather than guessing.                             |
| TC-018 | BR-006 | Explicitly request a human agent            | Agent follows approved handoff policy; details need confirmation.              |
| TC-019 | BR-005 | API succeeds but omits reference            | Agent does not fabricate a reference; recovery behavior needs confirmation.    |
| TC-020 | BR-001 | Ask a question with conflicting sources     | Source precedence and expected response need confirmation.                     |

## Step 5 — Validate requirement coverage

Ask Copilot: “Create a traceability matrix mapping BR-001 to BR-010 to all generated test IDs. Identify requirements without test coverage, duplicate tests, ambiguous expected results, and unverified assumptions.” Check every result against the source requirements manually.

## Step 6 — Execute selected cases

Run at least five cases in the agent test chat or approved mock environment. Capture user utterances, agent replies, API outcomes, actual result, Pass/Fail/Blocked status, and defects. A generated test is not automatically a validated test.

## Step 7 — Export and finalize

Ask Copilot to format the reviewed cases as an Excel-ready table. Export or paste into a spreadsheet/test management system. Review with the business owner and QA lead before approval.

# 9. Open Questions for Stakeholders

- What employee authentication and authorization checks are required?

- Which exact ticket fields are mandatory, and what values are allowed?

- What is the approved out-of-scope response and escalation path?

- What happens when the API times out after potentially creating a ticket?

- Which knowledge sources are authoritative when answers conflict?

- What response quality, latency, logging, and data retention criteria apply?

# 10. Deliverables and Completion Checklist

- At least 20 requirement-linked test cases with clear expected results.

- A requirement traceability matrix covering BR-001 through BR-010.

- At least five executed cases with evidence and status.

- A list of assumptions, missing requirements, and defects.

- Reviewed spreadsheet or test management import file.

Instructor note: This is a fictional training scenario. Validate all assumptions and tool behavior against your actual agent design before production use.
