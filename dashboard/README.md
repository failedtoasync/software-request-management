# Dashboard — Software Request Management

The **`Software Request Management Dashboard`** provides an overview of software request states, approval and fulfillment outcomes, SLA compliance, and request demand trends. It combines four visualizations using Requested Item and Task SLA data to support operational monitoring.

## Dashboard Visualizations

### Software Request Operational Overview

Displays the distribution of software requests by Requested Item **State**, provides an overview of software requests across their lifecycle states.

### Approval & Fulfillment Outcome

Displays Requested Item records grouped by **Stage**, provides a view of requests across the stages of the approval and fulfillment process.

### Software Request Demand Trend

Displays the count of Requested Item records by **month**, using **Created date** as the time dimension to show monthly trends in software request demand.

### Software Request SLA Compliance

This visualization is based on Task SLA records and displays completed SLA records for the `Software Request Fulfillment SLA`. It filters records to the relevant SLA with **Stage = Completed** and groups them by **Has breached**, distinguishing SLAs completed within the target from those that breached it.

[View Dashboard](../screenshots/software-request-management-dashboard.png)
