# Flow Designer — Software Request Fulfillment

The **`Software Request Fulfillment`** flow manages the software request lifecycle from submission through final fulfillment. It coordinates sequential manager and product owner approvals, Requested Item state updates, email notifications, and Catalog Task creation based on approval decisions and fulfillment outcomes.

**Trigger:** Initiated automatically via the **Service Catalog** whenever a user submits the **Software Request** catalog item.

## 1. Approval & Fulfillment Workflow

### Step 1 — Retrieve Request Details and Notify the Requester

The flow uses **Get Catalog Variables** to retrieve the submitted request information. A **Send Email** action then sends an email to the requester.

### Step 2 — Set the Requested Item to Pending

The Requested Item (RITM) is updated to **Pending** before the approval process begins. This represents the waiting stage while approvals are being processed.

### Step 3 — Manager Approval

The flow uses **Ask For Approval on Requested Item** to request the manager's decision.

- **Approved:** The flow proceeds to the Product Owner approval stage.
- **Rejected:** The RITM is updated to **Closed Incomplete**, a rejection email is sent to the requester, and the flow ends.

### Step 4 — Product Owner Approval

The Product Owner approval is requested only after the manager approves the request.

- **Approved:** The flow proceeds to fulfillment.
- **Rejected:** The RITM is updated to **Closed Incomplete**, a rejection email is sent to the requester, and the flow ends.

### Step 5 — Begin Fulfillment

After both approvals are granted, the flow updates the RITM to **Work in Progress** and creates a Catalog Task for fulfillment.

### Step 6 — Process the Fulfillment Outcome

The flow evaluates the outcome of the Catalog Task.

- **Successful fulfillment:** The RITM is updated to **Closed Complete**, and a completion email is sent to the requester.
- **Unsuccessful fulfillment:** The RITM is updated to **Closed Incomplete**, and an email is sent to the requester.

## 2. Requested Item State Transitions

| State | Purpose in the Workflow |
|---|---|
| Pending | The request is waiting during the approval stage. |
| Work in Progress | Both approvals are complete and fulfillment has started. |
| Closed Complete | The fulfillment process completed successfully. |
| Closed Incomplete | An approval was rejected or fulfillment was unsuccessful. |

These state updates distinguish the approval stage from active fulfillment and record the final outcome of the request.

## 3. Flow Stages & Lifecycle Management

The flow uses six custom Flow Stages to provide progress indicators throughout the software request lifecycle. Each stage is assigned at a specific point in the flow to reflect the current processing phase or outcome.

- **Requested:** Applied after the initial request submission email is sent to the requester. Represents the initial request stage.
- **Manager Approval:** Applied after the Requested Item is updated to Pending and before the manager approval action. Represents the first approval stage.
- **Prod.Owner Approval:** Applied before the Product Owner approval action, which runs only after the manager approves the request. Represents the second approval stage.
- **Request Cancelled:** Applied in either approval-rejection branch after the rejection email is sent and before the flow ends. The RITM is updated to Closed Incomplete.
- **Fulfillment:** Applied after both approvals are granted, before the flow updates the RITM to Work in Progress and creates a Catalog Task.
- **Complete:** Applied at the end of both fulfillment outcome branches, after the RITM is updated and the requester is notified. The RITM reaches Closed Complete for successful fulfillment or Closed Incomplete for unsuccessful fulfillment.


## 4. Email Notifications

Email notifications are implemented using **Send Email** actions within Flow Designer rather than separate Notification records.

The flow sends emails at key points in the lifecycle, including initial request processing, approval-related outcomes, successful fulfillment, and unsuccessful outcomes. These actions keep the requester informed without requiring a separate notification workflow.

---

## Flow Execution Screenshots

[View Successful Fulfillment Execution](../screenshots/flow-successful-fulfillment.png)

[View Manager Rejection Execution](../screenshots/flow-manager-rejection.png)

[View Product Owner Rejection Execution](../screenshots/flow-product-owner-rejection.png)

[View Unsuccessful Fulfillment Execution](../screenshots/flow-unsuccessful-fulfillment.png)
