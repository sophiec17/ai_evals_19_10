# Module 4 · Launch Strategy · Ascend IQ Copilot

## 4.0 Release Criteria

| Gate | Failure | Metric | Threshold | Dataset | Method | Runs at |
|---|---|---|---|---|---|---|
| Hard | Showing incorrect information  | The percentage of generated answers that are inconsistent with the retrieved specs, including answers that contradict the documentation, misrepresent it, or add unnecessary details. | 100% , no tolerance  | Ascend IQ golden set | LLM judge | Staging |
| Soft | Row 17 · Tone: slang detected | The percentage of generated answers that contain no slang. This is measured with a regex check against an approved list of slang words | 5% | Ascend IQ golden set | Code-based check | Pull Request |
| Advisory | Row 3 · Latency: exceeded the maximum response time | The share of test cases whose end-to-end response time exceeds the maximum allowed latency. | 5% | Ascend IQ golden set | Code-based check | Pull Request |

## CI Gate Request for Engineering

- **Hard gate · Showing incorrect information .** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: The percentage of generated answers that are inconsistent with the retrieved specs, including answers that contradict the documentation, misrepresent it, or add unnecessary details.. Passes when: 100% , no tolerance . On a fail: block the merge.
- **Soft gate · Row 17 · Tone: slang detected.** Check: the code-based check, run on the Ascend IQ golden set at Pull Request. Measures: The percentage of generated answers that contain no slang. This is measured with a regex check against an approved list of slang words. Passes when: 5%. On a fail: pause the release until the PM signs off on an override.
- **Advisory gate · Row 3 · Latency: exceeded the maximum response time.** Check: the code-based check, run on the Ascend IQ golden set at Pull Request. Measures: The share of test cases whose end-to-end response time exceeds the maximum allowed latency.. Passes when: 5%. On a fail: post a warning, and don't block.

## Mitigation Plan · Soft Gate

If the soft gate fails, tone of voice may drift and slang may appear in more than 5% of generated responses. I recommend a staged rollout, which limits the access to the tool to a small group of users. This allows us to observe how customers phrase their queries on the platform and may help identify slang terms that are missing from the blocklist. This will also help evaluate the robustness of the tone-of-voice prompts with real customer queries.

