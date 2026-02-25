# Migration & Default Risk – Credit Portfolio Simulation

This repository contains a Monte Carlo implementation of a one-period credit migration and default risk model under a one-factor Merton framework. The objective is to analyze how portfolio concentration, issuer-level diversification, and asset correlation affect the distribution of credit portfolio losses.

## Model Overview

The model follows a CreditMetrics-style approach:

- Rating transitions are driven by a one-factor Merton asset return model.
- Migration probabilities are taken from a one-period transition matrix.
- Portfolio losses arise from rating-dependent changes in bond values.
- Asset correlation levels are varied to assess systematic risk effects.

Two portfolio structures are analyzed:

1. **Concentrated Portfolio**  
   One issuer per rating class.

2. **Diversified Portfolio**  
   100 issuers per rating class with equal exposure per issuer.

For each case, the following risk measures are computed:
- Expected portfolio value  
- 90% and 99.5% Value-at-Risk (VaR)  
- 90% and 99.5% Expected Shortfall (ES)

## Key Research Questions

- How does issuer concentration impact tail risk?
- How does diversification mitigate idiosyncratic credit migration risk?
- Why does diversification fail under perfect correlation?
- How fat-tailed are credit loss distributions compared to normal asset returns?

## Methodology

- One-factor Gaussian Merton model:
  
  $$
  X_i = \sqrt{\rho} Y + \sqrt{1-\rho} \epsilon_i
  $$

- Monte Carlo simulation (200,000 scenarios)
- Migration thresholds calibrated to match the transition matrix exactly
- Tail risk evaluated using VaR and Expected Shortfall

## Main Insight

Diversification dramatically reduces credit portfolio risk when idiosyncratic risk dominates. However, as asset correlation increases, systematic risk becomes the primary driver of tail losses, and diversification loses effectiveness. Under perfect correlation, diversified portfolios collapse to the same loss distribution as concentrated portfolios.
