# Digital Certificates — Outcomes & Measurement Considerations

## 1. Reported indicators

The available project summary reports these before-and-after figures for the certificate-issuance work:

| Indicator | Baseline | Reported result | Absolute change |
|---|---:|---:|---:|
| Automated generation | 20% | 85% | +65 percentage points |
| Manual processing | 80% | 15% | -65 percentage points |
| Certificate issuance time | 1 business day | 10 minutes | Time reduced; exact baseline duration in minutes is not specified |

The percentages and times are transcribed from the available project summary. The calculation of absolute percentage-point change is arithmetic based on those reported values.

## 2. Interpretation

The reported indicators suggest a substantial increase in automated generation, a decrease in manual processing, and a shorter issuance turnaround time.

However, the source summary does not provide the measurement period, sample size, calculation method, definitions of each metric, or a causal breakdown of which changes produced which results. This portfolio therefore does not claim that the proposed template-coverage design alone produced the reported outcomes.

## 3. Recommended measurement definitions

For a future implementation or a fully evidenced case, define each measure before comparing results.

| KPI | Suggested definition | Measurement considerations |
|---|---|---|
| Automation rate | Number of eligible certificate requests completed automatically divided by all completed in-scope requests | Define treatment of cancellations, retries, and manual completion after failed automation |
| Manual-processing rate | Number of in-scope requests that require staff handling divided by all completed in-scope requests | Define whether any staff touch counts as manual processing |
| Issuance turnaround time | Elapsed time between request submission and certificate availability | Decide calendar time vs. business time; report median and percentiles as well as average where possible |
| Template coverage | Number of in-scope certificate types with active approved templates divided by all in-scope certificate types | A type being covered does not itself guarantee every request can be automated |
| Generation failure rate | Number of automated generation attempts that fail divided by all automated generation attempts | Classify technical failures separately from business-rule exceptions |

## 4. Measurement plan

1. Agree the scope of certificate types and eligible requests.
2. Record a baseline over a defined period.
3. Instrument request route, status transitions, and generation outcome.
4. Measure the same indicators after rollout.
5. Segment outcomes by certificate type and route.
6. Review exceptions and failure reasons before attributing improvement to a specific change.
