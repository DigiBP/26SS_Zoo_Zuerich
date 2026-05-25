# Team Zoo Zürich

![Team Zoo Zürich](Images/Image_1.png)

# SS26_AlpineTech_Solutions
## Table of Contents

* [Project Members](#project-members)
* [1. Introduction](#1-introduction)
* [2. Problem Description](#2-problem-description)
  * [2.1 AS-IS Process Overview](#21-as-is-process-overview)
    * [Key Limitations of the AS-IS Process](#key-limitations-of-the-as-is-process)
    * [AS-IS BPMN Diagram](#as-is-bpmn-diagram)
    * [Project Focus: Digitalisation of the First Part of the Process](#project-focus-digitalisation-of-the-first-part-of-the-process)
* [3. Project Objective](#3-project-objective)
* [4. Digitalisation Approach: AS-IS vs. TO-BE](#4-digitalisation-approach-as-is-vs-to-be)
* [5. TO-BE Process](#5-to-be-process)
  * [5.1 Register a Lead](#51-register-a-lead)
  * [5.2 Choose Sales Representative and Assign Lead](#52-choose-sales-representative-and-assign-lead)
  * [5.3 Send Email with Available Consultation Slots](#53-send-email-with-available-consultation-slots)
  * [5.4 Specify Needs with Client](#54-specify-needs-with-client)
  * [5.5 Create a Quote](#55-create-a-quote)

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

While the AS-IS process covers the entire sales lifecycle, **this project focuses on the digitalisation of the process from the moment a lead request is received through to the creation of a quote**. This scope covers lead registration, lead assignment, consultation scheduling, needs definition, and quote creation — the steps with the highest concentration of manual effort, coordination overhead, and risk of data loss.

![Focus Process](Camunda/Alpine_Tech_Solutions_AS-IS_process_focus_%20process.png)

---

## 3. Project Objective

The problems identified in the AS-IS process — fragmented data, manual coordination, and lack of visibility — require a structured digitalisation of the sales process. The goal of this project is to automate and centralise the steps **from the moment a lead request is received through to the creation of a quote**, eliminating manual overhead and reducing the risk of data loss.

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


## 5. TO-BE Process

The TO-BE process replaces the fragmented, manual workflow with a centralised, automated sales pipeline orchestrated through **Camunda BPMN**. The digitised scope covers the full journey from an incoming lead request to the creation of a quote.

![Alpine Tech Solutions TO-BE Process](Camunda/Alpine%20Tech%20Solutions_TO-BE_focus_process.png)

The full TO-BE process model can be viewed and edited in Camunda Modeler:
[Alpine Tech Solutions — TO-BE process (BPMN)](resources/bpmn_models/Alpine%20Tech%20Solutions_TO-BE%20process.bpmn)

---

### 5.1 Register a Lead

#### Overview

The lead registration is the entry point of the digitalized Lead-process. A potential customer who is interested in the company's services submits a contact form. In a production setting this form would be embedded directly in the company website; for this prototype it is implemented as a Google Form. The submission captures the prospect's details and automatically triggers the downstream workflow in Camunda.

![Screenshot: The Google contact form](Images/Contact_Form.png)

The complete Google Form can be viewed and Submitted [here](https://docs.google.com/forms/d/e/1FAIpQLSdGfdGSBaz-DSek2og8MKrBVoiu1B48YRsy3M5m94WbBHbJmg/viewform).

#### Implementation

The contact form is implemented as a Google Form. The linked Make scenario uses a **Google [Watch Responses] trigger** to detect new submissions. This is
a polling-based trigger: Make checks for new form responses at a fixed interval. Once a new submission is detected, the scenario carries out three steps in sequence:


1. **Customer persistence** – A new record is inserted into the `customer` table of our PostgreSQL database (hosted on Neon). During this step, the free-text region input is normalized into a standardized country code (`ch`, `de`, `at`), so that downstream steps can rely on consistent values.
2. **Lead persistence** – A new record is inserted into the `lead` table and linked to the customer created in the previous step.
3. **Process start** – A REST call is made to the Camunda engine to start a new process instance. The relevant lead and customer data is passed along as process variables, so that subsequent tasks can access it without re-querying the database.

![Screenshot: The Make scenario for lead registration](Images/Register_Lead_Make_Process.png)

From this point onward, the Camunda Lead-process owns and orchestrates the workflow.

#### Design Rationale

**Trigger mechanism — polling vs. event-driven:** Ideally, the process would react to a form submission instantly. We therefore investigated event-driven alternatives, including triggering the scenario directly when a row is added to the linked response spreadsheet. However, we were unable to get the instant trigger working reliably within the project's scope. We therefore use Make's polling-based Google trigger, which checks for new submissions at a fixed interval. For the purpose of this prototype, a short polling delay is an acceptable trade-off: the lead is still processed automatically and without manual intervention, only with a brief latency between submission and process start. A fully event-driven trigger — for example via a Google Apps Script `onFormSubmit` event posting to a Make webhook — is a clear next step for a production deployment.

Customer and lead are stored as **separate records** because they represent different entities: a customer is a company or person, whereas a lead represents a single instance of sales interest. This separation reflects correct data modeling and would, for example, allow a returning customer to generate a second, independent lead.

The **region normalization** is performed once, at insertion time, rather than repeatedly later. This ensures that every downstream consumer — such as the automatic sales representative assignment and the VAT logic during quote creation — can rely on clean, consistent country codes.

Finally, core data is passed to Camunda **as process variables** when the instance is started. This makes the information directly available to later user tasks and forms without additional database lookups.

#### Known Limitations

- **The lead intake is polling-based rather than event-driven.** Make's Google  connector checks for new submissions at a fixed interval, introducing a short latency between form submission and process start. An event-driven trigger (e.g. an Apps Script `onFormSubmit` webhook) would eliminate this latency and is a recommended improvement.
- For the prototype, the Google Form stands in for a form embedded in the company website. The integration pattern would remain identical — the embedded form would post to the same webhook.

---

### 5.2 Choose Sales Representative and Assign Lead

#### Overview

Once a lead has been registered, the process must determine which sales
representative is responsible for it. Rather than relying on manual triage, the assignment is performed automatically based on defined business criteria. This ensures that leads are assigned consistently, immediately, and without a human bottleneck.

#### Implementation

The assignment is implemented as a dedicated Camunda service task ("Choose Sales Representative"), separate from the lead intake. The service task calls its own Make scenario via the API connector. The Make scenario executes a single SQL query against the database that selects the most suitable employee, and then writes the chosen employee onto the lead record via an `UPDATE` statement.

![Screenshot: The Make scenario for sales representative assignment](Images/Register_Lead_Make_Process.png)

The selection query evaluates all employees and ranks them by three criteria, in
order of priority:

1. **Region match** – the representative operates in the customer's region.
2. **Industry / specialization match** – the representative is specialized in the customer's industry.
3. **Current workload** – as a tie-breaker, the representative with the fewest currently assigned leads is preferred.

Importantly, these criteria are applied as a **ranking**, not as a filter. The query therefore always returns a representative, even if no employee perfectly matches the  region and industry of the customer.

#### Design Rationale

**Why a SQL query instead of Camunda DMN.** Camunda offers DMN (Decision Model and Notation) as a native mechanism for modeling decision logic in decision tables. We deliberately chose not to use DMN for this step. A DMN decision table is well suited to decisions that map a fixed set of *input values* to *output values* through static rules. The sales representative assignment, however, is not a static rule evaluation: it requires querying live data (the set of employees, their specializations, and their current lead counts) and performing a relative ranking across all candidates, including an aggregation (counting assigned leads per employee). This kind of data-driven, comparative selection is naturally expressed in SQL and would be awkward or impossible to express in a DMN table, which has no access to the database and no concept of "rank all rows and pick the best." Using a SQL query keeps the decision logic close to the data it depends on and allows the assignment rules to evolve simply by adjusting the query.

**Why these three criteria, in this order.** Region is prioritized first because a representative should operate within the customer's market. Industry specialization is second, ensuring domain expertise where possible. Workload is used only as a tie-breaker, so that among otherwise equally suitable representatives, leads are distributed evenly and no single representative becomes overloaded.

**Why the query always returns a representative.** The criteria are applied as a ranking rather than a hard filter. If the selection were a strict filter and no employee matched both region and industry, the query would return nothing and the process would stall with an unassigned lead. By ranking instead of filtering, the process always proceeds: a slightly imperfect assignment is preferable to a blocked process instance.

**Why the result is persisted to the lead record.** The chosen representative is written directly onto the `lead` table. The lead record thereby becomes the single source of truth for ownership of the lead, and every subsequent step can reliably determine the responsible representative by reading the lead.

---

### 5.3 Send Email with Available Consultation Slots

#### Overview

Once a sales representative has been assigned, the customer is invited to schedule a first consultation. This is the first direct customer touchpoint and bridges the automated intake with a human conversation. The customer receives a personalized email containing a booking link for their specifically assigned representative.

#### Implementation

The step is implemented as a dedicated Camunda service task, which calls a Make scenario via a webhook. The Make scenario performs the following:

1. Based on the `leadId`, a single SQL query retrieves both the customer's details and the assigned representative's details — including the representative's personal Cal.com booking link, which is stored in the `calcom_link` column of the `employee` table.
2. A personalized invitation email is sent to the customer via the Gmail module. The email addresses the customer by name, names the assigned representative, and contains that representative's Cal.com booking link.

![Screenshot: The Make scenario for sending the Cal.com link](Images/Send_Appointment_Make_Process.png)

![Screenshot: The invitation email](Images/Consultion_Booking_Email.png)

Each employee has their own Cal.com event type ("Initial Consultation with [Name]"), all hosted under a single shared Cal.com account. The corresponding booking link is stored per employee in the database.

#### Waiting for the Booking — Human Task with a Timer

After the invitation has been sent, the process must wait for the customer to react. This is modeled as a **user task** ("Confirm Booking Status") assigned to the sales representative, with an **interrupting boundary timer event** attached.

- If the customer books a consultation, the representative completes the user task
  and the process continues to the needs-clarification phase.
- If no booking occurs, the boundary timer fires after **14 days**, the user task is
  cancelled, and the lead is automatically closed as "unresponsive".

This construct prevents dead process instances: a lead that never responds does not
remain open indefinitely but is automatically closed after a defined period.

### Design Rationale

**Why one Cal.com account with multiple event types.** For the prototype, all representatives' event types are hosted under a single Cal.com account. This was a pragmatic decision that keeps the setup within the free tier while still presenting each customer with a representative-specific link. Crucially, the data model — one `calcom_link` per employee — is correct independently of this simplification. In a production setting, each representative would have their own calendar, and only the stored links would change; the process itself would remain unaltered.

**Why a manual confirmation instead of automatic booking detection.** Ideally, a booking on Cal.com would be detected automatically (via a Cal.com webhook) and correlated back to the running process instance. We deliberately scoped this out: the fully automated variant requires a webhook integration and message correlation, which adds significant integration complexity. Instead, the sales representative — who is notified of a real booking by Cal.com anyway — manually confirms the booking by completing the user task. The process model already accommodates the automated variant: the user task could later be replaced by a message catch event without restructuring the surrounding flow.

**Why a timer-based timeout.** Without a time limit, a lead whose customer never responds would leave a process instance running forever. The interrupting boundary timer guarantees that unresponsive leads are closed automatically after 14 days, keeping the set of active process instances clean and meaningful.

### Known Limitations

- Because all event types share a single underlying Cal.com account, they also share availability. This is a cosmetic separation rather than true per-representative scheduling. In production, each representative would have an independent calendar.
- Cal.com event types are provisioned manually for each employee. Adding a new representative requires creating a matching event type and populating the `calcom_link` field. This is acceptable for the fixed roster of the prototype.
- A booking made *after* the 14-day timeout would still reach the representative via Cal.com, but the corresponding lead would already be closed. In the current prototype this edge case is handled manually. The architecturally correct solution would treat a late booking as a returning lead and start a fresh process instance.

---

### 5.4 Specify Needs with Client

![Specify Needs with Client](Camunda/Specify_needs_with_clients/Specify_needs_with_clients.png)

This step is the core communication loop between the Sales Representative and the client. It is fully integrated with the central database via **Make (Integromat)** and consists of three stages: retrieving existing data, collecting needs through a structured form, and saving everything back to the database.

---

#### Retrieve Lead Data

![Make Scenario 1 – Retrieve Lead Data](Camunda/Specify_needs_with_clients/Specify_needs_Make.Scenario1-Retrive%20Lead%20Data.png)

Before the call begins, **Make Scenario 1** is triggered automatically. It connects Camunda with the database and retrieves all existing information about the lead — contact details, previous interactions, and any data already collected during earlier process steps. This data is injected into the Camunda process instance so the Sales Representative starts the conversation with full context, even if a different rep handled the client previously.

---

#### Document Communication — Camunda Form

During the call, the assigned Sales Representative opens a **Camunda User Task** containing a structured form pre-populated with the retrieved lead data. The rep fills in the client's requirements, preferences, and any relevant notes while the conversation is ongoing. 

The form is divided into multiple sections (Form 1–6), each capturing a specific area of the client's needs:

| | |
|---|---|
| ![Form 1](Camunda/Specify_needs_with_clients/Form_1.png) | ![Form 2](Camunda/Specify_needs_with_clients/Form_2.png) |
| ![Form 3](Camunda/Specify_needs_with_clients/Form_3.png) | ![Form 4](Camunda/Specify_needs_with_clients/Form_4.png) |
| ![Form 5](Camunda/Specify_needs_with_clients/Form_5.png) | ![Form 6](Camunda/Specify_needs_with_clients/Form_6.png) |

---

#### Save to Database

![Make Scenario 2 – Save to Database](Camunda/Specify_needs_with_clients/Specify_needs_Make.Scenario2-Save%20to%20DataBase.png)

Once the form is submitted, **Make Scenario 2** is triggered. All responses entered by the Sales Representative are automatically saved back to the central database. This ensures that the full communication history is preserved and accessible to any team member at any time — regardless of who conducted the call.

---

#### Communication Loop

Because a client typically requires multiple interactions before confirming their needs, this step runs as a **loop**. After each call, the process returns to the beginning of 5.4 — the rep retrieves the updated data, conducts the next conversation, fills in the form again, and saves the new information. The loop continues until the client's requirements are confirmed.

Once confirmed, the process exits the loop and returns to the main TO-BE flow, where one of two outcomes follows:

- **Lead closed** — the client is not a match; the case is closed in the database.
- **Create a Quote** — the client proceeds, and the process advances to step 5.5.

---

### 5.5 Create a Quote

Once the client has confirmed their requirements, the process advances to quote creation. A quote is generated automatically from a predefined template using the data collected and stored during the needs definition phase, replacing the manual Word/Excel preparation from the AS-IS process.

---

### How It Works




