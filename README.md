# Mini-CRM-Demo-Power-Apps-Dataverse-Power-Automate-
Overview

Small demo CRM built to show practical skills with Microsoft Power Platform: Dataverse (data modeling), Model-Driven Power Apps (UI), Business Rules (validation), and Power Automate (workflow automation).
Purpose: demonstrate that I can design a CRM data model, enforce business logic, and automate notifications without writing code.

Data model

Tables

Leads

Primary Name (Text)

Email (Text)

Phone (Text)

Source (Text)

Opportunities

Opportunity Name (Primary)

Amount (Currency)

Stage (Choice: Prospecting, Proposal, Negotiation, Closed Won, Closed Lost)

CloseDate (Date)

Lead (Lookup → Leads)

Relationship

Leads (1) → Opportunities (N)
One Lead can have many Opportunities (1:N lookup from Opportunities to Leads).

Business Rule

Rule: If Stage = Closed Won then set Amount to Required.

Purpose: enforce data quality so closed deals always include an amount (useful for forecasting and finance).

Automation

Flow name: Notify Closed Won Opportunity (Power Automate)

Trigger: When a row is modified (Dataverse) — Table: Opportunities
Condition: Stage = Closed Won
Action: Send an email notification (Outlook) with dynamic content from the opportunity (Name, Amount, CloseDate, Lead).

Purpose: simulate real operational alerting (sales/finance notifications) when deals close.

Screenshots (add to /screenshots)

leads-table.png — Leads table columns & sample data

opportunities-table.png — Opportunities table columns & sample data

relationship-1n.png — 1:N relationship UI showing lookup

business-rule.png — Business Rule designer with the rule active

power-automate-flow.png — Flow designer showing trigger, condition, and email action

model-driven-app.png — Model-driven App running: list view of Leads & Opportunities

How to run / reproduce (quick)

Open Power Apps → Dataverse → create the two tables above (or import schema).

Create the 1:N relationship (Opportunities → Lead lookup).

Build a Model-Driven App including Leads and Opportunities.

Add the Business Rule on Opportunities (Stage = Closed Won → Amount required) and activate it.

In Power Automate, create the Notify Closed Won Opportunity flow (trigger: Dataverse row modified → condition → send email).

Test: create a Lead, create an Opportunity, move Stage → Closed Won and verify the email arrives.
