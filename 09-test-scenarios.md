# Digital Certificates — Test Scenarios

**Status:** Proposed test coverage for the reconstructed portfolio design

## 1. Functional scenarios

| ID | Scenario | Preconditions / input | Expected result | Type |
|---|---|---|---|---|
| TC-01 | Submit request for a supported type | Type is enabled and exactly one active, approved template is mapped | Request is created and routed to automated generation | Positive |
| TC-02 | Submit request for a type without a template | Type is enabled but no active, approved template exists | Request is created and routed to manual processing with a reason | Positive / routing |
| TC-03 | Submit request for a disabled type | Type is disabled | Request is rejected with a validation response | Negative |
| TC-04 | Submit request with missing type identifier | `certificateTypeId` is absent | Request is rejected with a validation response | Negative |
| TC-05 | Ambiguous template mapping | Two eligible templates are mapped to the same type | Automatic generation does not start; an exception is recorded | Negative / edge case |
| TC-06 | Successful document generation | Request is routed to automated generation and required data is available | Document is created, associated with the request, and status becomes `ISSUED` | Positive |
| TC-07 | Document-generation failure | Generator returns a controlled failure | Request is not marked `ISSUED`; failure is recorded | Negative |
| TC-08 | Check request status | Caller is authorized and request exists | Current status and route are returned | Positive |
| TC-09 | Access another student's request | Caller is not authorized for the requested record | Access is denied without exposing protected data | Security |
| TC-10 | Manual route completion | Request is awaiting manual processing and staff completes the workflow | Outcome is recorded and the certificate becomes available under the agreed process | Positive |
| TC-11 | Retired template | Only a retired template is mapped to the type | The retired template is not used; request follows the agreed exception/manual route | Edge case |
| TC-12 | Trace template version | Automated generation succeeds | The document/request can be traced to the template version used | Traceability |

## 2. Acceptance links

- TC-01 and TC-02 validate the routing rules in FR-03 through FR-05.
- TC-05 validates FR-06 and BR-04.
- TC-06 and TC-07 validate FR-08 and BR-06.
- TC-09 validates the proposed access-control requirement.
- TC-12 validates traceability of template version and processing outcome.

## 3. Test data considerations

Use synthetic student identifiers, non-production certificate types, and dummy document content. Do not include real student data or confidential company materials in a public repository.

The examples should be adapted once the actual business catalogue, status model, and implementation behavior are known.
