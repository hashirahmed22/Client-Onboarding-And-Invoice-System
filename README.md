PARADOX Client Onboarding Automation
Theme: Human + AI, Better Together. An n8n workflow that takes a freelance web app client from first request to welcome email. AI drafts the emails, and a human approves the steps that matter.

The problem
Freelancers lose hours on the same admin for every new client: collecting requirements, writing the agreement and invoice, chasing signatures and payment, and sending the welcome email. This workflow automates that admin and keeps the freelancer in control of anything the client sees.

How it works
Part 0: Intake

The client fills in a web form with company, contact, need, budget and due date.
The due date is checked. It must be 14 days to 1 year away, otherwise the client is emailed to choose another date.
A Lead row is added to the Google Sheet and the owner is notified.
Claude drafts a meeting invite. The owner approves or rejects it before it is sent.
Part 1: Deal closed

The owner sets Status to Closed-Won in the sheet.
The agreement and invoice are generated at the same time from Google Doc templates, filled with the client’s details, and exported as PDFs.
The owner approves both documents. On approval, each is emailed to the client as a PDF. A rejection marks the row Needs Fix.
The row becomes Awaiting Payment.
Part 2: Paid

The owner sets Paid to TRUE when the money arrives.
Claude writes the personal parts of a welcome email, and it is sent to the client.
The row becomes Active Client.
Where the human comes in
Meeting invite approval: AI-written text should not reach a client unchecked.
Agreement and invoice approval: money and legal terms need human judgment.
Closed-Won and Paid: only the freelancer knows when a deal is agreed and the funds are in the bank.
Built with
n8n: workflow engine, form trigger and approval emails
Claude (Sonnet 5): drafts the meeting invite and welcome email parts, through structured output parsers
Google Sheets: client database and status triggers
Google Drive and Docs: agreement and invoice templates, PDF export
Gmail: all email sending, including the approvals
Setup
Import client-onboarding-ahmed.json into n8n (Import from file).
Connect Gmail, Google Sheets, Google Drive, Google Docs and an Anthropic model.
Create a Google Sheet with a Clients tab and these headers: Deal ID, Legal Name, Contact Name, Contact Email, Scope Items, Budget, Due Date, Notes, Status, Paid, Deposit Amount, Contract Link, Invoice Link.
Create the agreement and invoice templates in Google Docs. Use placeholders such as [[client_legal_name]] and [[total_amount]], and update the template IDs and folder ID in the copy steps.
Replace the sheet ID and email address in the workflow with your own.
Test with your own email as the client, then activate the workflow.
Notes
The workflow runs on n8n. The competition requires deployment on Alternate Clouds.
The agreement and invoice templates are samples for testing only, not legal advice.
The file contains no API keys or passwords.
