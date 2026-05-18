# ⚡ HR Outside Employment Disclosure Automation

> Replacing paper forms and manual email chains with a fully automated Microsoft 365 workflow — built during a college internship at Front Range Community College (FRCC).

---

## 📋 The Problem

FRCC's HR department was managing outside employment disclosures using **Word documents emailed back and forth**. Employees would fill out a form, email it to their supervisor, and HR would manually track responses in a spreadsheet. Forms got lost. Supervisors missed emails. HR had no real-time visibility.

There were two separate forms for two employee classifications:
- **Faculty, Administrator, Technical & Professional staff** — a disclosure form with Yes/No routing
- **Classified employees** — a formal request form requiring multi-level supervisor approval

---

## ✅ The Solution

A fully automated Microsoft 365 workflow using **Microsoft Forms + Power Automate + SharePoint Excel** that:

1. Replaces the Word docs with online forms employees can fill out in minutes
2. Automatically logs every submission to a shared Excel spreadsheet on SharePoint
3. Automatically routes email notifications to the correct supervisor(s) based on the employee's answers
4. Eliminates manual data entry, lost forms, and missed emails entirely

---

## 🔁 How It Works

### Faculty/Admin Flow

```
Employee submits Microsoft Form
            ↓
Power Automate captures submission
            ↓
Logs all answers to Excel (always)
            ↓
Is outside employment = YES?
       ↓              ↓
      YES              NO
       ↓              ↓
Email supervisor   Email employee
"Action Required"  "No action needed"
```

### Classified Employee Flow

```
Employee submits Microsoft Form
            ↓
Power Automate captures submission
            ↓
Logs all answers to Excel (always)
            ↓
Emails Supervisor for review and approval
(Supervisor manually forwards to 2nd Level if approved)
```

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Microsoft Forms** | Digital replacement for Word doc forms |
| **Power Automate** | Workflow automation and conditional routing |
| **Microsoft Excel (SharePoint)** | Centralized submission tracking database |
| **Microsoft Teams** | Hosting environment for forms and workflows |
| **OneDrive for Business** | File storage and connector |

---

## 📁 What's in This Repo

```
├── README.md                          # This file
├── Power_Automate_Setup_Guide.docx    # Full step-by-step setup guide
├── screenshots/                       # Screenshots of the flow steps
│   ├── 01_form_faculty_admin.png
│   ├── 02_form_classified.png
│   ├── 03_excel_faculty_admin.png
│   ├── 04_excel_classified.png
│   ├── 05_flow_trigger.png
│   ├── 06_flow_get_response.png
│   ├── 07_flow_excel_mapping.png
│   ├── 08_flow_condition.png
│   └── 09_flow_email_steps.png
```

---

## 📊 Excel Spreadsheet Structure

### Faculty/Admin Spreadsheet (12 columns)

| Column | Source |
|--------|--------|
| Submission Date | Auto — Power Automate |
| Full Name | Form answer |
| Position/Job Title | Form answer |
| Department | Form answer |
| Supervisor Name | Form answer |
| Supervisor Email | Form answer |
| Filing Type | Form answer |
| Outside Employment | Form answer |
| Secondary Employer | Form answer |
| Duties Description | Form answer |
| Approval Status | Auto — set to "Pending" |
| Supervisor Comments | Manual — filled by supervisor |

### Classified Spreadsheet (15 columns)

| Column | Source |
|--------|--------|
| Submission Date | Auto — Power Automate |
| Full Name | Form answer |
| Department | Form answer |
| Position/Job Title | Form answer |
| Secondary Employer Info | Form answer |
| Days and Hours | Form answer |
| Total Hours Per Week | Form answer |
| Requested Start Date | Form answer |
| Supervisor Name | Form answer |
| Supervisor Email | Form answer |
| 2nd Level Supervisor Name | Form answer |
| 2nd Level Supervisor Email | Form answer |
| Approval Status | Auto — set to "Pending Review" |
| Supervisor Comments | Manual — filled by supervisor |
| 2nd Level Comments | Manual — filled by 2nd level supervisor |

---

## 🧠 Key Design Decisions

**Why Microsoft Forms instead of keeping the Word doc?**
Microsoft Forms integrates natively with Power Automate, making it possible to trigger automation the moment an employee submits. Word docs require manual handling at every step.

**Why format Excel as a table?**
Power Automate's "Add a row into a table" action requires the data to be in a formatted Excel table — not just a range. Without this, the connector cannot identify the columns.

**Why conditional routing for Faculty/Admin but not Classified?**
The Faculty/Admin form includes a Yes/No question about current outside employment. If the answer is No, there is nothing for the supervisor to review — so routing them an email would be noise. The Classified form is always a request to begin outside employment, so every submission always warrants supervisor review.

**Why ask employees to enter their supervisor's email?**
FRCC does not currently have a centralized employee-supervisor lookup table accessible via Power Automate. Having employees self-report their supervisor's email is the most reliable approach until that infrastructure exists.

---

## 🚀 How to Set This Up

See the full step-by-step walkthrough in **[Power_Automate_Setup_Guide.docx](./Power_Automate_Setup_Guide.docx)**

High-level steps:
1. Create a Microsoft Teams team for HR coordination
2. Build both Microsoft Forms inside a channel
3. Create both Excel spreadsheets on SharePoint formatted as tables
4. Build Power Automate flows connecting forms to Excel and email routing
5. Test end-to-end with both Yes and No responses
6. Share form links with employees via Collect Responses

---

## 📈 Results

| Before | After |
|--------|-------|
| Word doc emailed manually | Online form submitted in minutes |
| HR manually enters data into spreadsheet | Excel updates automatically on submission |
| Supervisor notified only if someone remembers | Supervisor email sent automatically |
| Forms frequently lost or delayed | Every submission tracked in real time |
| No visibility into submission status | Central Excel log with Approval Status column |

---

## 👤 About

**Robin Martinez**
Internship Project — Front Range Community College (FRCC)
Spring/Summer 2026

Built as part of an IT internship focused on business process automation using the Microsoft 365 ecosystem. This project was designed and implemented end-to-end — from requirements gathering and form design through Power Automate flow development, testing, and documentation.

---

## 📄 License

This project is for educational and portfolio purposes. All FRCC-specific data has been removed.
