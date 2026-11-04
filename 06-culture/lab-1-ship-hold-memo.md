# Ship-or-Hold Memo · Ascend IQ

> **Decision:** HOLD

## The Answer

Ascend IQ have two critical P0 failures, firstly robustness gap as it's not correctly displaying the retrieved information. Secondly, it's hallucinating facts resulting incorrect data being presented to business users

## The Arguments

### 1. Hallucinated facts reach business users and ruin customer trust

Evidence: Ascend IQ evals have flagged 8/20 failed test cases, where the platform provides inaccurate and untrustworthy content. One example shows  Ascend IQ providing outdated pricing i.e. showing a $49 price, but the reference says "New Price (Updated yesterday): $59/mo."

### 2. Retrieved information is displayed incorrectly

Evidence: Ascend IQ evals have flagged 1/20 failed test cases. The platform retrieves the right information but doesn’t show it correctly, so users see content that doesn’t match the source.The test case failed to provide a correct answer even when a reference shows a ""SOC2 Type II Certified" badge visible."

## Next Step · Decision Needed

Recommend we hold the Ascend IQ launch; please approve the hold. Both these failures reflect 9/20 of Ascend IQ test cases therefore the recommendation is not to ship due concerns on reliability and accuracy.

