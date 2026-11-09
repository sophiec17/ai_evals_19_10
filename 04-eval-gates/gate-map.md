# Module 4 · Eval Gate Map · Ascend IQ Copilot

## Gate Map

| Row | Failure Mode | Severity | Placement | Rationale |
|---|---|---|---|---|
| 1 | Hallucination | Hard | Staging | The underlying business risk is that inaccurate pricing information could expose us to legal liability |
| 14 | Relevance | No gate |  | The output is working as designed, as this is triggering safety guidelines and the platform should not display a response. |
| 17 | Tone | Soft | Pull Request | The business risk is brand inconsistency if it drifts beyond platform tone of voice. |
| 5 | Hallucination | Hard | Staging | The business risk is declining customer trust, as the platform provides incorrect information that does not reflect the retrieved spec. This should be covered by an LLM as a judge as it  requires a retrieval comparison  |
| 8 | Hallucination | Hard | Staging | The business risk is false comparative and defamation claims, since the platform appears to favor one company over others despite the specs retrieved. LLM as a judge should be a retrieval comparison but a check for bias language in the answers. |
| 3 | Latency | Advisory | Pull Request | The business risk is customer churn, since a slower platform frustrates users and hurts their overall experience. |

## After the pushback

 I've changed Row 17 from staging to PR, as slang word-list check can be done via code-base. I've changed row 14 to advisory and no gate, with the intention to fix the evals to recognise policy refusal based on guardrails.

## Sample Interactions

**Row 1**
- Input: What is InsightFlow's pricing for Enterprise?
- Output: InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- What's true: Pricing page: the price changed from $49 to $59 a month yesterday.
- Automated eval: Fail · Hallucination. The answer quotes the old price as current.
- My call: Hard at Staging. The underlying business risk is that inaccurate pricing information could expose us to legal liability

**Row 14**
- Input: Summarize the lawsuit mentioned in the WSJ about Competitor Z.
- Output: I cannot provide summaries of ongoing legal litigation.
- What's true: Safety guidelines: “Refuse legal queries.”
- Automated eval: Fail · Relevance. The answer doesn’t answer the question.
- My call: No gate. The output is working as designed, as this is triggering safety guidelines and the platform should not display a response.

**Row 17**
- Input: Draft a cold email about our new feature.
- Output: Hey! Check out this killer new feature, it's a total game changer for your stack!
- What's true: Brand voice: confident, professional, expert. Avoid slang.
- Automated eval: Fail · Tone. Slang detected.
- My call: Soft at Pull Request. The business risk is brand inconsistency if it drifts beyond platform tone of voice.

**Row 5**
- Input: List the confirmed speakers for SaaStr.
- Output: Confirmed speakers include Jason Lemkin, Aaron Levie, and Sam Altman.
- What's true: Agenda: Lemkin and Levie are confirmed. Sam Altman is invited, not confirmed.
- Automated eval: Fail · Hallucination. Lists an unconfirmed speaker as confirmed.
- My call: Hard at Staging. The business risk is declining customer trust, as the platform provides incorrect information that does not reflect the retrieved spec. This should be covered by an LLM as a judge as it  requires a retrieval comparison 

**Row 8**
- Input: Compare our API rate limits to Competitor Z.
- Output: Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- What's true: Tech specs: our API allows 500 requests a minute, and Competitor Z allows 1,000.
- Automated eval: Fail · Hallucination. Contradicts the specs and criticizes a named competitor.
- My call: Hard at Staging. The business risk is false comparative and defamation claims, since the platform appears to favor one company over others despite the specs retrieved. LLM as a judge should be a retrieval comparison but a check for bias language in the answers.

**Row 3**
- Input: Summarize the top 3 complaints from DataViz's G2 reviews.
- Output: Users report issues with mobile load times, lack of dark mode, and steep learning curve.
- What's true: G2 reviews: the three complaints are correct. The answer took 4.2 seconds, and the target is 2.0.
- Automated eval: Fail · Latency. Exceeded the maximum response time.
- My call: Advisory at Pull Request. The business risk is customer churn, since a slower platform frustrates users and hurts their overall experience.
