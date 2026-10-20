# Digital Certificates — Requirements & Acceptance Criteria

**Status:** Proposed requirements for the reconstructed portfolio scenario

## 1. Functional requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | The system shall allow a student to select a certificate type from the types available to that student. | Must |
| FR-02 | The system shall validate that the selected certificate type exists and is enabled for requests. | Must |
| FR-03 | The system shall determine whether exactly one active, approved template is mapped to the selected certificate type. | Must |
| FR-04 | If an eligible template exists, the system shall route the request to automated generation. | Must |
| FR-05 | If no eligible template exists, the system shall route the request to manual processing and record the reason. | Must |
| FR-06 | If template mapping is ambiguous, the system shall not select a template arbitrarily and shall create an exception for resolution. | Must |
| FR-07 | The system shall expose the current request status to authorized users. | Must |
| FR-08 | After successful generation, the system shall associate the generated document with the request and make it available to the authorized student. | Must |
| FR-09 | The system shall record the selected template version for an automatically generated certificate. | Should |
| FR-10 | The system shall retain the route and outcome of the request for operational reporting. | Should |

## 2. User stories

### US-01 — Submit a certificate request

**As a student,** I want to select the certificate type I need, **so that** I can submit a request for the appropriate document.

**Acceptance criteria**

- Given the student is authorized to access the service, when the student selects an enabled certificate type and submits the request, then the system creates a request and returns its identifier.
- Given the selected certificate type is invalid or disabled, when the student submits the request, then the system rejects the submission with a clear validation message.

### US-02 — Automatically route a supported certificate type

**As a student,** I want supported certificate types to be generated automatically, **so that** I can receive the document without unnecessary manual handling.

**Acceptance criteria**

- Given exactly one active, approved template is mapped to the selected type, when the request is accepted, then the system routes it to automated generation.
- Given the request is successfully generated, when processing completes, then the request status becomes `ISSUED` and the authorized student can access the document.
- Given generation fails, when the failure is detected, then the request must not be marked `ISSUED` and the failure must be recorded.

### US-03 — Route an unsupported certificate type to manual processing

**As a Student Secretariat employee,** I want requests without an applicable automated template to be identified and routed to manual processing, **so that** unsupported requests can still be handled.

**Acceptance criteria**

- Given no active, approved template is mapped to the selected type, when the request is submitted, then its route is set to manual processing.
- The request status becomes `MANUAL_REVIEW_REQUIRED` or an equivalent agreed status.
- The system records the reason for manual routing.
- The student can see that the request is being processed, without being shown internal operational details.

### US-04 — Prevent ambiguous template selection

**As a system owner,** I want the system to detect ambiguous template mappings, **so that** a certificate is not generated with an arbitrary template.

**Acceptance criteria**

- Given more than one active, approved template is mapped to the same request type, when the system resolves the template, then it does not generate the certificate automatically.
- The system records an exception and makes it available for authorized resolution.

## 3. Non-functional considerations

These are proposed quality requirements; they should be quantified and agreed with stakeholders before implementation.

- **Access control:** Only an authorized student or authorized staff member can access a request and its document.
- **Traceability:** The system can identify when a request was created, which route was selected, and how processing ended.
- **Reliability:** A failed document-generation attempt must not produce a false `ISSUED` status.
- **Usability:** The student receives a clear status and actionable information where appropriate.
- **Maintainability:** Template mappings and versions should be manageable without undocumented routing behavior.

## 4. Dependencies and open decisions

- The real catalogue of certificate types must be supplied by the business owner.
- The source of certificate data and authorization checks must be defined.
- The manual-processing owner and operational queue must be agreed.
- The required audit-retention policy and document-access rules must be confirmed.
- Any service-level targets must be agreed and measured; none are invented here.
