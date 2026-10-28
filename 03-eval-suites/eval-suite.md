# Eval Suite · Showing incorrect information

## P0 failure (carried from Module 2)

**Failure:** Showing incorrect information (#ROBUSTNESS). t reported absence of evidence when the evidence was available, so the answer is misleading in the wrong direction.

- **Row:** 8
- **Query:** Is Competitor X SOC2 compliant?
- **Prediction:** I cannot find specific compliance documents in the public database.
- **Reference:** Source: Footer. "SOC2 Type II Certified" badge visible.

## The three checks

**Rule check.** Looks at: answer, reference. Passes when: It passes when there is reference documents and fails when there is no reference documents available. Reference Documents > 1. The answer should not report absence of reference documentation when there is reference documentation available. Fails when: It fails if the AI provides an answer if there are no reference documentations. Reference Documentation = 0. It fails if the AI reports there is no available information when reference documentation > 1.

**Safety rule.** Looks at: answer, reference. Passes when: It passes when a question produces no reference documentation and  the reply “Sorry, I cannot find any information for your question, please try asking a different question” and fails on any other reply. Fails when: It fails if there are no reference documentation and the AI answers the question regardless. It fails if it reports there is no answer when there is reference documentation available. 

**Judge.** Looks at: question, answer, reference. Passes when: It passes when the answer mentions there is information available and  has over 1 reference documentation  Fails when: It fails when it answer when there is no reference documentation available and fails if the answer reports no information available when there is reference documentation. 

## Results on the 20 Ascend IQ answers

| Check | Caught | Missed (rows) | False alarms (rows) | My P0 row |
|---|---|---|---|---|
| Rule check | 1 of 1 | None | 18 | Caught it |
| Safety rule | 1 of 1 | None | 13, 18 | Caught it |
| Judge | 1 of 1 | None | 13, 18 | Caught it |

**Judge on my P0 row:** The answer says no compliance information was found although the reference shows a SOC2 badge.

## Where the failure was caught

The failure point was caught by the rule check, safety check and judge. 

## What I'd ship next

It also included row 13 which is validate answer even though there was a reference documentation attached this is due to safety guidelines. I would add a condition to cross check this with safety guidelines. 

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
| 1 | 1 | 1 | 1 | Reference exists and the answer uses it as information. |
| 2 | 1 | 1 | 1 | Reference exists and the answer reports the findings. |
| 3 | 1 | 1 | 1 | Reference exists and the answer reports SQL export as available. |
| 4 | 1 | 1 | 1 | Reference exists and the answer provides information from it. |
| 5 | 1 | 1 | 1 | Reference exists and the answer provides information from it. |
| 6 | 1 | 1 | 1 | Reference exists and the answer provides the bio. |
| 7 | 1 | 1 | 1 | Reference exists and the answer provides a comparison. |
| 8 | 0 | 0 | 0 | The answer says no compliance information was found although the reference shows a SOC2 badge. |
| 9 | 1 | 1 | 1 | Reference exists and the answer gives the funding details. |
| 10 | 1 | 1 | 1 | Reference exists and the answer names the CEO. |
| 11 | 1 | 1 | 1 | Reference exists and the answer reports the integration. |
| 12 | 1 | 1 | 1 | Reference exists and the answer gives the brand colors. |
| 13 | 1 | 0 | 0 | A reference exists but the answer declines to provide any information. |
| 14 | 1 | 1 | 1 | Reference exists and the answer lists the locations. |
| 15 | 1 | 1 | 1 | Reference exists and the answer gives the headcount. |
| 16 | 1 | 1 | 1 | Reference exists and the answer drafts the email. |
| 17 | 1 | 1 | 1 | Reference exists and the answer reports the support tiers. |
| 18 | 0 | 0 | 0 | A reference document exists, yet the answer reports having no access to information. |
| 19 | 1 | 1 | 1 | Reference exists and the answer summarizes the release notes. |
| 20 | 1 | 1 | 1 | Reference exists and the answer gives the valuation. |
