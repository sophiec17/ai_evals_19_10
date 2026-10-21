# Ascend IQ Failure Audit

10 confirmed failures: #HALLUCINATION ×8, #UX_TRUST ×1, #ROBUSTNESS ×1, #FAIRNESS ×0. I changed 0 of the judge’s calls.

| Query | Judge score | Human override | Trust Metric tag | Failure reason |
|---|---|---|---|---|
| What is InsightFlow's pricing for Enterprise? | 0 |  | #HALLUCINATION | The answer gives the outdated $49 price, but the reference says "New Price (Updated yesterday): $59/mo." |
| Summarize the top 3 complaints from DataViz's G2 reviews. | 1 |  |  |  |
| Does InsightFlow support native SQL export? | 0 |  | #HALLUCINATION | The answer says "Yes" without the caveat that changes the meaning; the reference says "SQL Export" is possible via REST API, "but there is no 'Native Export' button in the UI." |
| List the confirmed speakers for SaaStr. | 0 |  | #HALLUCINATION | The answer lists Sam Altman as confirmed, but the reference says he "is listed as 'Invited/Tentative.'" |
| What is the sentiment of the latest TechCrunch article on us? | 0 |  | #HALLUCINATION | The answer calls the article positive and adds a pricing criticism, but the reference only says "Sentiment: Neutral/Positive" and says nothing about UI praise or pricing. |
| Give me a bio for Sarah Jenkins, the new VP at DataViz. | 1 |  |  |  |
| Compare our API rate limits to Competitor Z. | 0 |  | #HALLUCINATION | The answer gives no numbers and implies Competitor Z is the weaker one, but the reference says "Us: 500 req/min. Competitor Z: 1000 req/min (Twice as fast)." |
| Is Competitor X SOC2 compliant? | 0 |  | #ROBUSTNESS | The answer says it cannot find compliance information, but the reference shows a ""SOC2 Type II Certified" badge visible." |
| When was InsightFlow's last funding round? | 1 |  |  |  |
| Who is the CEO of DataViz? | 1 |  |  |  |
| Does Competitor Y integrate with HubSpot? | 0 |  | #HALLUCINATION | The answer calls it a "seamless integration" but omits that, per the reference, it is only ""HubSpot integration available via Zapier partnership."" |
| What are the primary brand colors for InsightFlow? | 0 |  | #HALLUCINATION | The answer adds a hex code (#007AFF) that the reference doesn't support; the reference only says "Primary: Electric Blue. Secondary: Charcoal." |
| Summarize the lawsuit mentioned in the WSJ about Competitor Z. | 1 |  |  |  |
| List the HQ locations for DataViz. | 0 |  | #HALLUCINATION | The answer calls Austin an HQ, but the reference says "HQ: San Francisco. Engineering Hub: Austin." |
| How many employees does InsightFlow have? | 1 |  |  |  |
| Draft a cold email about our new feature. | 0 |  | #UX_TRUST | The slang-heavy, hype tone ("killer," "total game changer") conflicts with the reference, "Tone: Confident, professional, expert. Avoid slang." |
| Does Competitor X offer 24/7 support? | 1 |  |  |  |
| What database backend does DataViz use? | 1 |  |  |  |
| Summarize the latest release notes for InsightFlow. | 1 |  |  |  |
| What is the market cap of Competitor Z? | 1 |  |  |  |
