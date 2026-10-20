# Digital Certificates — Template Coverage & Business Rules

**Status:** Proposed specification for the reconstructed portfolio scenario

## 1. Template coverage model

The actual certificate names and template catalogue are not available in the source materials. To avoid inventing production details, the table below uses generic illustrative categories only.

| Illustrative category | Template mapping | Proposed processing route | Notes |
|---|---|---|---|
| Supported certificate type | One active approved template exists | Automated | Demonstrates the automated route; not an actual certificate name |
| Unsupported certificate type | No active approved template exists | Manual | Demonstrates the manual route; not an actual certificate name |
| Type with conflicting or ambiguous mappings | More than one eligible template is found | Exception / manual review | Proposed safeguard to prevent arbitrary template selection |

For implementation, these rows would be replaced by a validated catalogue of actual certificate types and business-approved template mappings.

## 2. Proposed business rules

| ID | Rule | Rationale |
|---|---|---|
| BR-01 | Every certificate request must reference a valid certificate type | Enables deterministic routing |
| BR-02 | Automated generation is permitted only when exactly one active, approved template is mapped to the requested type | Prevents generation from an unsupported or ambiguous template |
| BR-03 | If no eligible template is mapped to the requested type, the request must be routed to manual processing | Ensures unsupported requests have an explicit path |
| BR-04 | If more than one eligible template matches a request, the system must not select one arbitrarily; it must raise an exception for resolution | Avoids unpredictable output |
| BR-05 | Each template must declare the required data fields used to populate the document | Makes field requirements testable |
| BR-06 | A certificate must not be marked as generated unless document generation succeeds | Prevents false completion states |
| BR-07 | The processing route, final status, and template version used (if any) must be traceable | Supports troubleshooting and auditability |
| BR-08 | A manual-processing request must retain a reason for manual routing | Enables reporting and prioritization of future automation |

These are proposed business rules for the portfolio design; they are not claimed to be historical rules from Be Smart.

## 3. Proposed request statuses

| Status | Meaning |
|---|---|
| `SUBMITTED` | The request has been received |
| `QUEUED_FOR_GENERATION` | The request is eligible for the automated route and awaits processing |
| `MANUAL_REVIEW_REQUIRED` | The request cannot proceed through the automated route and needs human handling |
| `GENERATING` | Document generation is in progress |
| `ISSUED` | The certificate has been generated and made available |
| `REJECTED` | The request was rejected under a defined business rule |
| `FAILED` | A technical failure prevented processing |

This is a proposed status model. Whether all statuses are required depends on implementation and operational needs.

## 4. Template lifecycle proposal

A basic controlled lifecycle could use `DRAFT`, `APPROVED`, `ACTIVE`, and `RETIRED` states. Only an active, approved template should be eligible for automated generation. Template changes should be versioned so that a request can be traced to the template version used.

This lifecycle is a design proposal, not a description of the original system.
