---

# 🧪 Paywall Pricing A/B Experiment Design
### RevenueCat Experiments — Full Pre-Registration Brief

---

## 1. 🎯 Experiment Objective

Determine whether **price anchoring and value framing** on the paywall — specifically a "Best Value" badge + monthly cost equivalent breakdown for the annual plan — increases trial-to-paid conversion rate and ARPU without degrading trial start rate.

---

## 2. 📐 Hypothesis

> **If** we add a "Best Value" badge and display the annual plan's monthly equivalent cost (e.g., *"$4.17/mo, billed $49.99/yr"*) on the paywall, **then** we expect a **≥10% relative lift** in trial-to-paid conversion rate, **because** price anchoring reduces cognitive load and makes the value differential between plans explicit — nudging users toward the higher-LTV annual plan.

**Causal mechanism:** Users who see "$12.99/mo" next to "$4.17/mo (annual)" perform an instant mental comparison. The anchoring effect makes annual feel like the obvious rational choice, increasing both conversion *and* plan mix toward annual.

---

## 3. 🔬 Experiment Structure

| Parameter | Detail |
|---|---|
| **Tool** | RevenueCat Experiments (Offerings A/B) |
| **Type** | A/B (2-variant, no multi-arm — one variable at a time) |
| **Traffic Split** | 50% Control / 50% Variant |
| **Randomization Unit** | `app_user_id` (user-level, sticky assignment) |
| **Scope** | New users only (first app open), all platforms |

### Control (A) — Current Paywall
- Monthly plan: $12.99/mo
- Annual plan: $49.99/yr
- No visual hierarchy cues

### Variant (B) — Framed Paywall
- Monthly plan: $12.99/mo
- Annual plan: **$49.99/yr** → displayed as *"$4.17/mo — Best Value 🏷️ (Save 68%)"*
- Annual plan visually highlighted (border, badge)

> ⚙️ **Implementation:** Create two Offerings in RevenueCat dashboard, assign each to an Experiment variant. Zero code changes required — paywall config handled remotely.

---

## 4. 📊 Metrics Framework

### Primary Success Metric
| Metric | Definition | Minimum Detectable Effect |
|---|---|---|
| **Trial-to-paid conversion rate** | `paid_subscribers / trial_starts` (30-day window) | **+10% relative** (e.g., 35% → 38.5%) |

### Secondary Metrics (Must Not Degrade)
| Metric | Direction | Rationale |
|---|---|---|
| Annual plan mix (% of paid choosing annual) | ↑ | Core LTV driver |
| ARPU at 30 days | ↑ | Captures plan mix shift value |
| Trial start rate | = or ↑ | Guardrail — paywall complexity shouldn't deter starts |

### Guardrail Metrics (Experiment Kills If These Move Negatively)
| Metric | Threshold |
|---|---|
| Trial start rate | < −5% relative = kill experiment |
| D7 cancellation rate | > +10% relative = kill experiment |
| App store rating / crash rate | Any degradation = kill experiment |

---

## 5. 🧮 Sample Size & Duration Calculation

Using a **two-proportion z-test** with the following inputs:

```
Baseline conversion rate (p1):     35%  [RevenueCat 2025 benchmark: monthly trial-to-paid]
Minimum detectable effect (MDE):   +10% relative → p2 = 38.5%
Statistical power (1−β):           80%
Significance level (α):            0.05 (two-tailed)
```

**Formula:**
```
n = 2 × [(z_α/2 + z_β)² × p̄(1−p̄)] / (p1−p2)²

Where: p̄ = (p1 + p2) / 2 = 0.3675
       z_α/2 = 1.96, z_β = 0.84

n ≈ 2 × [(1.96 + 0.84)² × 0.3675 × 0.6325] / (0.035)²
n ≈ 2 × [7.84 × 0.2325] / 0.001225
n ≈ 2 × 1.822 / 0.001225
n ≈ 2,977 trial starts per variant
```

### ✅ Minimum Required: **~3,000 trial starts per variant (6,000 total)**

| Volume Assumption | Required Duration |
|---|---|
| 500 trial starts/day | **~12 days** |
| 200 trial starts/day | **~30 days** |
| 100 trial starts/day | **~60 days** |

> ⚠️ **Hard rule:** Run for a **minimum of 14 days** regardless of volume to capture full weekly seasonality cycles. Do not peek and call early.

---

## 6. 📅 Experiment Timeline

```
Week 0    │ Pre-experiment: Baseline metric snapshot, QA both Offerings in sandbox
Week 1–2  │ Ramp: Monitor guardrail metrics daily (no peeking at primary metric)
Week 2+   │ Evaluation: Check significance only after minimum sample size hit
Week 3–4  │ Decision: Ship winner, iterate, or run follow-up test
```

**Pre-registration checklist (do this BEFORE launch):**
- [ ] Document baseline conversion rate from last 30 days
- [ ] Confirm both Offerings render correctly on iOS + Android (sandbox test)
- [ ] Set up RevenueCat Charts segment for experiment cohort
- [ ] Confirm webhook events flowing correctly for INITIAL_PURCHASE + TRIAL_START
- [ ] Designate a single decision-maker to prevent HiPPO override of results

---

## 7. 📈 Expected Business Impact (If Hypothesis Confirmed)

Assuming 500 trial starts/day and current 35% conversion:

| Scenario | Conversion Rate | Monthly New Paid Users | Impact vs. Baseline |
|---|---|---|---|
| **Baseline** | 35.0% | 5,250 | — |
| **+10% relative lift** | 38.5% | 5,775 | **+525 paid users/mo** |
| **+15% relative lift** | 40.3% | 6,045 | **+795 paid users/mo** |

If annual plan mix increases from ~30% → ~45% of conversions:
- **ARPU lift:** From ~$8.20 → ~$10.50/mo equivalent (+28%)
- **Combined revenue impact:** Meaningful — this is the experiment worth running first.

> 📌 *All forecasts are estimates based on RevenueCat 2025 benchmarks. Actual results depend on your app category, acquisition mix, and price points.*

---

## 8. 🚦 Decision Rules

| Outcome | Action |
|---|---|
| p < 0.05 AND primary metric ↑ AND guardrails clean | **Ship Variant B** |
| p < 0.05 AND primary metric ↑ BUT guardrail breached | **Do not ship** — investigate tradeoff |
| p ≥ 0.05 after full sample | **Null result** — try different variable (e.g., price point itself) |
| Guardrail breached early | **Kill experiment immediately** |

---

## 9. 🔁 Follow-On Experiment Roadmap

This experiment tests *framing* only. If it wins, the next logical tests in sequence:

1. **Price elasticity test** — Is $39.99/yr vs. $49.99/yr optimal?
2. **Trial length test** — 7-day vs. 14-day free trial on conversion rate
3. **Paywall template test** — Feature-focused vs. social proof vs. comparison table layout
4. **Personalized Offerings** — Different price points by acquisition channel (RevenueCat Targeting)

> One variable per test. Always. No exceptions.

---

**Bottom line:** This is a low-risk, high-upside experiment. Zero engineering required thanks to RevenueCat's remote Offerings config. If the 10% relative lift materializes, you're looking at hundreds of additional paid conversions per month — compounding. Ship it in sandbox this week, production by next Monday. 🚀