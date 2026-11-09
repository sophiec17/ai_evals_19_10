# Module 5 · Eval Budget · Ascend IQ

**Quarterly budget cap:** $200,000
**Online eval spend:** $155,000 (2 of at most 3 online evals)

## Budget

| Failure | Trust metric | Risk | Level | Cost |
| --- | --- | :---: | :---: | ---: |
| Data Fabrication | Hallucination Rate | P0 | Online eval | $85,000 |
| Context Specificity | Robustness | P1 | Online eval | $70,000 |
| Overconfident Tone | UX Trust | P1 | Periodic audit | $6,500 |
| Data Bias | Fairness | P2 | Code-based check | $2,750 |
| Slow Answers | Latency | P3 | Code-based check | $1,250 |

## Downgrades

### Periodic audit · Overconfident Tone (UX Trust · P1)
- **Cheaper check:** Weekly audit, using LLM as a judge to check for overconfident tone with human in the loop 
- **Why it’s enough:** This risk is P1 however overconfidence tone and stating guesses as facts are a symptoms of larger failures in the system in robustness and hallucination.

### Code-based check · Data Bias (Fairness · P2)
- **Cheaper check:** weekly audit, run code to check using representation check, based on the APAC share of sources cited or used in the summary, divided by APAC share of sources retrieved.
- **Why it’s enough:** This risk is a P2 because  there's no reputational damage but there's potential risk of customer churn. The weekly audit ensures we close the gap on source coverage between APAC and US data. This check cannot tell whether an APAC source was omitted because it wasn't relevant or because of the bias

### Code-based check · Slow Answers (Latency · P3)
- **Cheaper check:** every response, this should be based in the code with latency and timeout measurements
- **Why it’s enough:** It might miss how often users are waiting, and instance where it's slow but just just the threshold,




