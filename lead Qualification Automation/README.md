# Lead Qualification & Management Report Automation

## Overview

This automation processes a batch of CRM leads, validates each record, enriches valid leads with business metadata, generates a management report, and sends the report to Discord.

The workflow demonstrates a typical automation engineering pattern involving validation, branching, enrichment, merging, aggregation, and reporting.

---

## Business Scenario

A marketing agency exports new leads from its CRM every morning.

Before assigning leads to the sales team, the agency wants to:

- reject incomplete or invalid leads
- categorize valid leads
- assign business priority
- generate a daily management report

---

## Business Requirements

- Validate every lead
- Reject leads with:
  - missing name
  - missing company
  - invalid email
- Assign Region from Country
- Assign Priority from Region
- Produce one daily report
- Send report to Discord

---

## Workflow

Webhook
↓
Split Out
↓
Lead Validation (JavaScript)
↓
IF
├───────────────┐
│               │
Valid        Rejected
│               │
Region &        │
Priority        │
Assignment      │
│               │
└───────Merge───┘
↓
Aggregate
↓
Generate Report
↓
Discord

---

## Sample Input

```json
[
  {
    "name":"John Smith",
    "email":"john.smith@acme.com",
    "company":"Acme Ltd",
    "country":"USA"
  }
]
```

---

## Sample Output

```text
📊 Daily Lead Qualification Report

Qualified: 8
Rejected: 2
High Priority: 3
```

---

## Engineering Concepts

### Validation Layer

Business validation is separated from routing.

The validation stage computes:

- valid email
- valid company
- valid name
- rejection reason

without filtering data.

---

### Data Enrichment

Valid leads are enriched with:

- Region
- Priority
- Status

instead of replacing existing data.

---

### Branching

The workflow routes leads into:

- Qualified
- Rejected

using an IF node.

---

### Merge Pattern

After independent processing, both branches are merged into a single stream before reporting.

---

### Fan-In Aggregation

Aggregate converts multiple workflow items into one collection, enabling generation of a single management report.

---

## Tech Stack

- n8n
- JavaScript
- Discord Webhook

---

## Possible Improvements

- Real email verification API
- CRM integration
- Database storage
- Pagination for large datasets
- Retry and error handling
- Scheduled execution 