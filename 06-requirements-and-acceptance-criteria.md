# Digital Certificates — Requirements and Acceptance Criteria

## 1. Purpose

This document defines the functional and non-functional requirements for the digital certificate issuance process.

It answers three key questions:

1. What must the system do to process a certificate request?
2. What conditions must be satisfied for the request to be completed successfully?
3. How do we verify that the system behaves as expected?

I derived the requirements from the TO-BE process and the business rules defined in the previous documents.

## 2. Functional Requirements

Functional requirements describe the behaviour the system must provide.

| ID | Component | Requirement | Priority |
|---|---|---|---|
| FR-01 | Frontend | The system shall allow a student to select an available certificate type and submit a request. | Must |
| FR-02 | Backend | The Backend shall validate incoming requests, including required fields and data formats, before processing continues. | Must |
| FR-03 | Backend | The Backend shall return a validation error when a request contains missing or invalid data. | Must |
| FR-04 | Backend | The Backend shall retrieve the student data required to generate the selected certificate. | Must |
| FR-05 | Backend | The Backend shall identify the template mapped to the requested certificate type. | Must |
| FR-06 | Backend | The Backend shall proceed with automatic generation only when exactly one active, approved template matches the requested certificate type. | Must |
| FR-07 | Document Storage | Document Storage shall return the requested template file when the Backend requests it. | Must |
| FR-08 | Backend / PDF Generator | The Backend shall provide the selected template and required student data to the PDF Generator. | Must |
| FR-09 | PDF Generator | The PDF Generator shall create a PDF document using the supplied template and student data. | Must |
| FR-10 | Backend / Document Storage | The Backend shall submit the generated PDF to Document Storage and receive a document reference. | Must |
| FR-11 | Backend | The Backend shall update the request status to `COMPLETED` only after the certificate has been generated, stored, and made available to the student. | Must |
| FR-12 | Frontend | The system shall make the completed certificate available to the authorized student. | Must |
| FR-13 | Backend | The system shall route requests without an eligible template to manual processing. | Must |
| FR-14 | Backend | The system shall prevent automatic template selection when multiple eligible templates match the requested certificate type. | Must |
| FR-15 | Backend | The system shall record the request status, processing route, and template identifier and version used, where applicable. | Should |
| FR-16 | Frontend / Backend | The system shall allow authorized users to view the current request status. | Must |

## 3. User Stories and Acceptance Criteria

### US-01 — Submit a Certificate Request

**As a student,** I want to select the certificate type I need and submit a request, so that I can obtain the appropriate document.

**Acceptance criteria**

- **AC-01.1:** Given a student selects an available certificate type and provides valid required information, when the student submits the request, then the Backend accepts the request for processing.
- **AC-01.2:** Given a request contains missing or invalid data, when the Backend validates it, then the system returns a validation error and the Frontend displays a clear message.
- **AC-01.3:** Given a validation error is displayed, when the student corrects the input and resubmits the request, then the Backend validates the updated request.

### US-02 — Validate and Route a Request

**As a system,** I need to validate each incoming request and determine the appropriate processing route, so that certificate generation follows the defined business rules.

**Acceptance criteria**

- **AC-02.1:** Given a valid request, when the Backend completes validation, then processing continues to template selection.
- **AC-02.2:** Given an invalid request, when validation fails, then automatic certificate generation does not begin.
- **AC-02.3:** Given exactly one active, approved template matches the requested certificate type, when the Backend resolves the template, then the request follows the automated route.
- **AC-02.4:** Given no eligible template matches the requested type, when the Backend resolves the template, then the request is routed to manual processing.
- **AC-02.5:** Given multiple eligible templates match the requested type, when the Backend resolves the template, then it does not select a template arbitrarily and routes the request for review.

### US-03 — Generate a Certificate Automatically

**As a student,** I want supported certificate types to be generated automatically, so that I can receive my certificate without unnecessary manual processing.

**Acceptance criteria**

- **AC-03.1:** Given the request is valid and exactly one eligible template matches the selected certificate type, when the Backend retrieves the template and required student data, then it submits the required inputs to the PDF Generator.
- **AC-03.2:** Given the PDF Generator receives a valid template and the required student data, when generation succeeds, then it returns the generated PDF to the Backend.
- **AC-03.3:** Given the PDF Generator does not return a successfully generated PDF, then the Backend does not mark the request as `COMPLETED`.

### US-04 — Store and Deliver the Certificate

**As a student,** I want the completed certificate to be stored and made available to me, so that I can access and download the document.

**Acceptance criteria**

- **AC-04.1:** Given the PDF Generator successfully creates a certificate, when the Backend submits it to Document Storage, then Document Storage saves the document and returns a document reference.
- **AC-04.2:** Given the Backend receives a valid document reference, when the certificate is made available to the student, then the request status can be updated to `COMPLETED`.
- **AC-04.3:** Given the document has not been stored successfully, then the request must not be marked as `COMPLETED`.
- **AC-04.4:** Given the request is completed, when the authorized student accesses the request, then the certificate is available for download.

### US-05 — Handle Requests Requiring Manual Processing

**As a Student Secretariat employee,** I want requests that cannot be processed automatically to be identified and routed for manual handling, so that students can still obtain the required certificate.

**Acceptance criteria**

- **AC-05.1:** Given no eligible template matches the requested certificate type, when the Backend evaluates template coverage, then it assigns the request to manual processing.
- **AC-05.2:** Given multiple eligible templates match the requested type, when the Backend evaluates template coverage, then the request is sent for review instead of automatic generation.
- **AC-05.3:** Given a request is routed for manual processing or review, then the system records the routing reason and makes the request status visible to authorized users.

## 4. Non-Functional Requirements

Non-functional requirements define the quality, security, reliability, and performance expected from the system.

| ID | Category | Requirement | Verification |
|---|---|---|---|
| NFR-01 | Access Control | Only authorized students and staff shall access certificate requests and documents permitted for their roles. | Verify access permissions for authorized and unauthorized users. |
| NFR-02 | Data Integrity | The system shall associate each generated certificate with the correct request and student. | Verify the relationship between request, student, and generated document. |
| NFR-03 | Reliability | The system shall not mark a request as `COMPLETED` if generation or document storage fails. | Simulate an unsuccessful generation or storage operation and verify the request status. |
| NFR-04 | Traceability | The system shall retain the request identifier, processing route, final status, and template version used, where applicable. | Verify that the required information can be retrieved for a completed request. |
| NFR-05 | Usability | The Frontend shall display understandable validation messages and the current request status. | Verify the messages and status displayed for valid and invalid requests. |
| NFR-06 | Maintainability | Template mappings and template versions shall be identifiable and manageable without changing the request-processing logic for each individual certificate type. | Verify that a template mapping can be maintained through the designated configuration mechanism. |
| NFR-07 | Performance | For requests supported by the automated route, the target certificate issuance time shall be 10 minutes or less from request submission to certificate availability. | Measure elapsed time between request submission and certificate availability. |

## 5. Scope of the Requirements

The requirements cover the following workflow:

1. Request submission through the Frontend.
2. Backend validation of the incoming request.
3. Retrieval of student data and selection of the applicable template.
4. PDF generation using the PDF Generator.
5. Storage of the generated certificate in Document Storage.
6. Request completion and certificate availability to the student.
7. Routing to manual processing when automatic generation is not applicable.

The requirements also define the expected behaviour for invalid requests and ambiguous template mappings.

Detailed implementation of retry mechanisms, background workers, and recovery from individual technical failures is outside the scope of the current process design.

## 6. Traceability to Other Documents

| Document | Relationship |
|---|---|
| `01-business-context-and-problem.md` | Defines the business problem and expected outcomes. |
| `02-as-is-process.md` | Describes the current certificate issuance process. |
| `03-root-cause-analysis.md` | Identifies the causes of manual processing and extended issuance time. |
| `04-to-be-process.md` | Defines the target process and component interactions. |
| `05-template-coverage-and-business-rules.md` | Defines template selection, processing routes, and completion rules. |
| `07-proposed-api-contract.yaml` | Specifies the API contract supporting request processing. |
| `08-proposed-data-model.md` | Defines the data entities needed to support the process. |
| `09-test-scenarios.md` | Provides test scenarios for validating the requirements. |
| `10-outcomes-and-measurement.md` | Defines performance measurement and business outcomes.
