# Lab: Create Your First Computer-Using Agent in Copilot Studio

## Lab Objective

In this lab, you will create a Computer-Using Agent that automatically enters inventory records into the Adventure Inventory application using the Computer Use capability.

---

# Step 1: Create a Computer-Using Agent

1. Open **Microsoft Copilot Studio**.
2. From the **Home** page, select **Computer-using agent**.
3. In the **Name your agent** dialog box, enter:

```text
Adventure Inventory Agent
```

4. Click **Create**.

---

# Step 2: Configure Computer Use Instructions

On the **New computer use** screen, locate the **Instructions** section.

Paste the following instructions:

```text
Go to https://computerusedemos.blob.core.windows.net/web/Adventure/index.html

Submit a new entry for each of the following items.

Rear Derailleur, RD-4481, 50, 42.75, Tailspin Toys

Pedal Set, PD-1738, 80, 19.99, Northwind Traders

Brake Lever, BL-2975, 35, 14.50, Trey Research

Chainring Bolt Set, CB-5640, 100, 5.25, VanArsdel, Ltd.

Bottom Bracket, BB-9320, 60, 24.90, Tailwind Traders

After entering each item, save the record.

Verify the record appears in the inventory list before proceeding to the next item.

Continue until all items have been successfully entered.

Return a summary when finished.
```

5. Click **Add and configure**.

---

# Step 3: Configure Tool Details

## Name

```text
Adventure Inventory Entry
```

## Description

```text
Submits inventory records to the Adventure inventory application using computer use.
```

## Model

Leave the default model selected:

```text
Claude Sonnet 4.5
```

---

# Step 4: Refine Computer Use Instructions

Replace the instructions with the following optimized version:

```text
1. Open https://computerusedemos.blob.core.windows.net/web/Adventure/index.html

2. Create inventory records using the supplied product information.

3. Fill every required field.

4. Click Save after each record.

5. Confirm the product appears in the inventory table.

6. Continue until all products have been entered.

7. Return a summary of all created records.
```

---

# Step 5: Configure Outputs

Under **Outputs**, choose:

```text
Text
```

This option returns a readable summary of the completed operation.

---

# Step 6: Configure Machine

Under **Machine**, select:

```text
Hosted browser
```

### Why Hosted Browser?

- The application is publicly accessible.
- No desktop application is involved.
- No machine installation is required.

---

# Step 7: Configure Credentials

Under **Credentials to use**, select:

```text
Maker-provided credentials
```

Since the Adventure Inventory site does not require authentication, no additional configuration is needed.

---

# Step 8: Configure Human Supervision

Keep the default reviewer:

```text
abhishek@cloudthat.com
```

Notification method:

```text
Outlook
```

This allows the agent to request assistance if needed.

---

# Step 9: Configure Stored Credentials

No action required.

Leave **Stored credentials** empty because the application does not require sign-in.

---

# Step 10: Configure Access Control

Enable:

```text
Only allow specific websites and desktop apps
```

Add the following website:

```text
computerusedemos.blob.core.windows.net
```

This restricts the agent to approved websites only.

---

# Step 11: Enable HTTPS Enforcement

Turn on:

```text
Enforce HTTPS
```

This ensures the agent interacts only with secure websites.

---

# Step 12: Save the Agent

Click:

```text
Save
```

---

# Step 13: Test the Agent

Select:

```text
Open the Adventure Inventory application at https://computerusedemos.blob.core.windows.net/web/Adventure/index.html.

Create the following inventory records:

1. Rear Derailleur, RD-4481, Quantity 50, Price 42.75, Supplier Tailspin Toys

2. Pedal Set, PD-1738, Quantity 80, Price 19.99, Supplier Northwind Traders

3. Brake Lever, BL-2975, Quantity 35, Price 14.50, Supplier Trey Research

4. Chainring Bolt Set, CB-5640, Quantity 100, Price 5.25, Supplier VanArsdel, Ltd.

5. Bottom Bracket, BB-9320, Quantity 60, Price 24.90, Supplier Tailwind Traders

Submit each record individually. Verify that each entry is successfully saved before proceeding to the next record. After all entries are completed, provide a summary of the inventory items entered.
```

The hosted browser opens automatically and begins executing the instructions.

---

# Expected Execution Flow

```text
Browser Launches
        ↓
Adventure Inventory Site Opens
        ↓
Record 1 Created
        ↓
Record 1 Verified
        ↓
Record 2 Created
        ↓
Record 2 Verified
        ↓
Record 3 Created
        ↓
Record 3 Verified
        ↓
Record 4 Created
        ↓
Record 4 Verified
        ↓
Record 5 Created
        ↓
Record 5 Verified
        ↓
Summary Generated
```

---

# Expected Output

```text
Inventory update completed.

Products added:

- Rear Derailleur (RD-4481)
- Pedal Set (PD-1738)
- Brake Lever (BL-2975)
- Chainring Bolt Set (CB-5640)
- Bottom Bracket (BB-9320)

Total records added: 5
```

---

# Knowledge Check

### What is Computer Use?

Computer Use enables an AI agent to interact with applications and websites using:

- Mouse clicks
- Keyboard input
- Form submissions
- Screen understanding
- Website navigation

---

### When should you use Computer Use?

Use Computer Use when:

✅ No API is available

✅ No connector exists

✅ Legacy applications must be automated

✅ User interface interaction is required

---

### Typical Business Scenarios

- SAP legacy systems
- Procurement portals
- HR applications
- Finance systems
- Vendor onboarding portals
- Internal web applications

---

# Lab Outcome

By completing this lab, participants will learn how to:

- Create a Computer-Using Agent
- Configure a hosted browser
- Write Computer Use instructions
- Automate web-based data entry tasks
- Secure agent access using Access Control
- Test and validate Computer Use automations
- Understand when to choose Computer Use over APIs or connectors
