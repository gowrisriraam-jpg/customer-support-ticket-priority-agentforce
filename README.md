# Customer Support Ticket Priority Prediction and Automated Assignment System Using Agentforce

## 📌 Project Overview

This project is a Salesforce-based customer support automation system that uses **Agentforce and Salesforce Flow** to analyze support ticket descriptions, determine ticket priority, and automate actions for high-priority issues.

The system helps support teams reduce manual effort and handle urgent customer issues more efficiently.

## 🎯 Problem Statement

Customer support teams receive a large number of tickets every day. Manually reviewing, prioritizing, and assigning these tickets can cause delays in handling critical issues.

This project provides an automated solution that:

- Analyzes customer support ticket descriptions
- Determines ticket priority
- Identifies urgent issues
- Creates a task for high-priority tickets
- Assigns the ticket to the appropriate support level
- Returns the result through Agentforce

## 🚀 Objectives

- Automatically classify support tickets as **High, Medium, or Low**
- Identify urgent customer issues using ticket descriptions
- Automate task creation for high-priority tickets
- Reduce manual support-team effort
- Integrate Salesforce Agentforce with Flow
- Improve the overall support-ticket workflow

## 🛠️ Technologies Used

- Salesforce
- Agentforce
- Salesforce Flow
- Salesforce Custom Objects
- Salesforce Tasks
- GitHub

## 🗂️ Salesforce Custom Object

**Object Name:** Support Ticket Intelligence

**API Name:** `Support_Ticket_Intelligence__c`

### Main Fields

| Field | Data Type | Purpose |
|---|---|---|
| Ticket Number | Auto Number | Unique ticket identification |
| Customer | Lookup (Account) | Related customer account |
| Contact | Lookup (Contact) | Customer contact |
| Issue Type | Picklist | Technical, Billing, General |
| Description | Long Text Area | Ticket issue details |
| Priority Level | Picklist | Low, Medium, High |
| Status | Picklist | New, In Progress, Resolved |
| Created Date | Date | Ticket creation date |
| Assigned To | Lookup (User) | Assigned support agent |
| SLA Breach Risk | Checkbox | Indicates SLA risk |
| Resolution Time | Number | Resolution time in hours |

## 🔄 Flow Automation

The Auto-Launched Flow receives the **Account Name** as input and retrieves the latest support ticket associated with that account.

### Flow Process

```text
Account Name
     ↓
Get Account
     ↓
Store Account Id
     ↓
Get Latest Support Ticket
     ↓
Store Ticket Id
     ↓
Analyze Description
     ↓
Determine Priority
     ↓
High Priority Check
     ↓
Create Task for High Priority
     ↓
Assign Support Level
     ↓
Generate Action Message
     ↓
Return Output to Agentforce
```

## 🧠 Priority Classification Logic

| Priority | Keywords / Condition |
|---|---|
| High | `urgent`, `not working`, `failure` |
| Medium | `issue`, `slow`, `delay` |
| Low | None of the above conditions |

### High Priority

When the ticket description contains keywords such as:

- urgent
- not working
- failure

the ticket is classified as **High Priority**.

A task is created for urgent handling.

### Medium Priority

When the description contains keywords such as:

- issue
- slow
- delay

the ticket is classified as **Medium Priority**.

### Low Priority

If none of the defined priority keywords are detected, the ticket is classified as **Low Priority**.

## 🤖 Agentforce Integration

Agentforce is configured with a dedicated subagent:

**Support Ticket Priority Analysis**

The Agentforce action invokes the Salesforce Flow and provides the Account Name as input.

### Agent Input

`varAccountName`

### Agent Outputs

- `varAccountId`
- `varTicketId`
- `varPriorityLevel`
- `varAssignedTo`
- `varActionMessage`

The Agentforce subagent analyzes the ticket information and triggers the backend Flow for automation.

## 📊 Testing

The system was tested using High, Medium, and Low priority scenarios.

| Test Case | Expected Result |
|---|---|
| Urgent / failure-related issue | High Priority |
| Slow / delay-related issue | Medium Priority |
| General question | Low Priority |

Detailed test results are available in the `test-results` folder.

## 📸 Project Screenshots

### Salesforce Custom Object

![Custom Object](screenshots/01-custom-object.png)

### Ticket Fields

![Ticket Fields](screenshots/02-ticket-fields.png)

### Salesforce Flow

![Flow Overview](screenshots/03-flow-overview.png)

### Priority Decision

![Priority Decision](screenshots/04-priority-decision.png)

### High Priority Task

![High Priority Task](screenshots/05-high-priority-task.png)

### Agentforce Subagent

![Agentforce Subagent](screenshots/06-agentforce-subagent.png)

### Agent Action

![Agent Action](screenshots/07-agent-action.png)

## 📁 Project Structure

```text
customer-support-ticket-priority-agentforce/
│
├── README.md
│
├── screenshots/
│   ├── 01-custom-object.png
│   ├── 02-ticket-fields.png
│   ├── 03-flow-overview.png
│   ├── 04-priority-decision.png
│   ├── 05-high-priority-task.png
│   ├── 06-agentforce-subagent.png
│   └── 07-agent-action.png
│
├── test-results/
│   └── ticket-priority-results.csv
│
└── documentation/
    └── project-documentation.pdf
```

## 📈 Expected Outcome

- Faster identification of urgent tickets
- Reduced manual prioritization
- Automated handling of high-priority cases
- Better support-team workflow
- Reduced repetitive work
- Improved ticket-management process

## 🔮 Future Enhancements

- AI-based sentiment analysis
- More advanced ticket classification
- Intelligent workload-based agent assignment
- SLA prediction
- Email or notification automation
- Analytics dashboard for support managers

## 👥 Project Team

This project was developed as a team project using Salesforce Agentforce and Flow.

## 📌 Note

This project is developed for educational and demonstration purposes.
