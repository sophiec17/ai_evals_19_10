# Module 5 · Coverage Matrix · AI Voice Agent

## Coverage Row

| Product | Hallucination Rate | Fairness | Latency | UX Trust | Robustness |
|---|---|---|---|---|---|
| AI Voice Agent | ⚠️ Partial | ❌ Gap | ❌ Gap | ⚠️ Partial | ⚠️ Partial |

## What Runs Today

- An eval gate tests its answers to 300 billing questions before every release.
- A supervisor listens to 10 random calls a week for tone.
- A drift monitor alerts when callers start asking about things the agent wasn’t tested on.

## Accepted Gap

**Fairness.** We accept this gap because as part of the pre-release evals we will have our golden dataset covering a range of accents, dialects, speech impairments to ensure users should not receive bias responses and users for the same queries should receive consistent responses.  After release, we will run regional audits to verify that escalation rates and accuracy rates are consistent across regions. 

We’ll look again:  We'll revise this, if escalation rates are above 30%. 

## Critical Gap

We’ve flagged latency as the most critical failures, callers will notice within second, if the AI agent lags, pauses or breaks-up. Voice AI should instantly know when a customer  starts or stop speaking and response instantly.  Customers have higher expectation of latency via voice as suppose to chat messaging. A latency failure would frustrate customers and lead to more abandon calls and higher human agent escalation. To close this gap, we should have pre-release checks and continuous monitoring in production. Therefore should be a latency threshold as part of pre-release evals and run a production 
drift monitor to track latency alert within minutes when latency falls below expected threshold.

## After the Pressure Test

I changed the product coverage: UX trust should be downgraded to partial, the sample size is too small. Robustness should be downgraded to partial, as it flags for new topics, not failures on in-scope queries. My accepted gap, trigger should be changed from 50% to lower rates. Within my latency pre-release checks, I should also run load testing for expected peak volumes and concurrency. The latency metrics and threshold should be spilt by: turn latency, endpointing delay, barge-in, false endpoint rate, component latency, audio break-up. 



