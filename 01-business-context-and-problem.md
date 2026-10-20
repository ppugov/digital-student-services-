# Digital Certificates — Business Context & Problem Statement

Project:** Digital Student Services  
**Company:** Be Smart S.r.l.  
**Platform:** GOMP / smart_edu  
**Role represented:** Business / Systems Analyst  
**Document status:** Portfolio case study

## 1. Business context

Digital Certificates was one functional area within a university digitalization initiative on the GOMP / smart_edu platform. The initiative included improvements to the certificate-issuance process, with reported objectives of increasing automation and reducing processing time and manual effort.

The available project summary identifies certificate generation, automated data validation, and certificate lifecycle handling as relevant areas of work.

## 2. Problem statement

The available project summary describes a partially automated certificate-issuance process. At baseline, automated generation was reported at 20%, manual processing at 80%, and certificate issuance time at one business day.

For this portfolio case, the working scenario assumes that automated generation was available for selected certificate types, while certificate types without an applicable automated template required manual processing. This scenario provides a coherent basis for demonstrating process analysis and system specification, but it is not a verified statement about the original production workflow.

**Problem to analyze:** How can the certificate-issuance process increase automation coverage across certificate types while retaining a controlled manual route for types that cannot be generated automatically?

## 3. Business objectives

1. Increase the proportion of requests handled through automated certificate generation.
2. Reduce manual document-preparation effort.
3. Reduce certificate-issuance turnaround time.
4. Make the processing route explicit and traceable for each request.
5. Preserve a controlled route for certificate types that are not supported by an active automated template.

Objectives 1–3 align with the reported project outcomes. Objective 4–5 are proposed design objectives for this portfolio reconstruction.

## 4. Baseline indicators

| Indicator | Reported baseline |
|---|---:|
| Automated generation | 20% |
| Manual processing | 80% |
| Certificate issuance time | 1 business day |

The source summary does not specify the measurement period, sample size, inclusion criteria, or exact operational definition of each metric. See [Outcomes and measurement considerations](10-outcomes-and-measurement.md).

## 5. Scope

### In scope

- Certificate request intake at a high level
- Classification of certificate types
- Matching certificate types to automated templates
- Routing a request to automated or manual processing
- Generating and making a certificate available
- Business rules, functional requirements, API design, conceptual data model, and test scenarios for the proposed workflow

### Out of scope

- Reconstructing the exact original production architecture
- Claiming actual certificate types, APIs, database tables, or status names not supported by the available materials
- Other Digital Student Services modules, including administrative procedures, document storage, and online application submission
- Legal or regulatory requirements not documented in the available project materials

## 6. Stakeholders in the proposed model

The following are modeled stakeholders for the portfolio scenario, not a confirmed original stakeholder list:

| Stakeholder | Proposed interest |
|---|---|
| Student | Submit a certificate request and obtain the document |
| Student Secretariat / university staff | Handle requests that cannot follow the automated route |
| University administration | Define supported certificate types and operational rules |
| Platform / development team | Implement routing, template mapping, document generation, and status handling |

## 7. Key analytical question

What rules determine whether a requested certificate type can be generated automatically, and what should happen when no active template supports that type?
