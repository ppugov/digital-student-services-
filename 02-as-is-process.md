# Digital Certificates — AS-IS Process

## 1. Current-state process

The certificate issuance process follows two routes depending on whether the requested certificate type is supported by an automated template.

- **Automated route:** The platform identifies a matching template and generates the certificate automatically.
- **Manual route:** When an applicable automated template is unavailable, university staff prepare and process the certificate manually.

The process aims to ensure that students receive the required certificates while accounting for differences in template availability and processing requirements.

## 2. AS-IS BPMN Diagram

<!-- Insert the exported BPMN diagram below. Save the image in the repository root as as-is-process.svg. -->

![AS-IS Manual Certificate Issuance](<./AS IS — Manual Certificate Issuance.svg>)

## 3. Process steps

| Step | Actor / system | Activity | Expected output |
|---|---|---|---|
| 1 | Student | Selects the required certificate type | Request details |
| 2 | Platform | Identifies the requested certificate type and checks template availability | Processing route determined |
| 3A | Platform | Generates the certificate using the matching automated template | Generated certificate file |
| 3B | University staff | Prepares and processes the certificate manually when no applicable template is available | Prepared certificate file |
| 4 | Platform / university staff | Makes the completed certificate available to the student | Issued certificate |

## 4. Key process pain points

- Certificate types without automated-template coverage require manual processing.
- Manual preparation increases the workload of university staff.
- Template availability determines the processing route for a certificate request.
- Different processing routes can result in different certificate issuance times.
- Limited automation creates opportunities to standardize document generation and reduce repetitive administrative work.

## 5. Business impact

The process combines automated certificate generation with manual handling for requests that cannot be processed automatically. Expanding automated-template coverage can reduce manual intervention, improve process consistency, shorten issuance times, and free university staff to focus on requests requiring individual attention.

The AS-IS analysis provides the basis for identifying automation opportunities, defining business rules, and designing the TO-BE certificate issuance process.
