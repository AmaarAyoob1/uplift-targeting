# Persuadable: Uplift Targeting and A/B Testing on 14M Users

Which users should see an ad? Instead of targeting the users most likely to visit, this project estimates the
causal effect of the ad for each user (uplift) and targets the persuadable ones, then checks the result on a
second experiment.

## Key results so far
- **A/B test (Criteo, 13,979,592 users):** raw visit lift +1.03 pts shrinks to **+0.76 pts** after doubly robust
  (AIPW) adjustment for a small treatment imbalance (propensity AUC 0.508). Bias was ~7x the detectable effect.
- **Uplift models:** S-learner beat T-, X-, DR-learners and a causal forest. After propensity weighting, its top 10%
  shows **+5.72 pts [5.29, 6.09]**, 14% more than ranking by visit probability (better in 200/200 paired bootstraps).
  At a 30% budget all methods tie.
- **Policy in dollars** (assumed $1.50/visit, $0.01/user): targeting the top 16% earns **$36k vs $6k** for targeting
  everyone, keeping 89% of incremental visits. Uplift's edge over response targeting grows with ad cost (+1% to +12%).
- **Replication (Hillstrom email test, 64k customers, 3 arms):** both emails work (men's +7.66 pts visit). Uplift
  beat response targeting only for the women's email (+1.8 pts, 100% of bootstraps); a spend-based targeted policy
  lost to emailing everyone the men's version (578 buyers is too few to model spend).
- **Takeaway:** uplift modelling pays when effects vary across customers, data is large, and treatment is costly.

## Status
- [x] 1. Data audit and randomization check
- [x] 2. A/B test: lift, CIs, regression adjustment, AIPW, effect on exposed users, power/MDE
- [x] 3. S- and T-learners vs response targeting
- [x] 4. X-learner, DR-learner, causal forest (econml)
- [x] 5. Paired bootstrap + propensity-weighted evaluation, Qini curves
- [x] 6. Targeting policy valued in dollars with doubly robust scores
- [x] 7. Hillstrom replication: Holm-corrected multi-arm tests, cross-validated uplift, IPW policy value
- [ ] 8. Cleanup into stage notebooks, figures, final README, app

## Data (not included in this repo)
- Criteo Uplift Prediction Dataset v2.1 (CC BY-NC-SA 4.0): https://huggingface.co/datasets/criteo/criteo-uplift
  Diemert et al., "A Large Scale Benchmark for Uplift Modeling", AdKDD 2018.
- Kevin Hillstrom, MineThatData E-Mail Analytics and Data Mining Challenge (2008).

## Environment
Python 3.11, pandas, scikit-learn, LightGBM, statsmodels, scikit-uplift, econml.
