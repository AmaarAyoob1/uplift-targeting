# Uplift Targeting on the Criteo Uplift Dataset (work in progress)

Which users should see an ad? Instead of targeting the users most likely to visit, this project models
the causal effect of the ad per user (uplift) and targets the persuadable ones.

## Status
- [x] Step 1: data audit and randomization check (13,979,592 users, 85/15 treatment split)
- [x] Step 2: A/B test analysis. Raw visit lift +1.03 pts shrinks to +0.77 pts [0.70, 0.84] after
      doubly robust (AIPW) adjustment for a small treatment imbalance (propensity AUC 0.508)
- [x] Step 3: S- and T-learners. Top 10% by S-learner uplift: +6.72 pts vs +1.07 for random targeting
- [ ] Step 4: X-learner, DR-learner, causal forest
- [ ] Step 5: propensity-weighted evaluation with bootstrap CIs
- [ ] Step 6: targeting policy under a budget
- [ ] Step 7: Hillstrom replication
- [ ] Step 8: app and write-up

## Data
Criteo Uplift Prediction Dataset v2.1 (CC BY-NC-SA 4.0), not included in this repo.
Download criteo-research-uplift-v2.1.csv.gz from https://huggingface.co/datasets/criteo/criteo-uplift
into data/raw/.

Diemert et al., "A Large Scale Benchmark for Uplift Modeling", AdKDD 2018.

## Environment
Python 3.11, pandas, scikit-learn, LightGBM, statsmodels, scikit-uplift.
