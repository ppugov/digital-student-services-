# Digital Certificates — Test Scenarios

## 1. Purpose

This document defines the test scenarios used to verify the digital certificate issuance process.

It answers three key questions:

1. Does the system validate and process certificate requests correctly?
2. Does the system generate, store, and deliver the correct certificate?
3. Does the system handle invalid requests and requests that cannot be processed automatically?

Each test scenario defines the preconditions, test action, and expected result.

## 2. Functional Test Scenarios

| ID    | Scenario                                         | Preconditions / Input                                                                | Expected Result                                                                                            | Type         |
| ----- | ------------------------------------------------ | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- | ------------ |
| TC-01 | Retrieve certificate types                       | Student is authenticated                                                             | API returns the available certificate types with their identifiers and names                               | Positive     |
| TC-02 | Submit a valid certificate request               | Certificate type is enabled; exactly one active, approved template matches           | Backend accepts the request and selects the automated route                                                | Positive     |
| TC-03 | Submit request with missing certificate type     | `certificateTypeId` is missing                                                       | API returns `400 Bad Request`; the request is not processed                                                | Negative     |
| TC-04 | Submit request with unavailable certificate type | Certificate type does not exist or is disabled                                       | API returns `422 Unprocessable Entity`; automatic generation does not start                                | Negative     |
| TC-05 | Generate certificate successfully                | Valid request, eligible template, and required student data are available            | PDF Generator returns the generated PDF; the document is stored and the request status becomes `COMPLETED` | Positive     |
| TC-06 | Request without an eligible template             | No active, approved template matches the requested certificate type                  | Request is routed to manual processing; status becomes `MANUAL_REVIEW_REQUIRED`                            | Routing      |
| TC-07 | Multiple eligible templates match                | More than one active, approved template matches the requested certificate type       | Backend does not select a template arbitrarily; request is routed for review                               | Edge case    |
| TC-08 | Retrieve request status                          | Request exists and caller is authorized                                              | API returns the request identifier, current status, and processing route                                   | Positive     |
| TC-09 | Download issued certificate                      | Request is `COMPLETED`; caller is authorized                                         | API returns the stored certificate as `application/pdf`                                                    | Positive     |
| TC-10 | Download certificate before completion           | Certificate is not yet available                                                     | API returns `409 Conflict`; no incomplete document is presented as issued                                  | Negative     |
| TC-11 | Access another student's request                 | Caller is not authorized to access the requested record                              | Access is denied without exposing protected request or document data                                       | Security     |
| TC-12 | PDF generation failure                           | PDF Generator does not produce the certificate successfully                          | Request is not marked `COMPLETED`; the failure is recorded                                                 | Negative     |
| TC-13 | Document storage failure                         | Generated PDF cannot be stored successfully                                          | Request is not marked `COMPLETED`; the certificate is not made available for download                      | Negative     |
| TC-14 | Verify template traceability                     | Automated certificate generation completes successfully                              | The request and issued document can be traced to the template identifier and version used                  | Traceability |
| TC-15 | Complete manual processing                       | Request is awaiting manual processing; Secretariat completes the required activities | Generated document is stored, made available to the student, and the request status becomes `COMPLETED`    | Positive     |
| TC-16 | Automated issuance within target time           | Valid request follows the automated route; request and availability timestamps are captured | Certificate is available within 10 minutes of submission; elapsed time is recorded | Performance |
| TC-17 | Verify template mapping maintainability         | Authorized configuration mechanism is available; certificate type and template exist | Template mapping can be maintained without changing request-processing logic | Maintainability |

## 3. API Test Coverage

The API endpoints are validated against the expected request and response contracts.

| Endpoint                                                | Tests                             | Expected Behaviour                                                     |
| ------------------------------------------------------- | --------------------------------- | ---------------------------------------------------------------------- |
| `GET /api/v1/certificate-types`                         | TC-01                             | Returns available certificate types                                    |
| `POST /api/v1/certificate-requests`                     | TC-02, TC-03, TC-04, TC-06, TC-07 | Validates the request and selects the appropriate processing route     |
| `GET /api/v1/certificate-requests/{requestId}`          | TC-08, TC-11                      | Returns request information only to authorized callers                 |
| `GET /api/v1/certificate-requests/{requestId}/document` | TC-09, TC-10, TC-11               | Returns the PDF only when it is available and the caller is authorized |

TC-05, TC-12, TC-13, TC-14, and TC-15 cover processing and integration behaviour across the Backend, PDF Generator, Document Storage, and Student Secretariat. TC-16 verifies the issuance-time target, and TC-17 verifies template-mapping maintainability.

## 4. Requirements Traceability

| Requirement                                                   | Related Test Scenarios |
| ------------------------------------------------------------- | ---------------------- |
| FR-01 — Certificate type selection and submission             | TC-01, TC-02           |
| FR-02, FR-03 — Request validation                             | TC-03, TC-04           |
| FR-04, FR-05, FR-06 — Student data and template selection     | TC-02, TC-06, TC-07    |
| FR-07, FR-08, FR-09 — Template retrieval and PDF generation   | TC-05, TC-12           |
| FR-10, FR-11 — Document storage and request completion        | TC-05, TC-09, TC-13    |
| FR-12, FR-16 — Certificate availability and request status    | TC-08, TC-09, TC-10    |
| FR-13, FR-14 — Manual routing and ambiguous template mappings | TC-06, TC-07, TC-15    |
| FR-15 — Processing and template traceability                  | TC-14                  |
| NFR-01 — Access control                                       | TC-08, TC-09, TC-11    |
| NFR-02 — Data integrity                                       | TC-05, TC-09, TC-14    |
| NFR-03 — Reliability                                          | TC-12, TC-13           |
| NFR-04 — Traceability                                         | TC-14                  |
| NFR-05 — Usability                                            | TC-03, TC-04, TC-08    |
| NFR-06 — Maintainability                                      | TC-17                  |
| NFR-07 — Performance                                          | TC-16                  |

## 5. Test Data

Use test data that covers the following conditions:

- Enabled and disabled certificate types.
- One active, approved template, no eligible template, and multiple eligible templates.
- Valid and invalid certificate requests.
- Student data required by the selected template.
- Successfully generated PDFs and controlled generation or storage failures.
- Authorized and unauthorized access to requests and documents.

All test records and document contents should use synthetic data rather than real student information.

## 6. Expected Outcome

The test scenarios verify that certificate requests follow the business rules, the correct processing route is selected, and certificates are generated and stored before a request is marked `COMPLETED`.

The tests also verify that invalid requests are rejected, ambiguous template mappings do not result in arbitrary template selection, and only authorized users can access certificate data.

The performance target for automated issuance is defined in `06-requirements-and-acceptance-criteria.md` and measured according to `10-outcomes-and-measurement.md`.
