# 📊 Analyst Interview Guide — Master Edition

> A department-by-department field guide for data analysts conducting stakeholder interviews. Built to help you stop doing discovery and start doing design — because you already know the data.

---

## What This Is

A structured, interactive interview guide for analysts embedded in mid-market and enterprise companies. Every question is written assuming you've already pulled the tables, reviewed the schema, and know more about the data than the person you're meeting with.

The goal isn't discovery. It's alignment — confirming that your understanding of the data matches their understanding of the business, then designing self-service tools they can actually run themselves.

---

## Departments Covered

| Department | Focus |
|---|---|
| ⚠️ Before Every Interview | Prep framework — how to walk in ready |
| 🗂 Data Engineer / Project Manager | Architecture, access, deployment constraints |
| 📈 Sales (Inside & Outside) | Pipeline, rep performance, forecast, territory |
| 🧾 Accounts Receivable | Aging, collections workflow, dispute logic |
| 💳 Accounts Payable | Payment calendar, vendor holds, discount capture |
| 📦 Procurement | Vendor scorecards, spend analysis, PO logic |
| 🏭 Warehouse / Operations | Inventory accuracy, transfers, available-to-pick |
| 💰 Finance / CFO | Close process, revenue recognition, margin definitions |
| 📣 Marketing | Attribution, campaign-to-revenue, channel comparison |
| 🖥 IT | Access provisioning, schema changes, support model |

---

## Core Philosophy

**You already know the data. You don't know how they think about it.**

Every question in this guide is designed to surface one of three things:

1. **A business rule** that changes how a metric should be calculated
2. **A workflow** that reveals what the self-service tool actually needs to do
3. **A trust gap** that must be closed before any dashboard gets adopted

### The Four Follow-Up Questions

When someone says *"I just need to know X"* — ask:

> How often? For which time period? Filtered by what? Compared to what?

Vague requests produce vague dashboards. These four questions turn a request into a specification.

---

## Before Every Interview

Pull their primary tables before the meeting. Write down three things about their data that don't make business sense yet. Ask about them directly.

**Frame the conversation correctly:**

> *"I already have a good picture of your data. I'm here to make sure I understand your business well enough to build something you can actually run yourself."*

Ask them to bring:
- One report they run every week
- One they always have to ask someone else for
- One they wish existed

Three reports. Three different conversations: automate the first, build the second, design the third together.

---

## Power Question — Close Every Interview With This

> *"If you could open one screen tomorrow morning — built exactly the way you'd want it — and it showed you everything you needed to make your best decision of the day, what would be on it?"*

**Follow-up if the answer is vague:**

> *"What would the rows be? What would the columns be? What date range would you set first? What would you filter by? What number, if it was red instead of green, would change what you do today?"*

---

## Golden Rules

| Situation | Ask This |
|---|---|
| They describe a report they want | *"If you could build that yourself with a few clicks, what would the rows and columns be?"* |
| They say "I just need to know X" | *"How often, for which time period, filtered by what, and compared to what?"* |
| They say "the numbers are always wrong" | *"Can you show me one specific example, and what the right number should be?"* |
| They describe a manual process | *"What would have to be true in the data for you to never have to do that manually again?"* |
| End of every interview | *"What question did you expect me to ask that I didn't?"* |

---

## Department Highlights

### 📈 Sales
- Ask inside sales which CRM fields reps actually fill in consistently — you already know the answer, but confirming tells you whether it's a training problem, a process problem, or a field design problem.
- Stage definitions are almost always informal. You need the real definition to build pipeline metrics that mean something.
- Forecast methodology tells you whether pipeline data is clean enough to automate, or whether it needs cleanup first.

### 🧾 Accounts Receivable
- Confirm aging logic directly: *"When you say a customer is 30 days past due — does that mean 30 days past invoice date or 30 days past their due date?"*
- Disputed invoices in aging create false urgency in collections. You need their rule to build the filter correctly.
- Exception customers — do not call, legal hold, payment arrangements — need to be in the data and the dashboard.

### 💳 Accounts Payable
- Early payment discount capture is a direct ROI calculation. If it's manual today, you can automate the alert.
- Recurring payments should be filterable in self-service views so they don't distort exception analysis.

### 📦 Procurement
- Vendor scorecard weighting is a business decision. You can build the scorecard — they need to own the weights.
- Confirm the definition of "on time" before writing the query. You have `expected_delivery` and `actual_delivery`. Which comparison matters is their call.

### 🏭 Warehouse
- Trust level in the system is the most important question for warehouse self-service. If they don't trust it, a dashboard won't help until accuracy improves.
- Confirm what "available to pick" means — on-hand only, or does it subtract reserved, in-transit, and held quantities?
- Lead with something you already calculated from their data. It earns the conversation.

### 💰 Finance / CFO
- Show them one reconciled number before the meeting. It changes the entire dynamic.
- Confirm revenue recognition timing, COGS methodology, intercompany elimination rules, and the exact components of "gross margin" before building anything.
- Month-end blockers are your highest-value automation targets. Eliminating one day of close time is immediately visible to the CFO.

### 📣 Marketing
- Most marketing teams have never been able to trace a specific invoice back to the campaign that generated the customer. If you can show them even a rough campaign-to-revenue link in the first meeting, it will be the most valuable data they've ever seen.
- Attribution model is a business decision — first touch, last touch, or equal share. They choose. You build.

### 🖥 IT
- Access provisioning delays are the most common reason self-service rollouts stall after the build phase. Surface it before launch.
- An ERP field rename with no notice breaks every report built on it. Establish a change notification process.

---

## Running the App

This guide is built as a React component. To run it locally:

```bash
npm install
npm start
```

The app includes:
- Per-department question checklists with progress tracking
- Expandable "Why ask this" rationale for every question
- A sidebar navigation with completion indicators
- A persistent power question panel

---

## Contributing

Questions should follow this format:

- **The question itself** — specific enough to ask verbatim, without being leading
- **Why ask this** — the business logic or data implication that makes this question worth asking

Questions that could apply to any department belong in the "Before Every Interview" section. Questions that require domain-specific data context belong in the relevant department section.

---

## License

MIT
