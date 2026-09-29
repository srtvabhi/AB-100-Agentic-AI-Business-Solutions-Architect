# Lab 1 Artifact — F&O Procurement Knowledge

## Procurement Procedure

### Purchase Order Delay Procedure

1. Check the purchase order status in Dynamics 365 Finance.
2. Check workflow history and pending approvals.
3. Check supplier status.
4. Check related supply-chain exceptions.
5. If an approval is pending, identify the responsible role.
6. Do not approve a purchase order on behalf of another role.
7. Escalate unresolved exceptions to Procurement Operations.

### Supplier Escalation Rules

- Blocked supplier: escalate to Vendor Management.
- Missing approval: escalate to the responsible approver.
- Supply exception: escalate to Supply Chain Operations.
- Missing documentation: create a supplier follow-up task.

### Required Response Fields

When summarizing a purchase-order issue, include:

- Purchase order
- Supplier
- Current status
- Blocking condition
- Responsible role
- Recommended next step
