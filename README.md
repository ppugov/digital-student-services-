# Digital Student Services: Digital Certificates

**Business Analysis | Systems Analysis | Education Technology**

## Project Overview

Digital certificate issuance within the GOMP / smart_edu university platform at Be Smart S.r.l. The project focused on streamlining certificate-generation workflows, reducing manual processing, and improving service efficiency through business process optimization and systems analysis.

The scope covered stakeholder requirements, business process modeling, functional and non-functional requirements, API specifications, data modeling, and solution testing.

## Business Problem & Results

The certificate-issuance process involved substantial manual processing, creating opportunities to increase automation and reduce turnaround time.

| Metric | Before | After |
|---|---:|---:|
| Automated certificate generation | 20% | 85% |
| Manual processing | 80% | 15% |
| Certificate issuance time | 1 business day | 10 minutes |

## Analysis & Solution Design

1. **Stakeholder Analysis & Requirements Elicitation**  
   Analyzed user needs across students, the Student Secretariat, and University Administration through interviews, workshops, and discovery sessions.

2. **Business Process Analysis**  
   Modeled AS-IS workflows, identified improvement opportunities, and designed TO-BE processes using BPMN.

3. **Requirements Engineering**  
   Specified functional and non-functional requirements for frontend and backend behavior, including business rules, data validation, status transitions, error handling, user stories and acceptance criteria.

4. **Systems & Data Design**  
   Defined REST API contracts, request and response structures, integration logic, and data entities and relationships.

5. **Testing & Acceptance**  
   Prepared functional, integration, negative, security, performance, and edge-case test scenarios to validate system behavior against requirements.

## Key Deliverables

### Business Analysis
- [Business Context & Problem Statement](01-business-context-and-problem.md)
- [AS-IS Process](02-as-is-process.md)
- [Root-Cause Analysis](03-root-cause-hypotheses.md)
- [TO-BE Process](04-to-be-process.md)
- [Business Rules & Template Coverage](05-template-coverage-and-business-rules.md)

### Requirements & System Design
- [Requirements & Acceptance Criteria](06-requirements-and-acceptance-criteria.md)
- [REST API Contract — OpenAPI](07-proposed-api-contract.yaml)
- [Data Model](08-proposed-data-model.md)

### Testing & Performance
- [Test Scenarios](09-test-scenarios.md)
- [Outcomes & Measurement](10-outcomes-and-measurement.md)
- [Evidence & Project Documentation](11-evidence-and-project-documentation.md)

## Core Competencies

- **Business Analysis:** stakeholder analysis, requirements elicitation, process optimization, business rules.
- **Requirements Engineering:** FR/NFR, user stories, use cases, acceptance criteria.
- **Systems Analysis:** REST API, OpenAPI/Swagger, JSON, integration logic, error handling.
- **Data Modeling:** ERD, SQL, PostgreSQL, data validation.
- **Quality Assurance:** functional, integration, negative, security, performance, and edge-case testing.

## Performance Measurement

The key indicators are automated-generation rate, manual-processing rate, and certificate-issuance time. Comparing these metrics before and after the improvement provides a basis for evaluating process performance.
