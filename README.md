# Collateral and Margining Simulation

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1anJVXWcWzVcRzVR4NavaozByr4ITK9lO?usp=sharing)

This project is an educational Excel and Python simulation designed to understand how collateral, variation margin, initial margin and counterparty default risk interact in OTC derivatives.

I built this project because I wanted to move beyond the theory and create a simple model that makes the mechanics of margining visible. The objective was not to build a production-grade margin engine, but to understand the intuition behind the process and explain it in a clear and accessible way.

---

## Why I Built This

Collateral is often presented as a mechanism that reduces counterparty risk. That is true, but the story is more nuanced.

Variation margin helps reduce current exposure by adjusting collateral as the value of the derivative changes. Initial margin acts as an additional buffer in case the counterparty defaults and the position cannot be closed immediately.

However, collateral does not eliminate risk completely. Under stressed market conditions, losses during the Margin Period of Risk may exceed the available initial margin. At the same time, margin calls can create liquidity pressure because market participants may need to post cash or eligible collateral quickly.

The main question I wanted to explore was:

**Does collateral fully protect against counterparty risk, or does it also transform part of that risk into liquidity pressure?**

---

## What the Model Does

The project is divided into two parts.

### 1. Excel Dashboard

The Excel model focuses on one simulated market scenario. It shows the mechanics step by step:

- simulate the underlying asset price
- calculate the mark-to-market of a simplified long forward contract
- compute daily variation margin
- estimate initial margin
- simulate a counterparty default
- calculate the loss during the Margin Period of Risk
- compare that loss with the available initial margin
- summarise the results in a dashboard

The Excel version is useful because it makes the logic visual and easy to follow.

### 2. Python Monte Carlo Extension

The Python notebook extends the Excel model by running thousands of simulated market scenarios.

Instead of asking what happens in one scenario, Python allows the model to ask:

**Across many possible market paths, how often is the initial margin not enough to cover losses during the Margin Period of Risk?**

This turns the project from a single-scenario explanation into a basic risk simulation framework.

---

## Excel Dashboard Preview

![Dashboard Screenshot](images/dashboard_screenshot.png)

---

## Methodology

The underlying asset price is simulated using Geometric Brownian Motion. The model then calculates the value of a simplified long forward contract.

The simplified mark-to-market formula is:

```text
MTM = ((Underlying Price - Forward Strike) / Forward Strike) × Notional
