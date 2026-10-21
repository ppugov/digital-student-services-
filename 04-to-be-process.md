# Digital Certificates — TO-BE Process

## 1. Overview

I designed the target certificate issuance process to reduce manual document preparation and make certificate generation more efficient.

The process uses five components: Student, Frontend, Backend, PDF Generator, and Document Storage. Each component has a clearly defined responsibility, while the Backend coordinates the overall workflow.

The process covers the automated issuance of a certificate when a suitable template is already available. Requests with invalid input data are returned for correction before processing continues.

## 2. TO-BE BPMN Diagram

![TO-BE Digital Certificate Issuance Process](<./Digital Certificate Issuance — TO-BE_with_overlays (2).svg>)

[Open the TO-BE BPMN diagram (SVG)](<./Digital Certificate Issuance — TO-BE_with_overlays (2).svg>)

The diagram illustrates the interaction between the student and the system components, from submitting a certificate request to downloading the completed PDF document.

## 3. Process Flow

### 3.1. Certificate Request Submission

The student opens the university portal, selects the required certificate type, enters the requested information, and submits the request.

The Frontend collects the input and sends the request to the Backend for processing.

**Output:** Certificate request received by the Backend.

### 3.2. Request Validation

The Backend validates the incoming request before starting certificate generation. The validation covers required fields, data formats, and the information needed to identify the requested certificate.

If the request contains invalid or incomplete data, the Backend returns a validation error. The Frontend displays the error so the student can correct the information and submit the request again.

If validation succeeds, the Backend continues processing.

**Output:** Validated certificate request.

### 3.3. Template Retrieval

The Backend determines the template associated with the selected certificate type and requests the corresponding file from Document Storage.

Document Storage retrieves and returns the requested template. It does not select templates or apply business rules; those responsibilities remain with the Backend.

**Output:** Certificate template available for document generation.

### 3.4. PDF Generation

The Backend prepares the generation request using the certificate template and the required student data. It then sends the inputs to the PDF Generator.

The PDF Generator populates the template and returns the completed PDF document to the Backend.

**Output:** Generated certificate PDF.

### 3.5. Document Storage and Request Completion

The Backend submits the generated PDF to Document Storage. The storage component saves the file and returns a document reference.

After receiving the document reference, the Backend registers the certificate issuance and updates the request status to `COMPLETED`.

The Backend then returns the certificate reference to the Frontend.

**Output:** Stored certificate linked to a completed request.

### 3.6. Certificate Delivery

The Frontend displays the certificate download option to the student. The student accesses and downloads the completed PDF.

**Output:** Certificate available to the student.

## 4. System Responsibilities

| Component | Responsibility |
|---|---|
| Student | Selects the certificate type, submits the request, corrects validation errors, and downloads the certificate |
| Frontend | Collects request data, submits requests to the Backend, displays validation errors, and provides access to the completed certificate |
| Backend | Validates requests, determines the required template, coordinates document generation and storage, registers issuance, and manages request status |
| PDF Generator | Generates the PDF document from the supplied template and student data |
| Document Storage | Retrieves existing templates, stores generated PDF files, and returns document references |

The separation of responsibilities keeps business logic within the Backend and limits the PDF Generator and Document Storage to their respective technical operations.

## 5. Business Rules

| ID | Rule |
|---|---|
| BR-01 | A certificate request must specify the required certificate type. |
| BR-02 | The Backend must validate incoming request data before processing continues. |
| BR-03 | Invalid requests must be returned to the Frontend with validation errors. |
| BR-04 | The Backend determines which template corresponds to the selected certificate type. |
| BR-05 | The PDF Generator receives the template and the required student data from the Backend. |
| BR-06 | Document Storage performs file retrieval and storage operations initiated by the Backend. |
| BR-07 | The Backend must receive a document reference before marking the request as completed. |
| BR-08 | The Frontend makes the certificate available to the student after the Backend confirms completion. |

## 6. Improvements Compared with the AS-IS Process

| Area | AS-IS | TO-BE |
|---|---|---|
| Certificate generation | Automated generation covers a limited share of requests | Broader coverage of automated certificate generation |
| Document preparation | Staff manually prepare and generate many certificates | The PDF Generator produces certificates using existing templates |
| Request validation | Student information is checked during administrative processing | Backend validation takes place before generation |
| Component responsibilities | Manual processing requires employee involvement across several activities | Frontend, Backend, PDF Generator, and Document Storage have defined responsibilities |
| Document handling | Manual preparation and delivery form part of the workflow | Generated PDFs are stored and referenced by the Backend |
| Completion status | Completion depends on the processing and delivery activities | The Backend records completion after successful storage |

## 7. Target Performance Metrics

The process improvement is measured against the baseline and target values defined for the project.

| Metric | Baseline | Target |
|---|---:|---:|
| Automated certificate generation | 20% | 85% |
| Manual certificate processing | 80% | 15% |
| Certificate issuance time | 1 business day | 10 minutes |

The target is to increase automated generation, reduce manual processing, and shorten certificate issuance time. The measurement methodology and performance evaluation are documented in `10-outcomes-and-measurement.md`.

## 8. Related Requirements

The target process defines the expected system behaviour and the responsibilities of each component. The implementation requirements are detailed in the following documents:

- `05-template-coverage-and-business-rules.md` — template coverage and business rules.
- `06-requirements-and-acceptance-criteria.md` — functional requirements, non-functional requirements, and acceptance criteria.
- `07-proposed-api-contract.yaml` — API contract.
- `08-proposed-data-model.md` — data model.
- `09-test-scenarios.md` — test scenarios.
- `10-outcomes-and-measurement.md` — performance measurement and business outcomes.
