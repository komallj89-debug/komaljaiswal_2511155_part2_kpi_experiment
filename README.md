Part 2: KPI Framework & Experiment Analysis
Onboarding & Activation Campaign A/B Test

Business Problem Statement
Decision: Should we launch the new onboarding campaign to 100% of users?
The onboarding experience is the primary lever between acquisition and paid conversion. Core metrics tracked: Paid Conversion Rate (North Star), ARPU, Onboarding Completion, Engagement Score, plus guardrails (Refund Rate, Support Tickets, Days to Convert).

Dataset — 1,408 users (693 Control | 715 Treatment)
16 columns covering user identity, experiment group, funnel behavior (landing page → trial → onboarding → paid), revenue, support tickets, refunds, engagement score, and days to convert. Minor missing data in device_type (18), traffic_source (24), and engagement_score (14) — all handled in cleaning.

North Star: Paid Conversion Rate
Chosen because it directly measures the core business outcome (free → paid), is influenced by every upstream funnel step, and improvements compound into ARR and LTV.

KPI Tree
Paid Conversion Rate sits at the top, fed by three pillars — Acquisition (Landing Page Visit Rate, Trial Start Rate), Activation (Onboarding Completion, Engagement Score), and Retention (ARPU, Days to Convert) — with three guardrail metrics monitored separately.

Final Recommendation: LAUNCH (Phased Rollout)
+120% relative lift in paid conversion rate (3.17% → 6.99%, p = 0.0006). All funnel metrics improved. Roll out to 50% first while investigating the support ticket spike (+69.6%), then expand to 100% in Week 3 if guardrails hold.
