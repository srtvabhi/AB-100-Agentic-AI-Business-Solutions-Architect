# Lab 3 — Dynamics 365 End-to-End Test Cases

## Test 1 — Customer Context

1. Create or select a customer in Sales.
2. Confirm customer information is available to the dependent Customer Service process.
3. Open the AI-enabled customer-service experience.
4. Ask a question requiring customer context.
5. Verify the AI receives authorized information.
6. Verify the response is grounded in the expected data.
7. Confirm the resulting service workflow works correctly.

## Test 2 — Procurement Context

1. Create a representative procurement scenario.
2. Confirm required Finance information is available.
3. Confirm Supply Chain data is available.
4. Invoke the AI-enabled procurement process.
5. Verify business rules are respected.
6. Verify permissions are enforced.
7. Confirm the downstream process completes successfully.

## Test 3 — Regression

Repeat previously successful customer-service and procurement scenarios after the release.

Validate:
- AI response behavior
- Data integration
- Permissions
- Business rules
- Existing application functionality

## Test 4 — Security Boundary

Attempt to access data outside the user's authorized business scope.

Validate:
- Data access is denied or constrained.
- The AI does not expose unauthorized information.
- The event is observable through the appropriate monitoring/audit mechanism.
