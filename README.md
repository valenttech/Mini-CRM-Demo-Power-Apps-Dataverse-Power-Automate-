Small demo CRM built to showcase practical skills with the Microsoft Power Platform:
Dataverse (data modeling) • Model-Driven Apps (UI) • Business Rules (validation) • Power Automate (workflow automation).

The purpose is to demonstrate the ability to design a CRM data model, enforce business logic without code, and automate notifications.

🧱 Data Model
📌 Tables
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

🔗 Relationship

Leads (1) → Opportunities (N)
One Lead can have many Opportunities (1:N lookup from Opportunities to Leads).

⚙️ Business Rule

Rule:
If Stage = Closed Won, set Amount to Required.

Purpose:
Maintains data quality so all closed-won deals include a value (important for forecasting and finance).

🔔 Automation (Power Automate)

Flow Name: Notify Closed Won Opportunity
Trigger: When a row is modified (Dataverse) — table: Opportunities
Condition: Stage = Closed Won
Action: Send an email via Outlook with dynamic content:

Opportunity Name

Amount
CloseDate
Lead Name

Purpose:
Simulates real CRM alerting when a deal is closed.


🚀 How to Run / Reproduce

Go to Power Apps → Dataverse and create the two tables above (or import schema).
Create the 1:N relationship (Opportunities → Lead lookup).
Build a Model-Driven App including Leads & Opportunities.
Add and activate the Business Rule (Closed Won → Amount = required).
In Power Automate, create the flow (row modified → condition → send email).

Test the flow:

Create a Lead
Create an Opportunity
Change Stage → Closed Won
Verify the email is sent
