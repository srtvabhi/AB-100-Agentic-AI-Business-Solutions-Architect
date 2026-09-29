# Lab 3 Artifact — Supplier Compliance Policy

## Compliance Rules

A supplier certificate is considered current when:

- The certificate type is required for the supplier.
- The expiration date is later than the current review date.
- The supplier identity matches the vendor record.

## Exception Handling

If a certificate is expired:

1. Mark the supplier record for follow-up.
2. Create a procurement task.
3. Notify the procurement owner.
4. Do not automatically approve or reject the supplier.

## Missing Certificate

If the required certificate cannot be found:

1. Create a supplier documentation task.
2. Notify Vendor Management.
3. Keep the final supplier decision with the authorized business process.
