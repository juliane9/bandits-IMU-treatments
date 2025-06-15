# Contextual Bandits for Personalized Treatments for Patients in ICU

This project investigates how contextual bandit algorithms can be used to personalize early medication decisions for ICU patients using real-world clinical data. The goal is to simulate how such algorithms might perform in recommending the first drug administered based on early patient data, optimizing for survival and reduced ICU duration.

## Problem Statement
In the ICU, early treatment decisions are made under severe uncertainty. This project evaluates how well contextual bandits (like Linear Upper Confidence Bound or Thompson Sampling) could have performed, compared to clinicians, at recommending initial medications based on patient features (the context) like:
- Demographics (age, gender)
- Vital signs and lab results (mean and std. dev over the first 6 hours)

## Dataset
Source: eICU Collaborative Research Database Demo (v2.0.1)
- 3,614 ICU stays used with structured features extracted from the first 6 hours

## Model
The action is defined as the first drug group administered (fluid, analgesic, antiemetic).
The two reward models studied are:
- Survival (binary)
- ICU Length-of-Stay (LoS), z-scored inverse duration

Different bandit algorithms were tested and compared to see which one is more suitable for this task:
- UCB1 – context-free
- LinUCB – linear contextual model
- Thompson Sampling – Bayesian exploration strategy

Off-policy evaluation was performed via:
- IPS (Inverse Propensity Scoring)
- SN-IPS (Self-Normalized IPS)
- DR (Doubly Robust Estimator)

## Methods Overview
- Propensity scores estimated with multinomial logistic regression
- Actions simulated chronologically with bandit policies
- Logged rewards used to compute regret and estimator performance

## Key Results
Thompson Sampling led to improved survival (99% vs. 92%) and LinUCB reduced ICU stay by ~1 hour on average.
DR and IPS agreed within ~5%, confirming stability.
More details are included in the final report (report.pdf) and the code for the simulation can be found in the notebook bandits_simulation.ipynb.
