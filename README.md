# Software Request Management

A ServiceNow catalog-based solution that standardizes software requests through approval-driven fulfillment, automated notifications, SLA tracking, and dashboard reporting.

## Table of Contents

1. [Business Context & Solution](#1-business-context--solution)
2. [System Architecture & Workflow](#2-system-architecture--workflow)
   - [Software Request Submission](#software-request-submission)
   - [Approval & Fulfillment Automation](#approval--fulfillment-automation)
   - [SLA Tracking](#sla-tracking)
   - [Access & Platform Security](#access--platform-security)
   - [Operational Reporting](#operational-reporting)
3. [Technical Stack & Capabilities](#3-technical-stack--capabilities)
4. [Validation & Test Scenarios](#4-validation--test-scenarios)
5. [Repository File Index](#5-repository-file-index)

---

## 1. Business Context & Solution

### Business Context

Software requests require consistent information, appropriate approvals, and coordinated fulfillment. Without a structured process, tracking request progress, approval decisions, and fulfillment performance can become difficult.

### Solution

**Software Request Management** provides a centralized process for employees to submit software requests through the Service Catalog. Flow Designer coordinates the approval and fulfillment process, while automated notifications keep relevant users informed of request progress and outcomes.

The solution also incorporates SLA tracking and dashboard reporting to support visibility into fulfillment performance and overall request demand. By combining standard ServiceNow capabilities, the implementation provides a structured request lifecycle without unnecessary customization.

## 2. System Architecture & Workflow

### Software Request Submission

The Software Request catalog item provides a standardized entry point for employees to request new software installations, upgrades, or reinstallations. It captures the software requirements and supporting business information needed to process each request.

Catalog scripting and UI policies support the form experience, including automatically populating the Requested For field and displaying additional information when a user selects Other as the operating system.

### Approval & Fulfillment Automation

The `Software Request Fulfillment` flow manages the request lifecycle using sequential manager and product owner approvals. Based on approval decisions and fulfillment outcomes, the flow coordinates request updates, notifications, and Catalog Task creation.

This approach keeps the approval and fulfillment logic centralized in Flow Designer rather than distributing the process across multiple independent automations.

### SLA Tracking

The `Software Request Fulfillment SLA` monitors fulfillment performance against a defined two-day target. Its lifecycle is aligned with the request process, allowing fulfillment time to be tracked separately from approval waiting periods and helping identify whether requests meet their target.

### Access & Platform Security

The solution uses ServiceNow's standard platform access controls and catalog access behavior to operate within the platform's existing security model. Request submission, record access, and fulfillment activities remain subject to applicable platform permissions, while approval and fulfillment responsibilities are handled through the defined workflow.

### Operational Reporting

The `Software Request Management Dashboard` provides an overview of request states, approval and fulfillment outcomes, SLA compliance, and request demand trends through four visualizations.

Together, these views support operational monitoring without requiring users to examine individual request records to understand the broader picture.

## 3. Technical Stack & Capabilities

The solution combines standard ServiceNow capabilities with targeted catalog configuration to manage the software request lifecycle.

- **Service Catalog:** Catalog item design, variables, reference fields, and conditional form behavior.
- **Catalog Client Scripts & UI Policies:** Default field values and context-dependent form requirements.
- **Flow Designer:** Sequential approvals, notifications, request updates, and fulfillment orchestration.
- **Requested Items & Catalog Tasks:** Request lifecycle management and fulfillment tracking.
- **SLA Management:** Time-based fulfillment target monitoring.
- **Platform Analytics & Dashboards:** Operational reporting and request trend visibility.

## 4. Validation & Test Scenarios

The implementation was validated through four primary end-to-end scenarios:

- **Successful fulfillment:** Both approvals granted and fulfillment completed successfully.
- **Manager rejection:** The request is rejected at the manager approval stage.
- **Product owner rejection:** The request is rejected at the product owner approval stage.
- **Unsuccessful fulfillment:** The fulfillment task does not complete successfully.

Additional testing covered catalog form behavior, notification delivery, request lifecycle handling, SLA tracking, and dashboard reporting. All four primary scenarios passed, and the SLA and dashboard were verified as working.

Detailed scenarios and supporting screenshots are documented separately in the testing and evidence section.

## 5. Repository File Index

The following files contain the configuration details, implementation logic, and technical explanations for the project's key components.

- [Catalog Item — LINK TO BE ADDED](LINK_TO_CATALOG_ITEM_README)
- [Flow Designer — LINK TO BE ADDED](LINK_TO_FLOW_DESIGNER_README)
- [SLA Configuration — LINK TO BE ADDED](LINK_TO_SLA_README)
- [Dashboard — LINK TO BE ADDED](LINK_TO_DASHBOARD_README)
- [Testing & Evidence — LINK TO BE ADDED](LINK_TO_TESTING_AND_EVIDENCE_README)
