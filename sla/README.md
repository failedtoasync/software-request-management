# SLA — Software Request Fulfillment

The **`Software Request Fulfillment SLA`** tracks the time spent fulfilling software requests against a defined two-day target. Its lifecycle is aligned with the Requested Item (RITM) states so that time spent waiting for approvals is excluded from the fulfillment measurement.

## 1. SLA Configuration

The Software Request Fulfillment SLA is configured as a Resolution SLA on the Requested Item (sc_req_item) table. It uses the default SLA flow, a duration of two days, and the 8-5 weekdays schedule.

## 2. SLA Conditions

The SLA lifecycle is controlled by conditions on the Requested Item record.

**Start condition:** The SLA starts when the catalog item is `Software Request` and the RITM state is **Work in Progress**. This aligns the start of SLA measurement with the beginning of fulfillment after both approvals have been granted.

**Pause condition:** The SLA pauses when the RITM state changes to **Pending**. This excludes time spent waiting during the approval stage from the active fulfillment measurement.

**Resume condition:** The SLA resumes when the RITM returns to **Work in Progress**, allowing fulfillment time to continue accumulating.

**Stop condition:** The SLA stops when the RITM reaches either **Closed Complete** or **Closed Incomplete**. This covers both successful fulfillment and unsuccessful outcomes.

## 3. SLA Lifecycle

The SLA is designed to measure the fulfillment portion of the software request lifecycle rather than the entire time from submission to closure.

When the request enters Work in Progress, the two-day SLA begins measuring elapsed time according to the configured weekday schedule. If the RITM enters Pending, the SLA pauses; when it returns to Work in Progress, measurement resumes. Once the request reaches Closed Complete or Closed Incomplete, the SLA stops.

This lifecycle separates approval waiting time from active fulfillment time and provides a consistent basis for monitoring fulfillment performance.

