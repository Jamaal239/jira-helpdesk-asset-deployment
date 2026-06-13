# Jira Service Management: Enterprise Asset Tracking Implementation

This repository documents the end-to-end configuration and production deployment of an automated asset procurement and tracking pipeline within Jira Service Management (JSM). The objective of this implementation was to establish an ITIL-compliant hardware lifecycle workflow that dynamically captures critical configuration items (Asset Tags and Serial Numbers) directly within helpdesk service request workflows.

By engineering this structural bridge between front-end user ingestion and back-end database schema properties, the platform systematically eliminates asset tracking leakage, mitigates corporate risk, and optimizes hardware lifecycle auditing.

---

## Business Value & Operational Impact

In an enterprise IT infrastructure environment, manual inventory tracking leads to asset shrinkage and non-compliance. This deployment introduces key administrative controls:
* **Asset Leakage Mitigation:** Enforces rigid entry validation of core physical attributes prior to ticket closure, ensuring a 100% data capture rate for newly provisioned hardware.
* **Audit & Compliance Readiness:** Structurally aligns helpdesk operations with ITIL v4 Hardware Asset Management (HAM) compliance standards, creating an immutable paper trail for corporate auditors.
* **Operational Velocity:** Reduces Mean Time to Resolution (MTTR) by embedding inventory fields directly within the technician workspace, eliminating out-of-band communication loops.

---

## Implementation Lifecycle Architecture

The deployment was executed across five distinct operational phases, balancing front-end ticket lifecycle states with back-end relational database overrides:

### 01. Service Request Ingestion
An end-user initializes a hardware procurement request via the enterprise Customer Portal. The system automatically creates tracking ticket `EH-4`, populates the default system parameters, and places the issue into the unassigned triage queue.
* **Structural Verification Reference:** `01_laptop_request_ticket_created.png`

### 02. SLA Preservation & Operational Allocation
The service request is audited by the queue coordinator. Ownership is explicitly assigned to a system administrator/technician to establish direct operational accountability and halt response Service Level Agreement (SLA) timers.
* **Structural Verification Reference:** `02_assigning_ticket_to_technician.png`

### 03. Custom Schema Field Configuration
To capture precise corporate identifier data not natively supported by the standard out-of-the-box Jira data model, global custom fields for `Asset Tag` and `Serial Number` were provisioned via Jira Admin Text Schema settings.
* **Structural Verification Reference:** `03_creating_custom_asset_fields.png`

### 04. Functional Screen Layout Mapping
The newly engineered database fields were bound directly to project-specific Screen Configurations. By modifying the target `Request Fulfilment View/Edit Screen`, the fields are structurally injected into the technician's primary visual workspace.
* **Structural Verification Reference:** `04_linking_asset_fields_to_screen.png`

### 05. Production Run & Data Validation
A live end-to-end verification run was executed on the active ticket `EH-4`. Production infrastructure values were successfully committed to the database, confirming full integration between the database schema and the live UI layout.
* **Production Test Entries:**
  * **Asset Tag:** `IT-LAP-4029`
  * **Serial Number:** `5CD2185XYZ`
* **Structural Verification Reference:** `05_final_ticket_with_custom_asset_fields.png`

---

## Repository Artifact Verification

The following verified system screenshots correspond to the files in the root directory, serving as proof of deployment:

### Phase 1: Request Ingestion & Ticket Initialization
![01: Ticket Creation Layout](01_laptop_request_ticket_created.png)

### Phase 2: Resource Assignment & SLA Tracking
![02: Technician Allocation Schema](02_assigning_ticket_to_technician.png)

### Phase 3: Relational Database Schema Extension
![03: Custom Metadata Configuration](03_creating_custom_asset_fields.png)

### Phase 4: UI Screen Layout Interface Mapping
![04: Screen Layout Architecture](04_linking_asset_fields_to_screen.png)

### Phase 5: Production Live Verification Data Run
![05: Production Field Validation Run](05_final_ticket_with_custom_asset_fields.png)

---

## Technical Infrastructure Summary
* **Deployment Platform:** Jira Service Management (Cloud Enterprise Framework)
* **Core Framework:** ITIL v4 Hardware Asset Management (HAM) Lifecycle Strategy
* **Scope Identification:** `EH` Space Domain / Request Fulfillment Screen Mapping Schemes
