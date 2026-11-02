# Module 5 · Coverage Matrix · AI Voice Agent

## Coverage Row

| Product | Hallucination Rate | Fairness | Latency | UX Trust | Robustness |
|---|---|---|---|---|---|
| AI Voice Agent | ⚠️ Partial | ⚠️ Partial | ⚠️ Partial | ✅ Covered | ✅ Covered |

## What Runs Today

- An eval gate tests its answers to 300 billing questions before every release.
- A supervisor listens to 10 random calls a week for tone.
- A drift monitor alerts when callers start asking about things the agent wasn’t tested on.

## Accepted Gap

**Latency.** We accept this gap because there should be in-built timeout on response processing and generating. Once request hit threshold, there should be in-built fallback journeys.

We’ll look again:  We'll revise this, if escalation rates are above 30%. 

## Critical Gap

We’ve flagged Fairness as the most critical gap for AI Voice Agent because users should not receive bias responses and users for the same queries should receive consistent responses. Fairness failures (accents, dialects, speech impairments) carry reputational and regulatory exposure. The customers would notice first during a conversation.  I would make the following checks: 
Within the golden dataset, I would include recorded audio  variants across accent, dialect and speech-impairment audio and ensure experience and responses are consistent. There should be a maximum gap of max gap of 10% accuracy rate versus the best group.  This should be re-run per release gate. The data used should be sources from real customer recording from contact centre. The sample size should be 100 samples per different accent/impairment.
I would conduct audit of call recordings, across interactions with difference in accents, dialect, regions etc, what the escalation rates and accuracy rates are. This audit should be conducted monthly.



## After the Pressure Test

I changed the product coverage: UX trust should be downgraded to partial, the sample size is too small. Robustness should be downgraded to partial, as it flags for new topics, not failures on in-scope queries. My accepted gap, trigger should be changed from 50% to lower rate as the monitoring required for this is cheap. 

I also changed my fairness plan, I should define what counts as a pass and failures during evals and define the sampling size per group.

