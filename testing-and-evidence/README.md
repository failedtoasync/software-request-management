# Testing & Evidence — Software Request Management

Testing covered catalog form behavior, Flow Designer automation, approval decisions, fulfillment outcomes, email notifications, Requested Item state transitions, SLA tracking, and dashboard reporting. All four primary end-to-end scenarios passed.

## 1. Catalog Item Testing

The **Software Request** catalog item was tested to verify its form behavior before submission. The `Default Requested For` client script populated the Requested For field with the logged-in user, while the field remained editable for requests submitted on behalf of someone else.

The Catalog UI Policy was also verified. Selecting **Other** as the operating system displayed the additional operating system field and made it mandatory. Selecting another operating system restored the field's original visibility and mandatory behavior.

[View Catalog Form](../screenshots/software-request-form.png)


## 2. Flow Designer — End-to-End Workflow Testing

The **`Software Request Fulfillment`** flow was tested across the complete request lifecycle, from catalog submission through approval and fulfillment to the final outcome. The flow retrieves catalog variables, sends requester emails, updates the Requested Item (RITM), manages sequential approvals, and creates a Catalog Task when the request is approved.

### Successful Fulfillment

The flow processes the request through Manager approval followed by Product Owner approval. The RITM is updated to **Pending** while approvals are being processed. After both approvals are granted, the flow updates the RITM to **Work in Progress** and creates a Catalog Task for fulfillment.

When the task follows the successful outcome path, the RITM is updated to **Closed Complete**, and a completion email is sent to the requester.

[View Manager Approval](../screenshots/ritm-manager-approval.png)

[View Product Owner Approval](../screenshots/ritm-product-owner-approval.png)

[View Fulfillment and Catalog Task](../screenshots/ritm-fulfillment-task-created.png)

[View Successful Completion](../screenshots/ritm-closed-complete.png)

[View Successful Fulfillment Execution](../screenshots/flow-successful-fulfillment.png)


### Manager Rejection

When the Manager rejects the request, the flow follows the rejection branch without proceeding to Product Owner approval or fulfillment. The RITM is updated to **Closed Incomplete**, a rejection email is sent to the requester, and the flow ends.

[View Manager Rejection Execution](../screenshots/flow-manager-rejection.png)


### Product Owner Rejection

After the Manager approves the request, the flow proceeds to Product Owner approval. When the Product Owner rejects it, the flow ends without proceeding to fulfillment. The RITM is updated to **Closed Incomplete**, and a rejection email is sent to the requester.

[View Product Owner Rejection Execution](../screenshots/flow-product-owner-rejection.png)


### Unsuccessful Fulfillment

After both approvals are granted, the flow creates a Catalog Task and follows the unsuccessful fulfillment outcome path. The RITM is updated to **Closed Incomplete**, and an email informing the requester of the outcome is sent.

[View Unsuccessful Fulfillment Execution](../screenshots/flow-unsuccessful-fulfillment.png)


## 3. Email Notifications

Email behavior was verified at key points in the workflow, including initial request processing, approval rejection, successful fulfillment, and unsuccessful fulfillment. These emails are implemented using **Send Email actions within Flow Designer**, rather than separate Notification records.

[View Email Notifications](../screenshots/workflow-email-notifications.png)


## 4. SLA Verification

The `Software Request Fulfillment SLA` was verified as active and working with its two-day target and `8-5 weekdays` schedule.

Testing confirmed that the SLA starts when the RITM enters **Work in Progress**, pauses when it enters **Pending**, resumes when it returns to **Work in Progress**, and stops when the RITM reaches **Closed Complete** or **Closed Incomplete**. This aligns SLA measurement with the configured fulfillment lifecycle.

[View SLA Lifecycle](../screenshots/sla-in-progress-and-paused.png)


## 5. Dashboard Verification

The `Software Request Management Dashboard` was verified with all four visualizations:

- **Software Request Operational Overview:** Requested Items grouped by State.
- **Approval & Fulfillment Outcome:** Requested Items grouped by Stage.
- **Software Request SLA Compliance:** Completed Task SLA records for the `Software Request Fulfillment SLA`, grouped by `Has breached`.
- **Software Request Demand Trend:** Requested Item count by month, using Created date.

The dashboard uses Requested Item and Task SLA records to present request distribution, workflow stages, SLA compliance, and monthly demand.

[View Dashboard](../screenshots/software-request-management-dashboard.png)

