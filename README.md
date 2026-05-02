# Collateral and Margining Simulation

This project is an educational Excel-based simulation designed to explain the mechanics of collateral, variation margin, initial margin and counterparty default risk in OTC derivatives.

The model simulates an underlying asset price path, calculates the mark-to-market of a simplified forward contract, estimates daily variation margin, calculates initial margin using a simplified parametric VaR-style approach and analyses what happens if a counterparty defaults during the Margin Period of Risk.

The objective is to understand how collateral reduces counterparty risk while also showing how margin calls may create liquidity pressure under stressed market conditions.

## Dashboard Preview

![Dashboard Screenshot](images/dashboard_screenshot.png)

## Current Version

Version 1 includes an Excel model and dashboard with:

- Underlying asset simulation
- Forward mark-to-market calculation
- Daily variation margin
- Initial margin calculation
- Default scenario analysis
- Sensitivity analysis
- Interactive dashboard

## Excel Model

The Excel dashboard can be downloaded here:

[Download Excel Model](excel/collateral_margining_simulation_excel_v1.xlsx)

## Methodology

The model follows a simplified workflow:

1. Simulate an underlying asset price path using Geometric Brownian Motion.
2. Calculate the mark-to-market value of a simplified long forward contract.
3. Compute daily variation margin as the daily change in mark-to-market.
4. Estimate initial margin using a parametric VaR-style approach.
5. Simulate a counterparty default during the life of the trade.
6. Compare the loss during the Margin Period of Risk with the available initial margin.
7. Analyse how confidence levels and MPoR assumptions affect collateral requirements.

## Key Insight

Collateral reduces counterparty risk by requiring collateral to be exchanged as exposures change. Variation margin adjusts collateral daily to the current value of the contract, while initial margin acts as a buffer against potential losses after default and before the position can be closed or replaced.

However, collateral does not eliminate risk completely. In stressed scenarios, losses during the Margin Period of Risk may exceed the available initial margin, creating uncovered losses. More conservative margin assumptions reduce counterparty risk, but they also increase collateral requirements and may create liquidity pressure.

## Limitations

This is a simplified educational model. It does not include discounting, netting sets, collateral thresholds, minimum transfer amounts, funding costs, wrong-way risk, legal close-out mechanics or a full SIMM implementation.

## Next Steps

A Python Monte Carlo extension will be added to run multiple simulations and estimate the probability of uncovered losses under different margin assumptions.
