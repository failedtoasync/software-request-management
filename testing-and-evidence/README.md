# Testing & Evidence — Software Request Management

Testing covered catalog form behavior, approval and fulfillment paths, email notifications, Requested Item state transitions, SLA tracking, and dashboard reporting. All four primary end-to-end scenarios passed.

## 1. Catalog Item Testing

The Requested For field was verified to default to the logged-in user and remain editable when a request is submitted for someone else. The conditional operating system field was also tested: selecting **Other** displays the additional field and makes it mandatory, while selecting another operating system restores its original behavior.

## 2. End-to-End Workflow Testing

**Successful fulfillment — Passed**

The manager and Product Owner approvals were granted in sequence. After both approvals, the RITM moved to Work in Progress, a Catalog Task was created, and successful fulfillment updated the RITM to Closed Complete. The requester received the completion email.

**Manager rejection — Passed**

When the manager rejected the request, the flow ended without proceeding to Product Owner approval or fulfillment. The RITM was updated to Closed Incomplete, and the requester received a rejection email.

**Product Owner rejection — Passed**

After manager approval, the Product Owner rejected the request. The flow ended without proceeding to fulfillment, the RITM was updated to Closed Incomplete, and the requester received a rejection email.

**Unsuccessful fulfillment — Passed**

After both approvals, the Catalog Task followed the unsuccessful outcome path. The RITM was updated to Closed Incomplete, and the requester received an email about the outcome.

## 3. Notifications & State Transitions

Email behavior was verified at request submission, approval stages, successful fulfillment, and rejection or unsuccessful outcomes. The RITM state transitions were also checked to confirm that requests move through Pending and Work in Progress as appropriate, ending in Closed Complete or Closed Incomplete according to the outcome.

## 4. SLA Verification

The `Software Request Fulfillment SLA` was verified as active and working with its two-day target and `8-5 weekdays` schedule. Testing confirmed that the SLA starts when the RITM enters Work in Progress, pauses in Pending, resumes in Work in Progress, and stops when the RITM reaches Closed Complete or Closed Incomplete.

## 5. Dashboard Verification

The `Software Request Management Dashboard` was verified as working with its four visualizations: request state distribution, approval and fulfillment stages, SLA compliance, and monthly request demand. The reports use Requested Item and Task SLA records to present the configured operational data.

