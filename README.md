# Team Zoo Zürich

![Team Zoo Zürich](Images/Image_1.png)

# SS26_AlpineTech_Solutions
## Table of Contents

* [Project Members](#project-members)
* [Abstract & Project Overview](#abstract--project-overview)
* [2. Problem Description](#2-problem-description)
  * [2.1 AS-IS Process Overview](#21-as-is-process-overview)
    * [Key Limitations of the AS-IS Process](#key-limitations-of-the-as-is-process)
    * [AS-IS BPMN Diagram](#as-is-bpmn-diagram)
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

## Project members

### Project Team / Authors

| Name | Email |
| :--- | :--- |
| Robin Kaefer | [robin.kaefer@students.fhnw.ch](mailto:robin.kaefer@students.fhnw.ch) |
| Kateryna Shevelieva | [kateryna.shevelieva@students.fhnw.ch](mailto:kateryna.shevelieva@students.fhnw.ch) |
| Sofiia Irfan Pasha | [sofiia.irfanpasha@students.fhnw.ch](mailto:sofiia.irfanpasha@students.fhnw.ch) |
| Kateryna Hrebeniuk | [kateryna.hrebeniuk@students.fhnw.ch](mailto:kateryna.hrebeniuk@students.fhnw.ch) |
| Nataliia Zinovieva | [nataliia.zinovieva@students.fhnw.ch](mailto:nataliia.zinovieva@students.fhnw.ch) |

### Supervisors

| Name | Email |
| :--- | :--- |
| Andreas Martin | [andreas.martin@fhnw.ch](mailto:andreas.martin@fhnw.ch) |
| Charuta Pande | [charuta.pande@fhnw.ch](mailto:charuta.pande@fhnw.ch) |
| Devid Montecchiari | [devid.montecchiari@fhnw.ch](mailto:devid.montecchiari@fhnw.ch) |

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

### 2.1 AS-IS Process Overview

The current sales process at AlpineTech Solutions involves three internal roles — **Sales Representative**, **Sales Manager**, and **Technical Team** — coordinating with the **Customer** through a shared corporate email inbox.

**Process Flow:**

1. **Lead Registration** — A customer sends a request to the shared corporate email. The Sales Representative manually registers the lead by recording the client's contact details into a personal Excel file.

2. **Needs Definition** — The Sales Representative contacts the client to clarify their requirements and determine whether the client is interested in proceeding.

3. **Quote Creation** — If the client is interested, the Sales Representative manually creates a quote document in Word/Excel, which is then exported to PDF.

4. **Quote Verification** — The quote is reviewed by the Sales Manager. If the quote is not approved, it is returned to the Sales Representative for updates. This loop continues until the quote is approved.

5. **Quote Delivery** — The approved quote is sent to the client via Gmail.

6. **Client Decision** — The client's response is received by email. The Sales Representative manually checks the answer:
   - If the answer is **negative** — the client's row in Excel is marked red and the process ends (rejected).
   - If the answer is **positive** — the Sales Representative prepares and sends an invoice via Gmail.

7. **Project Handover** — The Sales Representative hands the project over to the Development Team. In parallel, the Technical Team creates and delivers the product to the client, while the system waits for the payment confirmation.

8. **Completion** — Once the product is delivered and payment is received, the client's row in Excel is marked green and the process ends successfully (*Customer onboarded / Project complete*).

**Tools currently used:**

| Step | Tool |
|---|---|
| Lead tracking | Excel (individual files per Sales Rep) |
| Quote preparation | Microsoft Word / Excel → PDF |
| Communication | Shared corporate Gmail inbox |
| Status tracking | Excel (manual color-coding: red = rejected, green = onboarded) |

#### Key Limitations of the AS-IS Process

- No centralised lead management — each Sales Representative maintains separate Excel files, leading to duplicates and data loss.
- All communication is handled through a shared inbox with no history tracking, meaning information is lost when staff are reassigned or absent.
- Quote and invoice preparation is entirely manual, consuming significant time and introducing inconsistencies.
- There is no structured follow-up mechanism — if a client does not respond, there is no automated re-engagement path.
- Sales Managers have no real-time pipeline visibility; status reporting requires manual consolidation from multiple spreadsheets.
- Client status is tracked by manually changing cell colors in Excel, which is error-prone and unscalable.

#### AS-IS BPMN Diagram

The diagram below shows the full AS-IS sales process at AlpineTech Solutions:

![Alpine Tech Solutions AS-IS Process](Camunda/Alpine_Tech_Solutions_AS-IS%20process.png)

The full process model can be viewed and edited in Camunda Modeler:
[Alpine Tech Solutions — AS-IS process (BPMN)](resources/bpmn_models/Alpine%20Tech%20Solutions_AS-IS%20process.bpmn)

#### Project Focus: Digitalisation of the First Part of the Process

While the AS-IS process covers the entire sales lifecycle, **this project focuses on the digitalisation of the first part of the process** — from lead registration through needs definition, quote creation, and quote approval. These steps represent the highest concentration of manual effort and coordination overhead, and are therefore the primary target for automation.

![Focus Process](Camunda/Alpine_Tech_Solutions_AS-IS_process_focus_%20process.png)

---

## 3. Project Objective

The problems identified in the AS-IS process — fragmented data, manual coordination, and lack of visibility — require a structured digitalisation of the first part of the sales process. The goal of this project is to automate and centralise the steps from lead registration through to quote approval, eliminating manual overhead and reducing the risk of data loss.

The solution targets the following outcomes:

- Centralised, real-time lead tracking replacing individual Excel files
- Automated lead assignment based on predefined rules (region, workload)
- Automated scheduling and follow-up reminders to prevent leads from stalling
- Structured quote generation with manager approval flow
- Full interaction history accessible to the entire sales team

---

## 4. Digitalisation Approach: AS-IS vs. TO-BE

The table below maps each identified bottleneck from the AS-IS process to its automated counterpart in the TO-BE implementation:

| Process Step | AS-IS (Manual) | TO-BE (Automated) |
| :--- | :--- | :--- |
| **Lead Registration** | Manual entry into individual Excel files; duplicates and data loss common. | Leads captured via contact form and stored instantly in a centralised CRM database via API. |
| **Lead Assignment** | Manual decision by the Sales Manager; slow and inconsistent. | Automatic routing to the responsible Sales Representative using a **DMN decision table** (region / workload). |
| **Consultation Scheduling** | No formal step — slots shared manually by email. | Automated booking link (Cal.com) sent via Gmail; confirmation received via webhook and injected into the process. |
| **Needs Definition** | Information gathered verbally during a call; stored in personal notes or Excel with no shared access. If the Sales Rep was absent, context was lost and the client had to repeat themselves. | A structured **Camunda User Task form** is filled by the Sales Rep during the call. Data is pulled from and saved to the central database, making the full client context available to any team member. The step repeats in a **loop** across multiple interactions until the client confirms their requirements — only then does the process advance to quote creation. |
| **Quote Generation** | Manual creation in Word/Excel, exported to PDF; inconsistent and time-consuming. | Quote generated automatically from a predefined template based on inputs collected during needs definition. |
| **Communication Tracking** | Fragmented Gmail threads; history lost when staff are absent or reassigned. | All interactions logged centrally in the CRM and accessible to the full sales team. |


## Task 3. Step-by-Step: Automating Meeting Scheduling with Cal.com

In the original process, the step **"Send email with available consultation slots"** was handled manually by a Sales Representative. Task 3 replaces this with a fully automated scheduling flow using **Cal.com**, connected to Camunda via **Make (Integromat)**.

---

### Challenge and Requirement

| Challenge | Requirement |
|---|---|
| Meeting slots were shared **manually** by the Sales Rep | Automate slot delivery via a self-service booking link |
| No booking confirmation mechanism in the process | Detect confirmation via webhook and resume the process automatically |
| Process could stall indefinitely waiting for a reply | Add a timeout escalation path for unresponsive leads |

---

### How It Works

1. **Trigger** — Once the lead is assigned, a Make scenario sends the client a Gmail containing their Sales Rep's **cal.com booking link**. No manual action is required.

2. **Client books** — The client self-selects a time slot via cal.com, which handles availability and calendar management automatically.

3. **Confirmation** — cal.com fires an `invitee.created` webhook, caught by Make, which calls the Camunda REST API to send a `ConsultationBooked` message to the waiting process instance. The process then resumes at **"Specify needs with client"**.

4. **Timeout** — If no booking is received within 7 days, a Timer Boundary Event escalates the case — either triggering a follow-up reminder or routing the lead to rejection.

---

### BPMN Changes

| Element | AS-IS | TO-BE |
|---|---|---|
| Send email with slots | Manual user task | Automated service task (Make + Gmail) |
| Client response | Not modeled | Message Catch Event (`ConsultationBooked`) |
| No-response handling | Not modeled | Timer Boundary Event (7-day escalation) |




