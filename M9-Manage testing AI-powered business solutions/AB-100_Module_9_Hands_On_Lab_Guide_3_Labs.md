# AB-100 Module 9 — Hands-On Lab Guide

## Lab 1 — Build and Run an AI Agent Evaluation Test Set

### Platform
Microsoft Copilot Studio

### Steps
1. Open Microsoft Copilot Studio.
2. Open an existing test agent or create a customer-service test agent.
3. Add the knowledge source used by the agent.
4. Save the agent.
5. Open **Evaluate**.
6. Create a new evaluation/test set.
7. Import `Lab1_Copilot_Studio_Test_Set.csv`.
8. Review the imported test cases.
9. Configure **General quality** evaluation.
10. Add safety/content-safety evaluation where supported.
11. Save the evaluation.
12. Run the evaluation.
13. Review the aggregate result.
14. Open failed test cases.
15. Classify each failure as prompt, knowledge, routing, tool/action, guardrail, or test-data issue.
16. Use `Lab1_Copilot_Studio_Evaluation_Criteria.md`.
17. Change one agent instruction or knowledge configuration.
18. Save the agent.
19. Re-run the same evaluation.
20. Compare the new run with the previous run.
21. Keep the original test set as the regression baseline.

## Lab 2 — Validate a Custom AI Model

### Platform
Microsoft Foundry

### Steps
1. Open the Microsoft Foundry portal.
2. Open an existing project.
3. Open the evaluation capability.
4. Prepare `Lab2_Custom_Model_Validation_Dataset.csv`.
5. Review query, ground truth, context, and acceptance criteria.
6. Convert the CSV to the dataset format requested by the evaluation experience if required.
7. Select the model or endpoint to evaluate.
8. Create the evaluation dataset.
9. Add relevant quality evaluators such as relevance, groundedness, or similarity where available.
10. Add risk/safety evaluators where required.
11. Apply `Lab2_Custom_Model_Validation_Criteria.md`.
12. Run the evaluation.
13. Review aggregate results.
14. Review row-level failures.
15. Check the missing-PO and incomplete-document cases.
16. Record each failure category.
17. Compare results with business acceptance thresholds.
18. Record required mitigation for failed criteria.
19. Re-run after model, prompt, data, or configuration changes.
20. Compare the new run with the baseline.
21. Record the final validation status.

## Lab 3 — Design End-to-End Dynamics 365 Test Cases with Copilot

### Platform
Dynamics 365 Sales + Dynamics 365 Customer Service + Copilot

### Steps
1. Open the available Dynamics 365 Sales environment.
2. Open the available Dynamics 365 Customer Service environment.
3. Identify a test customer and test order.
4. Confirm the test user's permissions.
5. Open `Lab3_D365_End_to_End_Test_Scenarios.csv`.
6. Execute the customer-identification scenario.
7. Record the resolved customer.
8. Execute the order-review scenario.
9. Record the order status.
10. Submit the order-delay question to the available Copilot/AI experience.
11. Verify the response uses the correct customer and order context.
12. Record the actual response and business outcome.
13. Test the missing-order scenario.
14. Verify clarification or the configured exception path.
15. Test the unauthorized-approval scenario.
16. Verify that no unauthorized capability is claimed.
17. Open Copilot.
18. Open `Lab3_Copilot_Test_Case_Blueprint.md`.
19. Submit the blueprint and business-process requirements.
20. Generate end-to-end test cases.
21. Review every generated test case.
22. Remove invented capabilities, data, or dependencies.
23. Add missing integration, security, error-handling, and business-outcome checks.
24. Map generated tests to `Lab3_D365_End_to_End_Test_Scenarios.csv`.
25. Execute the highest-priority cases.
26. Record actual results against expected results.
27. Change a prompt or configuration.
28. Re-run the same cases.
29. Compare the new results with the baseline.
30. Keep the validated cases as the regression set.
