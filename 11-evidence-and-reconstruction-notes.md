# Digital Certificates — Evidence and Project Documentation

## 1. Purpose

This document organizes the key project artefacts and links business objectives to process analysis, system design, testing, and performance measurement.

It provides a single reference for the decisions made throughout the certificate issuance improvement process and the documentation supporting those decisions.

## 2. Key Project Evidence

| Area | Evidence / Deliverable | Purpose |
|---|---|---|
| Business Analysis | `01-business-context-and-problem.md` | Defines the business context, problem, objectives, and performance indicators |
| Current-State Analysis | `02-as-is-process.md` | Documents the existing certificate issuance workflow |
| Root Cause Analysis | `03-root-cause-analysis.md` | Identifies the factors contributing to manual processing and extended issuance time |
| Target Process | `04-to-be-process.md` and BPMN diagram | Defines the target workflow and interactions between system components |
| Business Rules | `05-template-coverage-and-business-rules.md` | Defines template selection, processing routes, and completion conditions |
| Requirements Engineering | `06-requirements-and-acceptance-criteria.md` | Specifies functional requirements, non-functional requirements, and acceptance criteria |
| API Design | `07-proposed-api-contract.yaml` | Defines API endpoints, request and response schemas, and HTTP responses |
| Data Modeling | `08-proposed-data-model.md` and ER diagram | Defines the data entities, attributes, keys, and relationships |
| Quality Assurance | `09-test-scenarios.md` | Defines test scenarios for functional behaviour, routing, access control, and document generation |
| Performance Measurement | `10-outcomes-and-measurement.md` | Defines business KPIs, calculation methods, and performance targets |

## 3. Business Problem to Solution Traceability

The following table connects the main business challenges to the analysis, solution design, and validation activities.

| Business Challenge | Analysis | Solution Decision | Validation |
|---|---|---|---|
| Low automated-generation rate | Review automation coverage and manual processing | Expand automated generation for supported certificate types | TC-02, TC-05, TC-06 |
| High manual-processing rate | Identify requests that require employee intervention | Define automated and manual processing routes | TC-06, TC-07, TC-15 |
| Extended certificate issuance time | Measure request-to-issuance turnaround time | Reduce manual document preparation through automated PDF generation | TC-05 and KPI measurement |
| Invalid request data | Define request validation rules | Validate required fields before processing | TC-03, TC-04 |
| Incorrect or ambiguous template selection | Define template mapping and eligibility rules | Require exactly one eligible template for automated generation | TC-02, TC-07 |
| Incomplete certificate issuance | Define document storage and completion conditions | Mark a request as completed only after successful generation, storage, and availability | TC-05, TC-09, TC-13 |

## 4. Performance Evidence

The project uses three primary performance indicators to evaluate certificate issuance.

| KPI | Baseline | Result / Target | Absolute Change |
|---|---:|---:|---:|
| Automated certificate generation | 20% | 85% | +65 percentage points |
| Manual certificate processing | 80% | 15% | -65 percentage points |
| Certificate issuance time | 1 business day | 10 minutes | Reduced to 10 minutes |

The automation and manual-processing rates are complementary indicators: increasing the automated share reduces the proportion of requests handled manually.

Issuance time measures the elapsed period between request submission and certificate availability. Consistent definitions and measurement periods are required when comparing results.

## 5. Data Required for Performance Measurement

To calculate and reproduce the KPIs, the measurement process uses the following information:

| Data Point | Purpose |
|---|---|
| Request ID | Identify each certificate request |
| Request creation timestamp | Establish the beginning of the measurement period |
| Processing route | Distinguish automated and manual requests |
| Request status | Identify successfully completed requests |
| Certificate availability timestamp | Establish the end of the issuance-time measurement |
| Template ID and version | Trace the template used for automated generation |
| Generation outcome | Identify successful and failed generation attempts |

These data points support calculation of automation rate, manual-processing rate, issuance turnaround time, and generation failure rate.

## 6. Document Relationships

The project documentation follows a connected analysis and design sequence:

1. **Business context and current state:** Documents 01–03 define the business problem, existing workflow, and causes of inefficiency.
2. **Target process and rules:** Documents 04–05 define the intended workflow and the rules governing certificate generation.
3. **System design:** Documents 06–08 translate the target process into requirements, API contracts, and a data model.
4. **Verification:** Document 09 defines test scenarios linked to requirements and expected system behaviour.
5. **Business outcomes:** Document 10 defines the KPIs and measurement approach used to evaluate process performance.

This structure maintains traceability between business objectives, process decisions, system requirements, test coverage, and performance indicators.

## 7. Summary

The project documentation provides an integrated view of the digital certificate issuance process, from business problem analysis to system design, validation, and KPI measurement.

The artefacts can be reviewed together to understand the rationale behind the target process, how its behaviour is specified, how the design is validated, and how improvements in certificate issuance are evaluated.
