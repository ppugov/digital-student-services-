# Digital Certificates — Template Coverage and Business Rules

## 1. Purpose

This document defines the business rules that govern automated certificate generation and request processing.

It answers three key questions:

1. **How does the system select a certificate template?**
2. **What rules must be followed before a certificate can be generated?**
3. **When can a certificate request be considered completed?**

These rules determine how the Backend processes requests, selects templates, coordinates document generation, and confirms successful certificate issuance.

## 2. Template Selection

The Backend selects a template based on the certificate type specified in the student's request.

| Condition | System Behaviour | Processing Route |
|---|---|---|
| Exactly one active template matches the requested certificate type | Retrieve the template and continue automatic generation | Automated |
| No active, approved template matches the requested certificate type | Route the request to the Student Secretariat | Manual processing |
| Multiple active, approved templates match the requested certificate type | Stop automatic selection and route the request for review | Manual review |

Only active, approved templates can be used for automatic certificate generation. If the system cannot identify exactly one eligible template, automatic generation must not proceed.

## 3. Business Rules

| ID | Rule | Expected Behaviour |
|---|---|---|
| BR-01 | Certificate Type | Every request must specify a supported certificate type. |
| BR-02 | Request Validation | The Backend must validate required fields and data formats before processing continues. |
| BR-03 | Template Selection | The Backend determines the appropriate template using the requested certificate type. |
| BR-04 | Template Eligibility | Only active, approved templates are eligible for automatic generation. |
| BR-05 | Unique Template Match | Automatic generation proceeds only when exactly one eligible template matches. |
| BR-06 | Required Student Data | The Backend must obtain all required student data before requesting PDF generation. |
| BR-07 | Successful Generation | The generated PDF must be returned successfully before the Backend proceeds to storage. |
| BR-08 | Successful Storage | The Backend must receive a document reference from Document Storage before completing the request. |
| BR-09 | Request Completion | A request can be marked `COMPLETED` only after the certificate has been generated, stored, and made available to the student. |
| BR-10 | Processing Traceability | The system records the request status, processing route, and template identifier and version used. |
| BR-11 | Manual Routing Reason | Requests sent for manual processing or review must retain the reason for that decision. |

## 4. Template Lifecycle

Templates follow a controlled lifecycle to ensure that only approved templates are used for certificate generation.

| Status | Meaning |
|---|---|
| `DRAFT` | The template is being created or edited. |
| `IN_REVIEW` | The template is awaiting approval. |
| `APPROVED` | The template has passed the approval process but is not yet active. |
| `ACTIVE` | The approved template is available for certificate generation. |
| `RETIRED` | The template is no longer available for new requests. |

A template must be approved before it can become active. Each template has an identifier and version, allowing the system to identify which version was used to generate a certificate.

## 5. Request Completion

The Backend manages the request status throughout the certificate issuance process.

| Status | Meaning |
|---|---|
| `SUBMITTED` | The request has been received. |
| `PROCESSING` | The request is being processed. |
| `MANUAL_REVIEW_REQUIRED` | The request requires intervention by the Student Secretariat. |
| `COMPLETED` | The certificate has been generated, stored, and made available to the student. |
| `FAILED` | Processing could not be completed because of an error. |

The Backend is responsible for updating the request status. The PDF Generator reports the result of document generation, while Document Storage performs file retrieval and storage operations.

A request must not be marked `COMPLETED` before the certificate is stored and made available to the student.

## 6. Relationship to the TO-BE Process

The TO-BE process in `04-to-be-process.md` shows the successful automated route when the request is valid and a suitable active template is available.

This document defines the rules governing that process, including template selection, required data, document storage, and request completion. It also specifies how requests are routed when an eligible template cannot be identified.

The implementation of these rules is detailed in `06-requirements-and-acceptance-criteria.md`.
