# Catalog Item — Software Request

The **Software Request** catalog item provides a standardized entry point for employees to request new software installations, upgrades, or reinstallations. It collects the information required for approval and fulfillment while using catalog scripting and UI policies to support a consistent request experience.

## 1. Purpose

The catalog item addresses the need for a structured way to capture software requirements and their business justification. It collects requester information, request type, operating system, software details, version, and supporting information.

The item is configured to use the `Software Request Fulfillment` flow to manage the approval and fulfillment process.

## 2. Catalog Item Configuration

| Property | Configuration |
|---|---|
| Name | `Software Request` |
| Application | Global |
| Catalog | Service Catalog |
| Category | Software |
| Process Engine | Flow |
| Flow | `Software Request Fulfillment` |
| Short Description | Request software for business or work-related requirements. |

The catalog item supports requests for new installations, upgrades, and reinstallations. Its description explains that it is intended for business or work-related software needs.

## 3. Request Variables

The catalog item uses variables to collect the details required to process each request.

| Variable | Purpose |
|---|---|
| `requested_for` | Identifies the user who needs the software. Defaults to the logged-in user and can be changed. |
| `request_type` | Specifies whether the request is for a new installation, upgrade, or reinstallation. |
| `operating_system` | Identifies the target operating system. |
| `please_specify_other_operation_system` | Captures the operating system name when Other is selected. |
| `software` | References the requested software product model. |
| `version` | Captures the required software version. |
| `business_justification` | Records why the software is needed. |
| `additional_information` | Captures any other relevant details. |

The required fields ensure that the request contains the main information needed for approval and fulfillment. The software reference field uses the `cmdb_software_product_model` table and a reference qualifier that limits the available choices to software with status `In Production`.

## 4. Catalog Client Script — Default Requested For

The Catalog Client Script **`Default Requested For`** runs on form load and populates the Requested For variable with the currently logged-in user's ID.

This reduces manual entry when employees submit requests for themselves while allowing the field to be changed when the software is needed by another user.

**Implementation file:** [`default-requested-for.js`](default-requested-for.js)

## 5. Catalog UI Policy — Other Operating System

A Catalog UI Policy controls the visibility and mandatory behavior of the `please_specify_other_operation_system` variable.

When the Operating System field is set to Other, the additional field becomes visible and mandatory. When another operating system is selected, the policy's reverse behavior restores the field's original visibility and mandatory settings.

This ensures that users provide the additional operating system details only when they are needed.
