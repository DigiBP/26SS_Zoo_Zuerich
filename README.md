# SS26_AlpineTech_Solutions
## Table of Contents

* [Project Members](#project-members)
* [Abstract & Project Overview](#abstract--project-overview)
* [AS-IS Process](#as-is-process)
  * [Key Limitations of the AS-IS Process](#key-limitations-of-the-as-is-process)
  * [AS-IS BPMN Diagram](#as-is-bpmn-diagram)
  * [Project Goal](#project-goal)
* [TO-BE Process](#to-be-process)
  * [TO-BE BPMN Diagram](#to-be-bpmn-diagram)
  * [Challenges and Requirements](#challenges-and-requirements)
  * [Users and Stakeholders](#users-and-stakeholders)
* [Technologies Used](#technologies-used)
* [Backend Overview](#backend-overview)
  * [Architecture](#architecture)
  * [Application Entry Point ( main.py )](#application-entry-point--mainpy-)
  * [Database & Seeding](#database--seeding)
  * [Domain Models](#domain-models)
  * [API Layer (Routers)](#api-layer-routers)
  * [Service Layer (Business Logic)](#service-layer-business-logic)
  * [Frontend Hosting](#frontend-hosting)
  * [Docker Infrastructure](#docker-infrastructure)
  * [Typical Use Cases](#typical-use-cases)
* [Workflow Orchestration](#workflow-orchestration)
  * [Camunda BPMN Engine](#camunda-bpmn-engine)
  * [n8n Integration & AI Storage Worker](#n8n-integration--ai-storage-worker)

# Example of how to print the main sections:
for item in table_of_contents["sections"]:
    if isinstance(item, dict):
        for key in item.keys():
            print(f"- {key} (has subsections)")
    else:
        print(f"- {item}")
## 1. Introduction

AlpineTech Solutions is a Swiss-based technology company headquartered in Olten. The company provides IT services for small and medium-sized enterprises across Switzerland, Germany, and Austria. With approximately 200 employees, including a sales department of 10 representatives, AlpineTech Solutions has experienced rapid growth over the past three years.

As the company expanded its customer base and sales activities, the existing tools used to manage sales processes have become increasingly inefficient. Currently, AlpineTech Solutions relies on spreadsheets, email communication, and shared documents to track leads, manage customer interactions, and monitor sales opportunities. These fragmented tools create operational inefficiencies, chaos in processes and limit visibility into sales performance.

To address these challenges, AlpineTech Solutions has initiated a project to select and implement a Customer Relationship Management (CRM) system that will support the digitalisation and automation of its sales processes.

---

## 2. Problem Description

The sales department currently manages leads, customer information, and sales opportunities using Excel files stored in shared drives. Each sales representative maintains their own tracking files, which leads to inconsistent data, duplicated work, and poor coordination between team members.

Furthermore, communication with customers is handled primarily through email without a centralized record of interactions. As a result, when sales representatives are absent or accounts are reassigned, valuable information about client conversations and negotiations is often lost.

Sales managers also face difficulties obtaining an accurate overview of the sales pipeline. Weekly sales reports are manually compiled from different spreadsheets, manual presentation creature which consumes considerable time and often leads to outdated or inaccurate forecasts.

These issues have resulted in several operational problems:

- Sales leads are not centrally managed.
- Multiple representatives sometimes contact the same prospect.
- Customer interaction history is incomplete or totally missing.
- Quote generation and proposal preparation require manual work.
- Sales managers lack real-time visibility into deal progress.
- Reports and client presentations are done manually.

To improve efficiency and support future growth, AlpineTech Solutions's management has decided to introduce a CRM system that centralizes sales data and automates key sales activities.

---

## 3. Project Objective

The objective of this project is to identify, evaluate, and select an appropriate CRM software solution that will enable the digitalisation of AlpineTech Solutions's sales processes.

The CRM system should support the following objectives:

- Centralised management of leads, contacts, and customer accounts
- Structured tracking of sales opportunities through a sales pipeline
- Automated lead assignment and follow-up reminders
- Integrated communication tracking with customers
- Automated quote generation and sales reporting
- Integration with the company's existing ERP and email systems
- Maybe select?

The selected solution should improve operational efficiency, provide better data visibility, and support scalable sales growth.

---

## 4. Opportunities for Process Digitalisation and Automation

The implementation of the CRM system will enable several automated workflows within the sales process.

For example, when a new lead submits a contact form on the company website, the information can automatically be entered into the CRM system. The lead can then be automatically assigned to a sales representative based on predefined rules such as region or industry.

The CRM system can also automate follow-up reminders for sales representatives, ensuring that leads are contacted within a specified timeframe.

Another opportunity for automation is the sales opportunity pipeline, where deals automatically progress through defined stages such as lead qualification, proposal preparation, negotiation, and contract closing.

Quote generation can also be automated through predefined templates and pricing rules, reducing manual work and improving consistency in proposals.

Furthermore, the CRM system can automatically generate sales performance reports and dashboards, providing management with real-time insights into sales activities and revenue forecasts.

## 5. Current Implementation & Progress

### Comparison: From Manual Inefficiency to Digital Excellence

| Feature | AS-IS (Before) | TO-BE (Digitalised Improvement) |
| :--- | :--- | :--- |
| **Lead Registration** | Manual entry into multiple Excel files, leading to duplicates and data loss. | **Automated Service Task:** Leads are captured via API and instantly stored in a centralized CRM Database. |
| **Lead Assignment** | Manual decision-making by managers; slow and inconsistent coordination. | **Automated Logic:** Automatic routing to sales reps based on region or industry **(DMN)**. |
| **Consultation Booking** | Manual back-and-forth emails to find a suitable time slot. | **Smart Reminders:** System automatically decides when to send follow-ups or notify agents **(DMN)**. |
| **Document Creation** | Manual generation of quotes/invoices using Word and Excel templates. | **Automated Workers:** Quotes are generated as PDFs with dynamic pricing rules. |
| **Communication** | Fragmented email threads with no centralized history. | **Integrated Tracking:** All customer interactions are logged directly in the CRM via Gmail/API integration. |
| **Process Monitoring** | Weekly reports manually compiled from spreadsheets; often outdated. | **Real-Time Dashboards:** Automatic generation of sales performance reports and live revenue forecasts. |

## 6. Coaching questions
