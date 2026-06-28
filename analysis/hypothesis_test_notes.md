# Hypothesis Test Notes
## Experiment: Onboarding & Activation Campaign A/B Test

---

## 1. Metric Tested

**Primary North Star Metric:** `Paid Conversion Rate` (`converted_to_paid`)

This is the proportion of users in each group who converted from trial/free to a paid subscription within the 30-day observation window.

---

## 2. Hypotheses

**Null Hypothesis (H₀):**
> The paid conversion rate in the Treatment group is equal to the paid conversion rate in the Control group.
> H₀: p_treatment = p_control

**Alternate Hypothesis (H₁):**
> The paid conversion rate in the Treatment group is greater than the paid conversion rate in the Control group.
> H₁: p_treatment > p_control

---

## 3. Test Design

| Parameter | Value |
|---|---|
| Test Type | Two-Proportion Z-Test (one-tailed) |
| Direction | One-tailed (right/upper tail — we expect Treatment > Control) |
| Significance Level (α) | 0.05 (95% confidence level) |
| Decision Rule | Reject H₀ if p-value < 0.05 |

**Rationale for one-tailed test:** The treatment (new onboarding campaign) was specifically designed to improve conversion rates. We are only interested in detecting a positive improvement, not a decrease.

**Rationale for Z-test:** Sample sizes are sufficiently large (n_control = 693, n_treatment = 715) and binary outcome variable satisfies normal approximation conditions (np ≥ 5 for all groups).

---

## 4. Sample Data

| Group | Users (n) | Conversions | Conversion Rate |
|---|---|---|---|
| Control | 693 | 22 | 3.1746% |
| Treatment | 715 | 50 | 6.9930% |

---

## 5. Test Results

| Statistic | Value |
|---|---|
| Pooled proportion (p_pool) | 5.1136% |
| Standard Error (pooled) | 0.011744 |
| Z-statistic | 3.2519 |
| P-value (two-tailed) | 0.001146 |
| **P-value (one-tailed)** | **0.000573** |
| Chi-square statistic (cross-check) | 9.8024 |
| Chi-square p-value | 0.001743 |
| 95% Confidence Interval (abs. lift) | [+1.54%, +6.10%] |
| Absolute Lift | +3.82 percentage points |
| Relative Lift | +120.28% |

---

## 6. Decision

**P-value (0.000573) < α (0.05) → REJECT the Null Hypothesis**

We have sufficient statistical evidence at the 95% confidence level to conclude that the Treatment group achieved a significantly higher paid conversion rate than the Control group.

---

## 7. Business Interpretation

The new onboarding and activation campaign more than doubled the paid conversion rate — from 3.17% in Control to 6.99% in Treatment, a statistically significant increase of +3.82 percentage points (120% relative lift). This result is highly unlikely to be due to chance (p = 0.0006).

The 95% confidence interval [+1.54%, +6.10%] tells us that, if we were to run this experiment again, we would expect the true improvement in conversion rate to fall within this range.

**However**, before launching, the elevated support ticket rate (+69.6%) in the Treatment group warrants investigation. If the campaign is creating confusion or unmet expectations, post-conversion quality may deteriorate. This guardrail metric must be resolved before a full rollout.

---

## 8. Limitations

- **Short observation window:** 30-day revenue may not capture long-term LTV impacts.
- **Novelty effect:** The treatment's effect might diminish over time as users become accustomed to the new onboarding flow.
- **Segment heterogeneity:** Conversion lift varies by region and device — a single metric may obscure subgroup differences.
- **Support ticket cause unknown:** The 69.6% spike in support tickets could be driven by higher engaged users asking more questions (positive) or by confusion in the onboarding flow (negative).
