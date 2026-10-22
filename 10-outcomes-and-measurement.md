# Digital Certificates — Outcomes and Measurement

## 1. Purpose

This document evaluates the business outcomes of the digital certificate issuance process and defines how its performance is measured.

It answers three key questions:

1. How much has the level of automation increased?
2. How much have manual processing and certificate issuance time decreased?
3. Which KPIs are used to evaluate process performance?

## 2. Business Outcomes

The process improvement focuses on three primary indicators: automated certificate generation, manual processing, and certificate issuance time.

| KPI | Before | After | Change |
|---|---:|---:|---:|
| Automated certificate generation | 20% | 85% | +65 percentage points |
| Manual certificate processing | 80% | 15% | -65 percentage points |
| Certificate issuance time | 1 business day | 10 minutes | Substantially reduced |

The automation rate increased by 65 percentage points, while the share of requests requiring manual processing decreased by the same amount.

The target operating model prioritizes automated certificate generation for supported certificate types while retaining manual processing for requests that require individual handling.

## 3. KPI Definitions

### 3.1. Automated Generation Rate

Measures the proportion of completed certificate requests processed through the automated route.

**Formula:**

`Automated Generation Rate = (Automatically Generated Certificates / Total Completed Requests) × 100`

A higher rate indicates that more certificate requests are completed without manual document preparation.

### 3.2. Manual Processing Rate

Measures the proportion of completed certificate requests that require staff involvement in processing or document preparation.

**Formula:**

`Manual Processing Rate = (Manually Processed Requests / Total Completed Requests) × 100`

A lower rate indicates reduced dependence on manual administrative work.

### 3.3. Certificate Issuance Time

Measures the time between certificate request submission and the point at which the completed document becomes available to the student.

**Formula:**

`Issuance Time = Certificate Availability Timestamp − Request Submission Timestamp`

The measurement uses the request creation timestamp and the timestamp when the certificate becomes available. This provides a consistent measure of end-to-end processing time.

## 4. Measurement Method

I use the following approach to evaluate process performance:

1. **Establish the baseline.** Record the automation rate, manual processing rate, and issuance time before the process improvement.
2. **Track request processing.** Record the request identifier, processing route, status transitions, and relevant timestamps.
3. **Measure the same KPIs after the improvement.** Apply the same definitions and calculation methods to the updated process.
4. **Compare the results.** Calculate absolute percentage-point changes for the processing rates and compare issuance time before and after the change.
5. **Review operational performance.** Examine results by certificate type and processing route to identify areas where manual handling remains necessary.

The comparison uses the same scope of certificate types and consistent KPI definitions to ensure that changes in performance are interpreted correctly.

## 5. Supporting Operational Indicators

In addition to the primary KPIs, the following indicators support ongoing process monitoring.

| Indicator | Calculation | Purpose |
|---|---|---|
| Template Coverage | Certificate types with an active, approved template / Total certificate types in scope × 100 | Measures how much of the certificate catalogue supports automated generation |
| PDF Generation Failure Rate | Failed automated generation attempts / Total automated generation attempts × 100 | Identifies technical issues affecting document generation |
| Manual Routing Rate | Requests routed to manual processing / Total submitted valid requests × 100 | Measures how frequently the automated route cannot be used |
| Request Completion Rate | Completed requests / Total submitted valid requests × 100 | Measures the proportion of valid requests that reach completion |

These indicators provide additional insight into why some requests require manual handling and where further process improvements can be made.

## 6. Business Impact

The improvement addresses three operational priorities:

- **Reduced administrative workload:** A greater share of certificates can be generated without manual document preparation.
- **Faster service delivery:** Students receive their certificates in less time.
- **More consistent processing:** Standardized templates, validation rules, and request statuses make the workflow easier to manage and monitor.

The combination of automated generation and a defined manual route allows the process to handle supported certificate types efficiently while preserving a path for requests that require staff intervention.

## 7. Summary

The key performance indicators show a shift from predominantly manual certificate processing to a process with a substantially higher level of automation.

| Objective | Performance Indicator | Result |
|---|---|---|
| Increase automation | Automated generation rate | 20% → 85% |
| Reduce manual effort | Manual processing rate | 80% → 15% |
| Accelerate certificate delivery | Certificate issuance time | 1 business day → 10 minutes |

These indicators connect the business objectives defined in `01-business-context-and-problem.md` with the process changes described in `04-to-be-process.md`. The requirements for system behaviour are documented in `06-requirements-and-acceptance-criteria.md`, while the test coverage is defined in `09-test-scenarios.md`.
