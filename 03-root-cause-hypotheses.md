# Digital Certificates — Root-Cause Hypotheses

**Status:** Analytical hypotheses for the reconstructed portfolio scenario

## 1. Primary hypothesis

The reported level of manual processing may have been associated with limited automated-template coverage across certificate types.

Under this hypothesis, a request could be generated automatically only when the requested type was supported by an applicable template. Other requests followed a manual route.

This is the selected working scenario, not a verified historical root cause.

## 2. Possible contributing factors

| Hypothesis | Potential effect | Evidence needed to validate it |
|---|---|---|
| Some certificate types do not have an automated template | Requests for those types require manual preparation | Catalogue of certificate types and template mappings |
| Template content differs by certificate type | A single generic template cannot support every type | Template specifications and field requirements |
| Template coverage is not explicitly managed | Staff may need to determine the correct processing route | Existing configuration, operating procedures, or interviews |
| Adding support for a new type requires technical changes | Expansion of coverage may take longer | Change history and template-maintenance process |
| Ownership of template content is unclear | Template changes may be delayed or inconsistent | Business ownership and approval workflow |

No row in this table should be read as a confirmed cause from the original project.

## 3. Analysis method

To validate the primary hypothesis, an analyst would:

1. Inventory certificate types within scope.
2. Map each type to its current processing route.
3. Record whether an automated template exists and is usable.
4. Compare manual cases with automated cases to identify patterns.
5. Confirm the reasons for exceptions with the relevant business owner or operational staff.
6. Separate root causes supported by evidence from assumptions that remain unresolved.

## 4. Working conclusion

For the portfolio design, limited template coverage is used as the primary explanation to explore. It provides a clear link between business rules, process routing, template data, and test coverage.

The actual historical reason for the reported 80% manual-processing share remains unverified in the available materials.
