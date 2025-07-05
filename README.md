# Fixed Income Analytics & Interest Rate Modeling Project

This repository contains a comprehensive Python project for quantitative analysis of fixed income securities. It covers fundamental concepts such as present value, bond valuation, yield to maturity (YTM), duration, and convexity. Beyond basic valuation, it delves into constructing yield curves using bootstrapping and calculating forward rates. The project also implements advanced stochastic interest rate models, including the Vasicek and Cox-Ingersoll-Ross (CIR) models, providing both analytical solutions for Zero-Coupon Bond (ZCB) pricing and Monte Carlo simulations for rate path generation and valuation.

This project is suitable for finance students, quantitative analysts, and anyone interested in understanding the mathematical and computational aspects of fixed income markets.

## Features

**1. Fundamental Bond Valuation & Metrics:**
   - **Present Value (PV):** Calculates the present value of a future cash flow.
   - **Bond Valuation:** Determines the present value of coupon bonds, considering coupon payments and face value.
   - **Yield to Maturity (YTM):** Computes the YTM for coupon bonds.
   - **Duration:** Calculates both Macaulay and Modified Duration, essential measures of interest rate risk.
   - **Convexity:** Computes bond convexity, providing a more accurate risk measure beyond duration.

**2. Yield Curve Bootstrapping & Forward Rates:**
   - **Bootstrapped Spot Rate Curve:** Constructs a spot rate curve using the bootstrapping method from a set of observed bond prices (e.g., zero-coupon bonds or coupon-paying bonds).
   - **Forward Rate Curve:** Derives and plots the forward rate curve from the bootstrapped spot rates, indicating future implied interest rates.
   - **Graphical Comparison:** Visualizes and compares the bootstrapped spot rate curve and the derived forward rate curve.

**3. Stochastic Interest Rate Models:**
   - **Vasicek Model:**
     - Analytical pricing of Zero-Coupon Bonds (ZCBs).
     - Monte Carlo simulation of short rate paths.
     - Comparison of Monte Carlo ZCB prices with analytical solutions.
   - **Cox-Ingersoll-Ross (CIR) Model:**
     - Analytical pricing of Zero-Coupon Bonds (ZCBs).
     - Monte Carlo simulation of short rate paths, ensuring non-negative rates.
     - Comparison of Monte Carlo ZCB prices with analytical solutions.

**4. Data Visualization:**
   - Plots of bond price vs. YTM to illustrate the inverse relationship.
   - Visualization of simulated short rate paths for Vasicek and CIR models.
   - Graphical comparison of bootstrapped spot and forward rate curves.

## Project Structure

The core logic of the project is contained within a single Python script (`fixed_income_analytics.py`) or a Jupyter Notebook (`Quantitative_fixed_income_analytics.ipynb`).

-   `fixed_income_analytics.py` (or `Quantitative_fixed_income_analytics.ipynb`):
    -   Contains all functions and classes for bond valuation, duration, convexity, yield curve bootstrapping, forward rates, and interest rate model implementations.
    -   Includes example usage and plotting functions for demonstration.
-   `README.md`: This file, providing an overview of the project.
-   `requirements.txt`: Lists the necessary Python libraries.


## Author

Samyak Chandrakumar Jain
www.linkedin.com/in/samyakcjain
