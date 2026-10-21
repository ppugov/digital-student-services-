# Root Cause Analysis — Digital Certificates

## 1. Objective

I analyzed the certificate issuance process to identify the causes of manual processing, administrative workload, and extended issuance time.

The analysis focuses on three areas: automated-template coverage, manual document preparation, and the sequence of activities required to complete a certificate request.

## 2. Root Causes

### 2.1. Limited Automated-Template Coverage

Automated certificate generation depends on the availability of a suitable template for the requested certificate type. When a matching template is unavailable, the Student Secretariat processes the request manually.

Limited template coverage restricts automation and increases the number of requests handled by employees.

**Impact:**
- 80% of certificate requests require manual processing.
- Automated generation covers 20% of requests.
- The Student Secretariat spends a significant share of its effort on repetitive document processing.

### 2.2. Manual Document Preparation

Requests that cannot be processed automatically require staff to prepare and generate certificates manually. These activities increase the amount of employee effort required to complete each request.

**Impact:**
- Increased workload associated with routine administrative tasks.
- Longer processing times for manually handled requests.
- Reduced staff capacity for other administrative responsibilities.

### 2.3. Multiple Staff-Dependent Processing Steps

The manual workflow includes student information verification, document preparation, certificate generation, and delivery. Each activity must be completed before the certificate reaches the student.

The need for employee involvement across these steps increases the effort required to process requests and extends the overall turnaround time.

**Impact:**
- Repetitive work across individual requests.
- Processing time depends on the completion of multiple administrative activities.
- Additional operational effort that can be reduced through standardization and automation.

## 3. Cause-and-Effect Analysis

The analysis establishes the following relationship:

**Limited template coverage → increased manual processing → higher administrative workload → longer certificate issuance time.**

Expanding template coverage reduces the number of requests requiring manual document preparation. Standardizing the remaining manual workflow improves processing consistency and reduces repetitive administrative effort.

## 4. Root Cause Summary

| Root cause | Process consequence | Business impact |
|---|---|---|
| Limited automated-template coverage | More requests require employee handling | High manual processing rate |
| Manual document preparation | Staff prepare and generate certificates individually | Increased administrative workload |
| Multiple staff-dependent activities | Requests pass through several employee-executed steps | Longer processing time |

## 5. Improvement Priorities

Based on the analysis, I defined five priorities for the target process:

1. **Expand automated-template coverage** to support more certificate types.
2. **Automate certificate generation** for requests that meet the applicable business rules and data requirements.
3. **Standardize manual processing** for requests that require employee intervention.
4. **Define routing and validation rules** to ensure that each request follows the appropriate processing path.
5. **Monitor process performance** using automation rate, manual processing rate, and certificate issuance time.

These priorities form the basis for the target process described in `04-to-be-process.md` and the functional requirements defined in `06-requirements-and-acceptance-criteria.md`.

## 6. Baseline and Target Metrics

| Metric | Baseline | Target |
|---|---:|---:|
| Automated certificate generation | 20% | 85% |
| Manual certificate processing | 80% | 15% |
| Certificate issuance time | 1 business day | 10 minutes |

These metrics define the performance gap between the current process and the target state. I use them as the basis for measuring process improvement and evaluating the business outcomes documented in `10-outcomes-and-measurement.md`.
