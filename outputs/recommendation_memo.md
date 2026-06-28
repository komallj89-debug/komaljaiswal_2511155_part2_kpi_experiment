# Recommendation Memo
## Subject: A/B Experiment Results — Onboarding & Activation Campaign
**To:** Product Leadership & Growth Team
**From:** Analytics Team
**Date:** June 28, 2026
**Classification:** Internal — Decision Document

---

## 1. Executive Summary

We ran a controlled A/B experiment testing a redesigned onboarding and activation campaign against the current baseline experience. The experiment ran across 1,408 users (693 Control, 715 Treatment) over a 30-day observation window.

**The result is clear: the new campaign more than doubled our paid conversion rate.** The Treatment group achieved a 6.99% paid conversion rate versus 3.17% for Control — a +120% relative lift that is statistically significant at the 95% confidence level (p = 0.0006).

**Recommendation: LAUNCH with a phased rollout**, subject to root-cause investigation of the elevated support ticket rate in the Treatment group.

---

## 2. North Star Metric

**Metric:** Paid Conversion Rate (`converted_to_paid`)

This measures the percentage of users who progress from free/trial status to a paid subscription within 30 days of signup. It is the most direct indicator of whether our onboarding experience drives revenue-generating behavior and reflects the core business objective: converting acquired users into paying customers.

All other metrics in this analysis are either upstream drivers of conversion or downstream guardrails protecting the quality of those conversions.

---

## 3. KPI Tree Structure

Our KPI Tree organizes metrics across three pillars:

**Acquisition (Top of Funnel)**
- Landing Page Visit Rate: % of signed-up users who visit the landing page
- Trial Start Rate: % of users who begin a product trial

**Activation (Mid Funnel)**
- Onboarding Completion Rate: % of users who complete the onboarding flow
- Avg Engagement Score: Composite behavioral engagement metric

**Retention (Post-Conversion)**
- ARPU (30-day): Average revenue per user in the first 30 days
- Days to Convert: Average days between signup and paid conversion

**Guardrail Metrics** (monitored separately to detect harm):
1. Refund Rate
2. Support Ticket Rate
3. Days to Convert (also a guardrail — faster is good, but extremely fast may indicate impulsive purchases that lead to churn)

---

## 4. Experiment Results Summary

| Metric | Control | Treatment | Absolute Lift | Relative Lift |
|---|---|---|---|---|
| Users | 693 | 715 | +22 | +3.2% |
| Landing Page Visit Rate | 63.6% | 72.6% | +9.0pp | +14.1% |
| Trial Start Rate | 25.1% | 29.1% | +4.0pp | +15.9% |
| Onboarding Completion Rate | 15.6% | 21.3% | +5.7pp | +36.4% |
| **Paid Conversion Rate** | **3.17%** | **6.99%** | **+3.82pp** | **+120.3%** |
| ARPU (30-day) | $51.75 | $53.88 | +$2.13 | +4.1% |
| Avg Revenue / Converted User | $1,630 | $770 | -$860 | -52.7% |
| Refund Rate | 0.00% | 0.42% | +0.42pp | — |
| Support Ticket Rate | 0.22/user | 0.37/user | +0.15 | +69.6% |
| Avg Engagement Score | 57.0 | 62.9 | +5.9 | +10.4% |
| Avg Days to Convert | 8.9 days | 6.4 days | -2.5 days | -27.8% |

The funnel improvement is comprehensive: every top-of-funnel and mid-funnel metric improved under Treatment, creating a consistent story of a better onboarding experience.

---

## 5. Hypothesis Test Interpretation

A two-proportion Z-test was performed on paid conversion rate:

- **H₀:** p_treatment = p_control (no difference)
- **H₁:** p_treatment > p_control (treatment is better)
- **Test:** One-tailed Z-test at α = 0.05
- **Z-statistic:** 3.2519
- **P-value (one-tailed):** 0.000573
- **Result:** REJECT H₀
- **95% Confidence Interval for lift:** [+1.54%, +6.10%]

The result is highly statistically significant. The probability that this result occurred by chance is less than 0.1%. We can confidently attribute the improvement in conversion rate to the new campaign.

---

## 6. Guardrail Analysis

### Refund Rate
- Control: 0.00% | Treatment: 0.42%
- **Status: WATCH.** No refunds occurred in Control; 3 users in Treatment requested refunds. The absolute count is small (3/50 converted users), but the signal is new. This could indicate some users feel pressured into converting before they are ready (accelerated by the faster onboarding). Monitor at scale.

### Support Ticket Rate
- Control: 0.22 tickets/user | Treatment: 0.37 tickets/user (+69.6%)
- **Status: INVESTIGATE BEFORE FULL LAUNCH.** This is the most significant guardrail concern. A 70% increase in support contacts could mean:
  - *Positive signal:* More engaged users are actively exploring the product and have questions
  - *Negative signal:* The onboarding flow has gaps or creates confusion/unmet expectations
  - Root-cause analysis (ticket topic categorization) is required before full rollout.

### Days to Convert
- Control: 8.9 days | Treatment: 6.4 days (-27.8%)
- **Status: POSITIVE.** Faster time-to-conversion is a favorable signal. Users are finding value faster. This accelerates revenue recognition and reduces trial drop-off risk.

---

## 7. Segment-Level Insights

**By Region:**
- All four regions (North, South, East, West) showed positive conversion lift under Treatment.
- The lift appears consistent across regions, suggesting the campaign is broadly effective and not driven by a single geographic pocket.

**By Device Type:**
- Mobile users (the largest segment at ~61% of users) showed meaningful improvement.
- Desktop users also lifted, though the smaller sample sizes for Tablet users make that segment's results less reliable.

**By Traffic Source:**
- Organic and Paid Search users showed the strongest absolute conversion numbers.
- The campaign's impact appears consistent across acquisition channels, indicating it's the onboarding experience — not just a particular user type — that's driving the lift.

---

## 8. Final Recommendation

**LAUNCH — Phased Rollout**

Launch the new onboarding campaign to 100% of users, but implement in two stages:

**Phase 1 (Weeks 1–2):** Roll out to 50% of traffic while simultaneously:
- Auditing support tickets from the Treatment group in this experiment to categorize ticket reasons
- Implementing a support ticket monitoring dashboard with a kill-switch threshold (e.g., if support ticket rate exceeds 0.50 tickets/user, pause and investigate)
- Tracking refund rates weekly with a soft ceiling of 1.5%

**Phase 2 (Week 3+):** If guardrail metrics remain within acceptable bounds, expand to 100% of users.

The conversion rate improvement is too significant to delay. At current scale, the Treatment conversion rate (6.99%) vs. Control (3.17%) implies roughly 2.2x more paying customers from the same acquisition spend — a transformative business impact.

---

## 9. Risks and Limitations

1. **Support ticket root cause unknown:** The single largest risk. If tickets reflect confusion, the refund and churn rates may worsen over 60–90 days.
2. **Revenue per converted user declined:** Treatment converts more users but at lower individual revenue ($770 vs $1,630). This may reflect a broader funnel catch (lower-intent users converting), which could affect LTV.
3. **30-day window is short:** Long-term churn, LTV, and satisfaction impacts are not yet captured.
4. **Novelty effect:** Conversion rates may normalize downward as the new onboarding becomes the standard experience.
5. **Sample size for some segments is small:** Tablet and Referral traffic sub-segments have limited statistical power for segment-specific conclusions.

---

## 10. Next Steps

| Priority | Action | Owner | Timeline |
|---|---|---|---|
| P0 | Audit support tickets from Treatment users; categorize by reason | Support + Analytics | Week 1 |
| P0 | Set up real-time guardrail dashboards for refunds + tickets | Engineering | Week 1 |
| P1 | Begin Phase 1 rollout (50% traffic) | Product | Week 1 |
| P1 | Monitor 30-day refund and churn rates for new cohort | Analytics | Ongoing |
| P2 | Analyze 60-day LTV for converted users in both groups | Analytics | Week 6 |
| P2 | Run follow-up experiment to address support ticket root cause | Product | Week 4 |
| P3 | Evaluate segment-specific optimizations (device, region) | Product | Week 8 |

